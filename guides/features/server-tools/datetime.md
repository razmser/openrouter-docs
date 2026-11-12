> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Datetime

> Give any model access to the current date and time

Beta

> [!NOTE]
>
> **Beta**
>
> Server tools are currently in beta. The API and behavior may change.

The `openrouter:datetime` server tool gives any model access to the current date and time. This is useful for prompts that require temporal awareness: scheduling, time-sensitive questions, or any task where the model needs to know "right now."

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
    input: 'What day of the week is it today?',
    tools: [
      { type: 'openrouter:datetime' }
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
    "input": "What day of the week is it today?",
    "tools": [
      {"type": "openrouter:datetime"}
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
    "input": "What day of the week is it today?",
    "tools": [
      {"type": "openrouter:datetime"}
    ]
  }'
```

## Configuration

The datetime tool accepts an optional `timezone` parameter:

```json lines theme={null}
{
  "type": "openrouter:datetime",
  "parameters": {
    "timezone": "America/New_York"
  }
}
```

| Parameter | Type | Default | Description |
| - | - | - | - |
| `timezone` | string | `UTC` | IANA timezone name (e.g. `"America/New_York"`, `"Europe/London"`, `"Asia/Tokyo"`) |

## Response

When the model calls the datetime tool, it receives a response like:

```json lines theme={null}
{
  "datetime": "2025-07-15T14:30:00.000-04:00",
  "timezone": "America/New_York"
}
```

## Pricing

The datetime tool has no additional cost beyond standard token usage.

## Next Steps

* [Server Tools Overview](../server-tools.md). Learn about server tools
* [Web Search](web-search.md). Search the web for real-time information
* [Tool Calling](../tool-calling.md). Learn about user-defined tool calling
