> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# User Tracking

The OpenRouter API supports **User Tracking** through the optional `user` parameter. Supplying a stable per-end-user identifier helps isolate abuse blocks and improves your application's reporting.

## What is User Tracking?

User tracking enables you to specify an arbitrary string identifier for your end users in API requests. This optional metadata helps OpenRouter understand your sub-users.

## How It Works

Include a `user` parameter in [Responses API](../../api_reference/responses/overview.md), chat-completions, or image-generation requests with a stable identifier for your end user. This can be a user ID, client-side hash, pseudonym, or another stable identifier. OpenRouter folds it into the hashed identity sent upstream and never forwards it raw.

```json lines theme={null}
{
  "model": "~openai/gpt-sol-latest",
  "input": "Hello, how are you?",
  "user": "user_12345"
}
```

## Register External Users with the Management API

Organizations can explicitly register the same caller-supplied tracking identifiers through the Management API. Registration requires an organization [management key](../../guides/overview/auth/management-api-keys.md) and does not create a login, organization member, credential, or generated OpenRouter end-user ID.

```bash theme={null}
curl https://openrouter.ai/api/v1/external-users \
  -H "Authorization: Bearer $OPENROUTER_MANAGEMENT_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "user": "employee_123"
  }'
```

The `user` value is the source of truth and must exactly match the value sent on inference requests. It is case-sensitive, immutable, and unique within the organization.

Use the collection and resource routes to manage registrations:

* `POST /api/v1/external-users` registers a tracking identifier. The request body accepts only `user`.
* `GET /api/v1/external-users` lists active registrations; set `include_inactive=true` to include deactivated registrations.
* `GET /api/v1/external-users/{user}` retrieves one registration, including a deactivated one; check `is_active` for its lifecycle state. URL-encode the exact `user` value.
* `PATCH /api/v1/external-users/{user}` updates the registration with the required `is_active` boolean.
* `DELETE /api/v1/external-users/{user}` soft-deactivates a registration. Repeating the request succeeds, and the identifier remains reserved.

Registration alone does not attribute requests. Continue sending the same identifier as `user` on chat completions, image generation, and the Responses API; `safety_identifier` sets only the upstream abuse-isolation identity and does not attribute requests to a registered external user. Deactivation is a management lifecycle state and does not block inference.

## Implementation Example

```typescript title="TypeScript SDK" lines theme={null}
import { OpenRouter } from '@openrouter/sdk';

const openRouter = new OpenRouter({
  apiKey: '<OPENROUTER_API_KEY>',
});

const response = await openRouter.responses.send({
  responsesRequest: {
    model: '~openai/gpt-sol-latest',
    input: "What's the weather like today?",
    user: 'user_12345', // Your user identifier
    stream: false,
  },
});

if (!('output' in response)) {
  throw new Error('Expected a non-streaming response');
}

const message = [...response.output].reverse().find((item) => item.type === 'message');
console.log(message?.content.find((part) => part.type === 'output_text')?.text);
```

```python title="Python SDK" lines theme={null}
from openrouter import OpenRouter

with OpenRouter(
    api_key="<OPENROUTER_API_KEY>",
) as client:
    response = client.responses.send(
        model="~openai/gpt-sol-latest",
        input="What's the weather like today?",
        user="user_12345",  # Your user identifier
        stream=False,
    )

    for item in response.output:
        if getattr(item, "type", None) == "message":
            for part in item.content:
                if getattr(part, "type", None) == "output_text":
                    print(part.text)

```

```typescript title="TypeScript (OpenAI SDK)" expandable lines theme={null}
import OpenAI from 'openai';

const openai = new OpenAI({
  baseURL: 'https://openrouter.ai/api/v1',
  apiKey: '<OPENROUTER_API_KEY>',
});

async function chatWithUserTracking() {
  const response = await openai.responses.create({
    model: '~openai/gpt-sol-latest',
    input: "What's the weather like today?",
    user: 'user_12345', // Your user identifier
  });

  console.log(response.output_text);
}

chatWithUserTracking();
```

```go title="Go" lines theme={null}
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
	"log"
	"net/http"
	"os"
)

func main() {
	body, _ := json.Marshal(map[string]any{
		"model":  "~openai/gpt-sol-latest",
		"input":  "What's the weather like today?",
		"user":   "user_12345", // Your user identifier
		"stream": false,
	})

	req, _ := http.NewRequest("POST", "https://openrouter.ai/api/v1/responses", bytes.NewReader(body))
	req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
	req.Header.Set("Content-Type", "application/json")

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		log.Fatal(err)
	}
	defer resp.Body.Close()
	if resp.StatusCode != http.StatusOK {
		log.Fatalf("request failed: %s", resp.Status)
	}

	var result struct {
		Output []struct {
			Type    string `json:"type"`
			Content []struct {
				Type string `json:"type"`
				Text string `json:"text"`
			} `json:"content"`
		} `json:"output"`
	}
	if err := json.NewDecoder(resp.Body).Decode(&result); err != nil {
		log.Fatal(err)
	}

	for i := len(result.Output) - 1; i >= 0; i-- {
		if result.Output[i].Type != "message" {
			continue
		}
		for _, part := range result.Output[i].Content {
			if part.Type == "output_text" {
				fmt.Println(part.Text)
				return
			}
		}
		return
	}
}

```

```bash title="cURL" lines theme={null}
curl -s https://openrouter.ai/api/v1/responses \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "~openai/gpt-sol-latest",
    "input": "What'\''s the weather like today?",
    "user": "user_12345",
    "stream": false
  }' | jq -r '[.output[] | select(.type == "message")] | last | .content[] | select(.type == "output_text") | .text'

```

```text title="Output" theme={null}
What city or ZIP code should I use for today’s weather?
```

## Per-User Abuse Isolation

Send a stable per-end-user identifier with every request as `user` on chat completions, image generation, and the Responses API. On the Responses API, `safety_identifier` sets only the upstream abuse-isolation identity. A client-side hash or pseudonym works — when a provider requires a user identity, OpenRouter folds it into the hashed identity sent upstream and never forwards the raw value. Requests that include neither field share a single account-level identity upstream, so a provider policy block triggered by one end user can affect your whole account.

## Best Practices

### Choose Stable Identifiers

Use consistent, stable identifiers for the same user across requests:

* **Good**: `user_12345`, `customer_abc123`, `account_xyz789`
* **Avoid**: Random strings that change between requests

### Consider Privacy

When using user identifiers, consider privacy implications:

* Use internal user IDs rather than exposing personal information
* Avoid including personally identifiable information in user identifiers
* Consider using anonymized identifiers for better privacy protection

### Be Consistent

Use the same user identifier format throughout your application:

```python lines theme={null}
# Consistent format
user_id = f"app_{internal_user_id}"
```

```typescript title="TypeScript" lines theme={null}
// Consistent format
const userId = `app_${internalUserId}`;
```

```go title="Go" lines theme={null}
// Consistent format
userID := fmt.Sprintf("app_%v", internalUserID)
```

```bash title="cURL" lines theme={null}
# Consistent format
user_id="app_${internal_user_id}"
```
