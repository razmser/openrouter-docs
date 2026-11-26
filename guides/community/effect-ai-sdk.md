> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Effect AI SDK

> Integrate OpenRouter using the Effect AI SDK

## Effect AI SDK

You can use the [Effect AI SDK](https://www.npmjs.com/package/@effect/ai) to integrate OpenRouter with your Effect applications. To get started, install the following packages:

* [effect](https://www.npmjs.com/package/effect): the Effect core (if not already installed)
* [@effect/ai](https://www.npmjs.com/package/@effect/ai): the core Effect AI SDK abstractions
* [@effect/ai-openrouter](https://www.npmjs.com/package/@effect/ai-openrouter): the Effect AI provider integration for OpenRouter
* [@effect/platform](https://www.npmjs.com/package/@effect/platform): platform-agnostic abstractions for Effect

```bash lines theme={null}
npm install effect @effect/ai @effect/ai-openrouter @effect/platform
```

Once that's done you can use the [LanguageModel](https://effect.website/docs/ai/getting-started/#define-an-interaction-with-a-language-model) module to define interactions with a large language model via OpenRouter.

```typescript title="TypeScript" expandable lines theme={null}
import { LanguageModel } from "@effect/ai"
import { OpenRouterClient, OpenRouterLanguageModel } from "@effect/ai-openrouter"
import { FetchHttpClient } from "@effect/platform"
import { Config, Effect, Layer, Stream } from "effect"

const Gpt4o = OpenRouterLanguageModel.model("openai/gpt-4o")

const program = LanguageModel.streamText({
  prompt: [
    { role: "system", content: "You are a comedian with a penchant for groan-inducing puns" },
    { role: "user", content: [{ type: "text", text: "Tell me a dad joke" }] }
  ]
}).pipe(
  Stream.filter((part) => part.type === "text-delta"),
  Stream.runForEach((part) => Effect.sync(() => process.stdout.write(part.delta))),
  Effect.provide(Gpt4o)
)

const OpenRouter = OpenRouterClient.layerConfig({
  apiKey: Config.redacted("OPENROUTER_API_KEY")
}).pipe(Layer.provide(FetchHttpClient.layer))

program.pipe(
  Effect.provide(OpenRouter),
  Effect.runPromise
)
```

```python title="Python" lines theme={null}
import os
from openrouter import OpenRouter

with OpenRouter(api_key=os.environ["OPENROUTER_API_KEY"]) as client:
    stream = client.chat.send(
        model="openai/gpt-4o",
        messages=[
            {"role": "system", "content": "You are a comedian with a penchant for groan-inducing puns"},
            {"role": "user", "content": [{"type": "text", "text": "Tell me a dad joke"}]},
        ],
        stream=True,
    )

    for chunk in stream:
        if chunk.choices and chunk.choices[0].delta.content:
            print(chunk.choices[0].delta.content, end="", flush=True)
    print()

```

```go title="Go" lines theme={null}
package main

import (
	"bufio"
	"bytes"
	"encoding/json"
	"fmt"
	"io"
	"net/http"
	"os"
	"strings"
)

func main() {
	body, _ := json.Marshal(map[string]any{
		"model":  "openai/gpt-4o",
		"stream": true,
		"messages": []map[string]any{
			{"role": "system", "content": "You are a comedian with a penchant for groan-inducing puns"},
			{"role": "user", "content": []map[string]string{{"type": "text", "text": "Tell me a dad joke"}}},
		},
	})

	req, _ := http.NewRequest("POST", "https://openrouter.ai/api/v1/chat/completions", bytes.NewReader(body))
	req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
	req.Header.Set("Content-Type", "application/json")

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		panic(err)
	}
	defer resp.Body.Close()
	if resp.StatusCode != http.StatusOK {
		b, _ := io.ReadAll(resp.Body)
		fmt.Fprintln(os.Stderr, resp.Status, string(b))
		os.Exit(1)
	}

	scanner := bufio.NewScanner(resp.Body)
	for scanner.Scan() {
		data, ok := strings.CutPrefix(scanner.Text(), "data: ")
		if !ok || data == "[DONE]" {
			continue
		}
		var chunk struct {
			Choices []struct {
				Delta struct {
					Content string `json:"content"`
				} `json:"delta"`
			} `json:"choices"`
		}
		if json.Unmarshal([]byte(data), &chunk) == nil && len(chunk.Choices) > 0 {
			fmt.Print(chunk.Choices[0].Delta.Content)
		}
	}
	fmt.Println()
}

```

```bash title="cURL" lines theme={null}
curl -sN https://openrouter.ai/api/v1/chat/completions \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/gpt-4o",
    "stream": true,
    "messages": [
      { "role": "system", "content": "You are a comedian with a penchant for groan-inducing puns" },
      { "role": "user", "content": [{ "type": "text", "text": "Tell me a dad joke" }] }
    ]
  }' | sed -n 's/^data: //p' | grep -v '^\[DONE\]$' | jq -j '.choices[0].delta.content // empty'
echo

```

```text title="Output" theme={null}
Why do cows have hooves instead of feet?

Because they lactose!
```
