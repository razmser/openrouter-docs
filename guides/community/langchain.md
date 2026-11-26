> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# LangChain

> Using OpenRouter with LangChain

## Using LangChain

LangChain provides a standard interface for working with chat models. You can use OpenRouter with LangChain using the dedicated `ChatOpenRouter` integration packages. For more details on LangChain's model interface, see the [LangChain Models documentation](https://docs.langchain.com/oss/python/langchain/models).

**Resources:**

* [LangChain Python integration](https://docs.langchain.com/oss/python/integrations/chat/openrouter): [langchain-openrouter on PyPI](https://pypi.org/project/langchain-openrouter/)
* [LangChain JavaScript integration](https://docs.langchain.com/oss/javascript/integrations/chat/openrouter): [@langchain/openrouter on npm](https://www.npmjs.com/package/@langchain/openrouter)

```typescript title="TypeScript" lines theme={null}
import { ChatOpenRouter } from "@langchain/openrouter";

const model = new ChatOpenRouter(
  "anthropic/claude-sonnet-4.6",
  { temperature: 0.8 }
);

// Example usage
const response = await model.invoke([
  { role: "system", content: "You are a helpful assistant." },
  { role: "user", content: "Hello, how are you?" },
]);

console.log(response.content);

```

```python title="Python" lines theme={null}
from langchain_openrouter import ChatOpenRouter

model = ChatOpenRouter(
    model="anthropic/claude-sonnet-4.6",
    temperature=0.8,
)

# Example usage
response = model.invoke("What NFL team won the Super Bowl in the year Justin Bieber was born?")
print(response.content)
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
		"model":       "anthropic/claude-sonnet-4.6",
		"temperature": 0.8,
		"messages": []map[string]string{
			{"role": "system", "content": "You are a helpful assistant."},
			{"role": "user", "content": "Hello, how are you?"},
		},
	})

	req, _ := http.NewRequest("POST", "https://openrouter.ai/api/v1/chat/completions", bytes.NewReader(body))
	req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
	req.Header.Set("Content-Type", "application/json")

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		log.Fatal(err)
	}
	defer resp.Body.Close()

	var result struct {
		Choices []struct {
			Message struct {
				Content string `json:"content"`
			} `json:"message"`
		} `json:"choices"`
	}
	if err := json.NewDecoder(resp.Body).Decode(&result); err != nil {
		log.Fatal(err)
	}
	if len(result.Choices) == 0 {
		log.Fatalf("no choices returned (status %s)", resp.Status)
	}

	fmt.Println(result.Choices[0].Message.Content)
}

```

```bash title="cURL" lines theme={null}
curl -s https://openrouter.ai/api/v1/chat/completions \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "anthropic/claude-sonnet-4.6",
    "temperature": 0.8,
    "messages": [
      {"role": "system", "content": "You are a helpful assistant."},
      {"role": "user", "content": "Hello, how are you?"}
    ]
  }' | jq -r '.choices[0].message.content'

```

```text title="Output" theme={null}
Hello! I'm doing well, thanks for asking! How are you doing today? Is there something I can help you with? 😊
```

For full documentation (including streaming, tool calling, structured output, reasoning, multimodal inputs, provider routing, and more), see the LangChain integration guides:

* [Python: ChatOpenRouter](https://docs.langchain.com/oss/python/integrations/chat/openrouter)
* [JavaScript: ChatOpenRouter](https://docs.langchain.com/oss/javascript/integrations/chat/openrouter)
