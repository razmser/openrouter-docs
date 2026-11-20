> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Responses API

> OpenAI-compatible Responses API

> [!NOTE]
>
> **Stateless Only**
>
> This API is **stateless** - each request is independent and no conversation state is persisted between requests. You must include the full conversation history in each request. Requests that set `store: true` or a non-null `previous_response_id` are rejected with a `400` error.

OpenRouter's Responses API provides OpenAI-compatible access to multiple AI models through a unified interface, designed to be a drop-in replacement for OpenAI's Responses API. This stateless API offers enhanced capabilities including reasoning, tool calling, and web search integration, with each request being independent and no server-side state persisted.

## Base URL

```lines theme={null}
https://openrouter.ai/api/v1/responses
```

## Authentication

All requests require authentication using your OpenRouter API key:

```typescript title="TypeScript" lines theme={null}
const response = await fetch('https://openrouter.ai/api/v1/responses', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${process.env.OPENROUTER_API_KEY}`,
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    model: 'openai/gpt-4o-mini',
    input: 'Hello, world!',
  }),
});

const result = await response.json();
console.log(JSON.stringify(result, null, 2));

```

```python title="Python" lines theme={null}
import os
import requests

response = requests.post(
    'https://openrouter.ai/api/v1/responses',
    headers={
        'Authorization': f'Bearer {os.environ["OPENROUTER_API_KEY"]}',
        'Content-Type': 'application/json',
    },
    json={
        'model': 'openai/gpt-4o-mini',
        'input': 'Hello, world!',
    }
)

print(response.json())

```

```bash title="cURL" lines theme={null}
curl -X POST https://openrouter.ai/api/v1/responses \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/gpt-4o-mini",
    "input": "Hello, world!"
  }'

```

```go title="Go" lines theme={null}
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
	"io"
	"log"
	"net/http"
	"os"
)

func main() {
	body, _ := json.Marshal(map[string]any{
		"model": "openai/gpt-4o-mini",
		"input": "Hello, world!",
	})

	req, err := http.NewRequest("POST", "https://openrouter.ai/api/v1/responses", bytes.NewReader(body))
	if err != nil {
		log.Fatal(err)
	}
	req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
	req.Header.Set("Content-Type", "application/json")

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		log.Fatal(err)
	}
	defer resp.Body.Close()

	data, err := io.ReadAll(resp.Body)
	if err != nil {
		log.Fatal(err)
	}

	var out bytes.Buffer
	if err := json.Indent(&out, data, "", "  "); err != nil {
		fmt.Println(string(data))
		return
	}
	fmt.Println(out.String())
}

```

```text title="Output" theme={null}
{
  "id": "gen-1794947580-aB47fruOzZLs4Q1yYYEw",
  "object": "response",
  "created_at": 1794947580,
  "model": "openai/gpt-4o-mini",
  "status": "completed",
  "completed_at": 1794947582,
  "output": [
    {
      "id": "msg_tmp_twroxelw9tl",
      "type": "message",
      "role": "assistant",
      "status": "completed",
      "content": [
        {
          "type": "output_text",
          "text": "Hello! How can I assist you today?",
          "annotations": [],
          "logprobs": []
        }
      ]
    }
  ],
  "error": null,
  "incomplete_details": null,
  "access_programs": null,
  "tools": [],
  "tool_choice": "auto",
  "parallel_tool_calls": true,
  "max_output_tokens": null,
  "temperature": 1,
  "top_p": 1,
  "presence_penalty": 0,
  "frequency_penalty": 0,
  "top_logprobs": 0,
  "max_tool_calls": null,
  "metadata": {},
  "background": false,
  "previous_response_id": null,
  "service_tier": "default",
```

## Core Features

### [Basic Usage](basic-usage.md)

Learn the fundamentals of making requests with simple text input and handling responses.

### [Reasoning](reasoning.md)

Access advanced reasoning capabilities with configurable effort levels and encrypted reasoning chains.

### [Tool Calling](tool-calling.md)

Integrate function calling with support for parallel execution and complex tool interactions.

### [Web Search](web-search.md)

Enable web search capabilities with real-time information retrieval and citation annotations.

## Error Handling

The API returns structured error responses:

```json lines theme={null}
{
  "error": {
    "code": "invalid_prompt",
    "message": "Missing required parameter: 'model'."
  },
  "metadata": null
}
```

For comprehensive error handling guidance, see [Error Handling](error-handling.md).

## Rate Limits

Standard OpenRouter rate limits apply. See [API Limits](../limits.md) for details.
