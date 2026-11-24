> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Agent SDK

> Build AI agents with multi-turn loops, tools, and conversation state

The Agent SDK (`@openrouter/agent`) provides the primitives you need to build agentic applications on OpenRouter. Instead of manually wiring up conversation loops, tool dispatch, and state tracking, the Agent SDK handles all of that so you can focus on defining *what* your agent does.

The Agent SDK is built on top of the TypeScript [Client SDK](../client-sdks/overview.md): `@openrouter/agent` depends on `@openrouter/sdk` and installs it for you, so its `OpenRouter` class accepts the same client options. Add `@openrouter/sdk` to your own dependencies if you also want to call REST endpoints directly, so that you control which version you get.

## When to use the Agent SDK

Choose the Agent SDK when you need **agentic behavior**: multi-step reasoning where the model calls tools, processes results, and decides what to do next.

* **Multi-turn agent loops**: `callModel` automatically loops until a stop condition is met
* **Tool definitions**: define tools with the `tool()` helper and the SDK executes them for you
* **Stop conditions**: control when the loop ends with `stepCountIs`, `hasToolCall`, `maxCost`, and more
* **Conversation state**: the SDK tracks messages, tool results, and context across turns
* **Streaming**: real-time token output within each agent step
* **Dynamic parameters**: change model, temperature, or tools between turns based on context
* **MCP tools**: plug in a remote [Model Context Protocol](call-model/mcp-tools.md) server and its tools drop straight into `callModel`

> [!TIP]
>
> If you only need simple request/response calls to a model without agent loops, the [Client SDKs](../client-sdks/overview.md) are a lighter-weight option.

## Installation

