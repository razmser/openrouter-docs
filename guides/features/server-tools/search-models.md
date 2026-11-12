> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Search Models

> Let any model search the OpenRouter model catalog

Beta

> [!NOTE]
>
> **Beta**
>
> Server tools are currently in beta. The API and behavior may change. This tool is experimental. When it graduates, the tool type is likely to be renamed (dropping the `experimental__` prefix), which would be a breaking change for requests using the current name.

The `openrouter:experimental__search_models` server tool lets a model search and filter the OpenRouter model catalog. The model can look up models by name, capabilities, modalities, and other attributes, useful for agents that pick models dynamically, for example with the [Subagent](subagent.md) tool.

## Quick Start

```typescript title="TypeScript" expandable lines theme={null}
const response = await fetch('https://openrouter.ai/api/v1/responses', {
  method: 'POST',
  headers: {
    Authorization: 'Bearer <OPENROUTER_API_KEY>',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    model: 'openai/gpt-5.2',
    input: 'Which models on OpenRouter can take image input and have at least 128k context?',
    tools: [
      { type: 'openrouter:experimental__search_models' }
    ]
  }),
});

const data = await response.json();
const message = [...data.output].reverse().find((item: { type: string }) => item.type === 'message');
console.log(message?.content.find((part: { type: string; text?: string }) => part.type === 'output_text')?.text);
```

```python title="Python" expandable lines theme={null}
import requests

response = requests.post(
  "https://openrouter.ai/api/v1/responses",
  headers={
    "Authorization": f"Bearer <OPENROUTER_API_KEY>",
    "Content-Type": "application/json",
  },
  json={
    "model": "openai/gpt-5.2",
    "input": "Which models on OpenRouter can take image input and have at least 128k context?",
    "tools": [
      {"type": "openrouter:experimental__search_models"}
    ]
  }
)

data = response.json()
message = next(item for item in reversed(data["output"]) if item["type"] == "message")
print(next(part["text"] for part in message["content"] if part["type"] == "output_text"))
```

```bash title="cURL" lines theme={null}
curl https://openrouter.ai/api/v1/responses \
  -H "Authorization: Bearer <OPENROUTER_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "openai/gpt-5.2",
    "input": "Which models on OpenRouter can take image input and have at least 128k context?",
    "tools": [
      {"type": "openrouter:experimental__search_models"}
    ]
  }'
```

## Configuration

The search models tool accepts an optional `max_results` parameter:

```json lines theme={null}
{
  "type": "openrouter:experimental__search_models",
  "parameters": {
    "max_results": 5
  }
}
```

| Parameter | Type | Default | Description |
| - | - | - | - |
| `max_results` | integer | `5` | Maximum number of models to return per call. Between 1 and 20 |

### Call Arguments

The model generates the search arguments. All fields are optional; an empty call browses the full catalog:

| Field | Type | Description |
| - | - | - |
| `query` | string | Free-text search matched against model names, slugs, and descriptions |
| `input_modalities` | string\[] | Filter by supported input modalities (`text`, `image`, `file`, `audio`, `video`). Returns models that support ALL specified modalities |
| `output_modalities` | string\[] | Filter by supported output modalities (e.g. `text`, `image`, `embeddings`, `audio`). Returns models that support ALL specified modalities |
| `min_context_length` | integer | Minimum context length in tokens |
| `series` | string | Filter by model series/family group (e.g. `Claude`, `GPT`, `Gemini`) |

## Response

The tool returns matching models with their key attributes:

```json lines theme={null}
{
  "models": [
    {
      "id": "anthropic/claude-sonnet-4.5",
      "name": "Anthropic: Claude Sonnet 4.5",
      "description": "...",
      "context_length": 1000000,
      "input_modalities": ["text", "image", "file"],
      "output_modalities": ["text"],
      "series": "Claude"
    }
  ],
  "total_results": 12,
  "showing": 1
}
```

`total_results` is the number of models that matched the filters; `showing` is how many were returned after applying `max_results`.

## Pricing

There is currently no separate charge for the search models tool; you pay only for standard token usage.

## Next Steps

* [Server Tools Overview](../server-tools.md). Learn about server tools
* [Subagent](subagent.md). Delegate tasks to a worker model
* [Models](../../overview/models.md). Learn about the OpenRouter model catalog
