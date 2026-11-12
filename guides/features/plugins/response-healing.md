> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Response Healing

> Automatically fix malformed JSON responses

The Response Healing plugin automatically validates and repairs malformed JSON responses from AI models. When models return imperfect formatting – missing brackets, trailing commas, markdown wrappers, or mixed text – this plugin attempts to repair the response so you receive valid, parseable JSON.

## Overview

Response Healing provides:

* **Automatic JSON repair**: Fixes missing brackets, commas, quotes, and other syntax errors
* **Markdown extraction**: Extracts JSON from markdown code blocks

## How It Works

The plugin activates for non-streaming requests when you set `text.format` in a [Responses API](../../../api_reference/responses/overview.md) request (or `response_format` on Chat Completions) to either `type: "json_schema"` or `type: "json_object"`, and include the response-healing plugin in your `plugins` array. See the [Complete Example](#complete-example) below for a full implementation.

## What Gets Fixed

The Response Healing plugin handles common issues in LLM responses:

### JSON Syntax Errors

**Input:** Missing closing bracket

```text lines theme={null}
{"name": "Alice", "age": 30
```

**Output:** Fixed

```json lines theme={null}
{"name": "Alice", "age": 30}
```

### Markdown Code Blocks

**Input:** Wrapped in markdown

````text lines theme={null}
```json
{"name": "Bob"}
```
````

**Output:** Extracted

```json lines theme={null}
{"name": "Bob"}
```

### Mixed Text and JSON

**Input:** Text before JSON

```text lines theme={null}
Here's the data you requested:
{"name": "Charlie", "age": 25}
```

**Output:** Extracted

```json lines theme={null}
{"name": "Charlie", "age": 25}
```

### Trailing Commas

**Input:** Invalid trailing comma

```text lines theme={null}
{"name": "David", "age": 35,}
```

**Output:** Fixed

```json lines theme={null}
{"name": "David", "age": 35}
```

### Unquoted Keys

**Input:** JavaScript-style

```text lines theme={null}
{name: "Eve", age: 40}
```

**Output:** Fixed

```json lines theme={null}
{"name": "Eve", "age": 40}
```

## Complete Example

```typescript title="TypeScript" expandable lines theme={null}
const response = await fetch('https://openrouter.ai/api/v1/responses', {
  method: 'POST',
  headers: {
    Authorization: 'Bearer <OPENROUTER_API_KEY>',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    model: 'google/gemini-2.5-flash',
    input: 'Generate a product listing with name, price, and description',
    text: {
      format: {
        type: 'json_schema',
        name: 'Product',
        schema: {
          type: 'object',
          properties: {
            name: {
              type: 'string',
              description: 'Product name'
            },
            price: {
              type: 'number',
              description: 'Price in USD'
            },
            description: {
              type: 'string',
              description: 'Product description'
            }
          },
          required: ['name', 'price']
        }
      }
    },
    plugins: [
      { id: 'response-healing' }
    ]
  }),
});

const data = await response.json();
const message = [...data.output].reverse().find((item: { type: string }) => item.type === 'message');
const text = message?.content.find((part: { type: string; text?: string }) => part.type === 'output_text')?.text;
if (text === undefined) {
  throw new Error('No output_text in response');
}
// The plugin attempts to repair malformed JSON syntax
const product = JSON.parse(text);
console.log(product.name, product.price);
```

```python title="Python" expandable lines theme={null}
import requests
import json

response = requests.post(
  "https://openrouter.ai/api/v1/responses",
  headers={
    "Authorization": f"Bearer <OPENROUTER_API_KEY>",
    "Content-Type": "application/json",
  },
  json={
    "model": "google/gemini-2.5-flash",
    "input": "Generate a product listing with name, price, and description",
    "text": {
      "format": {
        "type": "json_schema",
        "name": "Product",
        "schema": {
          "type": "object",
          "properties": {
            "name": {
              "type": "string",
              "description": "Product name"
            },
            "price": {
              "type": "number",
              "description": "Price in USD"
            },
            "description": {
              "type": "string",
              "description": "Product description"
            }
          },
          "required": ["name", "price"]
        }
      }
    },
    "plugins": [
      {"id": "response-healing"}
    ]
  }
)

data = response.json()
message = next(item for item in reversed(data["output"]) if item["type"] == "message")
product = json.loads(
  next(part["text"] for part in message["content"] if part["type"] == "output_text")
)
# The plugin attempts to repair malformed JSON syntax
print(product["name"], product["price"])
```

## Limitations

> [!WARNING]
>
> **Non-Streaming Requests Only**
>
> Response Healing only applies to non-streaming requests.

> [!WARNING]
>
> **Will not repair all JSON**
>
> Some malformed JSON responses may still be unrepairable. In particular, if the response is truncated by `max_output_tokens`, the plugin will not be able to repair it.