| Language | Package |
| - | - |
| TypeScript | [`@openrouter/agent`](https://www.npmjs.com/package/@openrouter/agent) |
| Python | [`openrouter-agent-sdk`](https://pypi.org/project/openrouter-agent-sdk/) |
| Go | [`go-agent`](https://pkg.go.dev/github.com/OpenRouterTeam/go-agent) |

```bash title="npm" lines theme={null}
npm install @openrouter/agent
```

```bash title="pnpm" lines theme={null}
pnpm add @openrouter/agent
```

```bash title="yarn" lines theme={null}
yarn add @openrouter/agent
```

```bash title="bun" lines theme={null}
bun add @openrouter/agent
```

```bash title="deno" lines theme={null}
deno add npm:@openrouter/agent
```

```bash title="pip (Python)" lines theme={null}
pip install openrouter-agent-sdk
```

```bash title="go (Go)" lines theme={null}
go get github.com/OpenRouterTeam/go-agent
```

The Python and Go packages are ports of `@openrouter/agent` kept in sync automatically. See the [Python agent SDK repository](https://github.com/OpenRouterTeam/python-agent) and [Go agent SDK repository](https://github.com/OpenRouterTeam/go-agent) for language-specific details. The rest of this Agent SDK documentation uses TypeScript examples.

## Quick example

```typescript expandable lines theme={null}
import { OpenRouter, tool } from '@openrouter/agent';
import { z } from 'zod';

const openrouter = new OpenRouter({
  apiKey: process.env.OPENROUTER_API_KEY,
});

const weatherTool = tool({
  name: 'get_weather',
  description: 'Get the current weather for a location',
  inputSchema: z.object({
    location: z.string().describe('City name'),
  }),
  execute: async ({ location }) => {
    return { temperature: 72, condition: 'sunny', location };
  },
});

const result = openrouter.callModel({
  model: '~anthropic/claude-sonnet-latest',
  input: 'What is the weather in San Francisco?',
  tools: [weatherTool],
});

const text = await result.getText();
console.log(text);
```

```python title="Python" lines theme={null}
import asyncio
import os
from pydantic import BaseModel, Field
from openrouter_agent import OpenRouter, call_model, tool


class WeatherInput(BaseModel):
    location: str = Field(description="City name")


weather_tool = tool(
    name="get_weather",
    description="Get the current weather for a location",
    input_schema=WeatherInput,
    execute=lambda params, ctx: {
        "temperature": 72,
        "condition": "sunny",
        "location": params.location,
    },
)


async def main() -> None:
    client = OpenRouter(api_key=os.environ["OPENROUTER_API_KEY"])

    result = call_model(
        client,
        {
            "model": "~anthropic/claude-sonnet-latest",
            "input": "What is the weather in San Francisco?",
            "tools": [weather_tool],
        },
    )

    text = await result.get_text()
    print(text)


asyncio.run(main())

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

type M = map[string]any

func getWeather(location string) M {
	return M{"temperature": 72, "condition": "sunny", "location": location}
}

func main() {
	tools := []any{M{"type": "function", "function": M{
		"name":        "get_weather",
		"description": "Get the current weather for a location",
		"parameters": M{
			"type":       "object",
			"properties": M{"location": M{"type": "string", "description": "City name"}},
			"required":   []string{"location"},
		},
	}}}
	messages := []any{M{"role": "user", "content": "What is the weather in San Francisco?"}}

	for {
		body, _ := json.Marshal(M{"model": "~anthropic/claude-sonnet-latest", "messages": messages, "tools": tools})
		req, _ := http.NewRequest("POST", "https://openrouter.ai/api/v1/chat/completions", bytes.NewReader(body))
		req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
		req.Header.Set("Content-Type", "application/json")
		resp, err := http.DefaultClient.Do(req)
		if err != nil {
			log.Fatal(err)
		}
		raw, _ := io.ReadAll(resp.Body)
		resp.Body.Close()
		if resp.StatusCode != 200 {
			log.Fatalf("%d: %s", resp.StatusCode, raw)
		}
		var out struct {
			Choices []struct{ Message M } `json:"choices"`
		}
		if err := json.Unmarshal(raw, &out); err != nil {
			log.Fatal(err)
		}
		// An error can arrive with HTTP 200 and no choices
		if len(out.Choices) == 0 {
			log.Fatalf("no choices in response: %s", raw)
		}
		msg := out.Choices[0].Message
		messages = append(messages, msg)

		calls, _ := msg["tool_calls"].([]any)
		if len(calls) == 0 {
			fmt.Println(msg["content"])
			return
		}
		for _, c := range calls {
			call := c.(M)
			var args struct{ Location string }
			json.Unmarshal([]byte(call["function"].(M)["arguments"].(string)), &args)
			result, _ := json.Marshal(getWeather(args.Location))
			messages = append(messages, M{"role": "tool", "tool_call_id": call["id"], "content": string(result)})
		}
	}
}

```

```text title="Output" theme={null}
San Francisco is sunny right now, and the temperature is 72°. The tool didn't say whether that's °F or °C. It's probably °F, since 72°C would be impossibly hot.
```

The SDK sends the input to the model, receives a tool call, executes `get_weather`, feeds the result back, and returns the final response, all in one `callModel` invocation.

## Core concepts

### `callModel`

The main entry point. It runs an inference loop that:

1. Sends the `input` to the model
2. If the model returns tool calls, executes them automatically
3. Appends tool results to the conversation
4. Repeats until a stop condition is met or no more tool calls are made

See the [Call Model documentation](https://openrouter.ai/docs/agent-sdk/call-model) for the full API.

### Tools

Define tools with the `tool()` helper. Each tool has a name, description, Zod parameter schema, and an `execute` function. The SDK handles serialization, validation, and dispatch.

```typescript lines theme={null}
import { tool } from '@openrouter/agent';
import { z } from 'zod';

const searchTool = tool({
  name: 'search',
  description: 'Search the web',
  inputSchema: z.object({ query: z.string() }),
  execute: async ({ query }) => {
    // Your search implementation
    return { results: ['...'] };
  },
});
```

```python title="Python" lines theme={null}
from pydantic import BaseModel
from openrouter_agent import tool


class SearchInput(BaseModel):
    query: str


def run_search(params, ctx):
    # Your search implementation
    return {"results": ["..."]}


search_tool = tool(
    name="search",
    description="Search the web",
    input_schema=SearchInput,
    execute=run_search,
)

```

```go title="Go" lines theme={null}
var searchTool = M{"type": "function", "function": M{
	"name":        "search",
	"description": "Search the web",
	"parameters": M{
		"type":       "object",
		"properties": M{"query": M{"type": "string"}},
		"required":   []string{"query"},
	},
}}

func search(query string) M {
	// Your search implementation
	return M{"results": []string{"..."}}
}

```

### Stop conditions

Control when the agent loop terminates:

```typescript lines theme={null}
import { OpenRouter, callModel, tool, stepCountIs, maxCost } from '@openrouter/agent';
import { z } from 'zod';

const openrouter = new OpenRouter({
  apiKey: process.env.OPENROUTER_API_KEY,
});

const searchTool = tool({
  name: 'search',
  description: 'Search the web',
  inputSchema: z.object({ query: z.string() }),
  execute: async ({ query }) => {
    // Your search implementation
    return { results: ['...'] };
  },
});

const result = callModel(openrouter, {
  model: '~anthropic/claude-sonnet-latest',
  input: 'Research this topic thoroughly',
  tools: [searchTool],
  stopWhen: [stepCountIs(10), maxCost(0.50)],
});

const text = await result.getText();
console.log(text);

```

```python title="Python" lines theme={null}
import asyncio
import os
from pydantic import BaseModel
from openrouter_agent import OpenRouter, call_model, tool, step_count_is, max_cost


class SearchInput(BaseModel):
    query: str


def run_search(params, ctx):
    # Your search implementation
    return {"results": ["..."]}


search_tool = tool(
    name="search",
    description="Search the web",
    input_schema=SearchInput,
    execute=run_search,
)


async def main() -> None:
    client = OpenRouter(api_key=os.environ["OPENROUTER_API_KEY"])

    result = call_model(
        client,
        {
            "model": "~anthropic/claude-sonnet-latest",
            "input": "Research this topic thoroughly",
            "tools": [search_tool],
            "stop_when": [step_count_is(10), max_cost(0.50)],
        },
    )

    text = await result.get_text()
    print(text)


asyncio.run(main())

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

type M = map[string]any

func search(query string) M {
	// Your search implementation
	return M{"results": []string{"..."}}
}

// complete sends one chat completion request and returns the assistant message and its cost.
// Pass nil tools to make the model answer without calling a tool.
func complete(messages, tools []any) (M, float64) {
	payload := M{"model": "~anthropic/claude-sonnet-latest", "messages": messages}
	if tools != nil {
		payload["tools"] = tools
	}
	body, _ := json.Marshal(payload)
	req, _ := http.NewRequest("POST", "https://openrouter.ai/api/v1/chat/completions", bytes.NewReader(body))
	req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
	req.Header.Set("Content-Type", "application/json")
	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		log.Fatal(err)
	}
	raw, _ := io.ReadAll(resp.Body)
	resp.Body.Close()
	if resp.StatusCode != 200 {
		log.Fatalf("%d: %s", resp.StatusCode, raw)
	}
	var out struct {
		Choices []struct{ Message M } `json:"choices"`
		Usage   struct{ Cost float64 } `json:"usage"`
	}
	if err := json.Unmarshal(raw, &out); err != nil {
		log.Fatal(err)
	}
	if len(out.Choices) == 0 {
		log.Fatalf("no choices in response: %s", raw)
	}
	return out.Choices[0].Message, out.Usage.Cost
}

func main() {
	tools := []any{M{"type": "function", "function": M{
		"name":        "search",
		"description": "Search the web",
		"parameters": M{
			"type":       "object",
			"properties": M{"query": M{"type": "string"}},
			"required":   []string{"query"},
		},
	}}}
	messages := []any{M{"role": "user", "content": "Research this topic thoroughly"}}

	// Stop conditions: at most 10 steps or $0.50 total cost
	const maxSteps, maxCost = 10, 0.50
	totalCost := 0.0
	var last M
	hasPendingToolResults := false

	for step := 0; step < maxSteps && totalCost < maxCost; step++ {
		message, cost := complete(messages, tools)
		totalCost += cost
		last = message
		messages = append(messages, last)

		calls, _ := last["tool_calls"].([]any)
		hasPendingToolResults = len(calls) > 0
		if !hasPendingToolResults {
			break
		}
		for _, c := range calls {
			call := c.(M)
			var args struct{ Query string }
			if err := json.Unmarshal([]byte(call["function"].(M)["arguments"].(string)), &args); err != nil {
				log.Fatal(err)
			}
			result, _ := json.Marshal(search(args.Query))
			messages = append(messages, M{"role": "tool", "tool_call_id": call["id"], "content": string(result)})
		}
	}

	// A stop condition ended the loop right after a tool ran: send the tool
	// results back once more, without tools, so the model writes a final answer
	if hasPendingToolResults {
		last, _ = complete(messages, nil)
	}

	fmt.Println(last["content"])
}

```

```text title="Output" theme={null}
You asked me to research "this topic," but I don't see a topic in your message. What would you like me to look into?

It would help to know:
- **The subject:** a specific question, event, technology, person, or concept.
- **The scope:** whether you want a broad overview or a focus on one aspect, such as recent developments, history, pros and cons, or comparisons.
- **The purpose and depth:** for example, a quick briefing, a detailed report, or background for a decision or paper.
- **Any constraints:** a time frame, a region, or preferred source types, such as academic, news, or official data.

When you send the topic, I'll run several searches and give you a synthesized summary with sources.
```

## Agent SDK vs Client SDKs

| | Agent SDK | Client SDKs |
| - | - | - |
| **Focus** | Agentic primitives: multi-turn loops, tools, stop conditions | Lean API client that mirrors the REST API with full type safety |
| **Use when** | You want built-in agent loops, tool execution, and state management | You want direct model calls and manage orchestration yourself |
| **Conversation state** | Managed for you via `callModel` | You manage it |
| **Tool execution** | Automatic with the `tool()` helper | You dispatch tool calls |
| **Languages** | TypeScript, Python, Go | TypeScript, Python, Go |

## Next steps

* [Call Model](https://openrouter.ai/docs/agent-sdk/call-model): the complete `callModel` API reference
* [Tools](call-model/tools.md): defining and using tools
* [Stop Conditions](call-model/stop-conditions.md): controlling agent loop termination
* [Streaming](call-model/streaming.md): real-time token output
* [DevTools](dev-tools/devtools.md): pre-release telemetry capture; the CLI viewer is retired
* [Migrating from @openrouter/sdk](agent-migration.md): move agent imports to the standalone package
