> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Plugins

> Extend model capabilities with OpenRouter plugins

OpenRouter plugins extend the capabilities of any model by injecting or mutating a request or response to add functionality like PDF processing, automatic JSON repair, and context compression. Unlike [server tools](server-tools.md) (which the model can call 0-N times), plugins always run once when enabled. Plugins can be enabled per-request via the API or configured as defaults for all your API requests through the [Plugins settings page](https://openrouter.ai/settings/plugins).

Plugins use the `plugins` array; server tools use the `tools` array. [ZDR enforcement](zdr.md) filters the model inference endpoint, not plugin backends, with one exception: the [Web Search plugin](plugins/web-search.md) rejects the Firecrawl engine when ZDR is enforced in your account privacy settings or a guardrail. On [In-Region Routing](in-region-routing.md) endpoints, a plugin engine that is not resident in the region returns an error. See [Privacy and regional availability](server-tools.md#privacy-and-regional-availability).

## Available Plugins

OpenRouter currently supports the following plugins:

| Plugin | Description | Docs |
| - | - | - |
| **Web Search** (deprecated) | Augment LLM responses with real-time web search results. Use the [`openrouter:web_search` server tool](server-tools/web-search.md) instead. | [Web Search](plugins/web-search.md) |
| **PDF Inputs** | Parse and extract content from uploaded PDF files | [PDF Inputs](../overview/multimodal/pdfs.md) |
| **Response Healing** | Automatically fix malformed JSON responses from LLMs | [Response Healing](plugins/response-healing.md) |
| **Alignment** (beta) | Check every assistant message against rules sent with the request, in audit or enforce mode | [Alignment](plugins/alignment.md) |
| **Armor** (beta) | A safety classifier for tool calls: write rules in plain English, and calls that break them never reach your application | [Armor](plugins/armor.md) |
| **Pareto Router** | Set a default coding quality tier for the Pareto code router | [Pareto Router](../routing/routers/pareto-router.md) |
| **Context Compression** | Compress prompts that exceed a model's context window using middle-out truncation | [Message Transforms](message-transforms.md) |

## Enabling Plugins via API

Plugins are enabled by adding a `plugins` array to your [Responses API](../../api_reference/responses/overview.md) request. Each plugin is identified by its `id` and can include optional configuration parameters.

```typescript title="TypeScript" expandable lines theme={null}
const response = await fetch('https://openrouter.ai/api/v1/responses', {
  method: 'POST',
  headers: {
    Authorization: 'Bearer <OPENROUTER_API_KEY>',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    model: 'openai/gpt-5.2',
    input: 'What are the latest developments in AI?',
    plugins: [
      { id: 'web' }
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
    "input": "What are the latest developments in AI?",
    "plugins": [
      {"id": "web"}
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
    "input": "What are the latest developments in AI?",
    "plugins": [
      {"id": "web"}
    ]
  }'
```

```go title="Go" lines theme={null}
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
	"net/http"
	"os"
)

func main() {
	body, _ := json.Marshal(map[string]any{
		"model": "openai/gpt-5.2",
		"input": "What are the latest developments in AI?",
		"plugins": []map[string]any{
			{"id": "web"},
		},
	})

	req, _ := http.NewRequest("POST", "https://openrouter.ai/api/v1/responses", bytes.NewReader(body))
	req.Header.Set("Authorization", "Bearer "+os.Getenv("OPENROUTER_API_KEY"))
	req.Header.Set("Content-Type", "application/json")

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		panic(err)
	}
	defer resp.Body.Close()

	// An error response has no output, so check the status before decoding
	if resp.StatusCode != http.StatusOK {
		panic("OpenRouter rejected the request: " + resp.Status)
	}

	var data struct {
		Output []struct {
			Type    string `json:"type"`
			Content []struct {
				Type string `json:"type"`
				Text string `json:"text"`
			} `json:"content"`
		} `json:"output"`
	}
	if err := json.NewDecoder(resp.Body).Decode(&data); err != nil {
		panic(err)
	}

	for i := len(data.Output) - 1; i >= 0; i-- {
		if data.Output[i].Type != "message" {
			continue
		}
		for _, part := range data.Output[i].Content {
			if part.Type == "output_text" {
				fmt.Println(part.Text)
				return
			}
		}
		return
	}
}

```

```text title="Output" theme={null}
As of **November 17, 2026**, the biggest “latest developments” in AI cluster around a few themes:

## 1) New model launches + cheaper “frontier-ish” performance
- **Microsoft** announced **six new AI models** at its Ignite conference, positioning them as specialized, lower-cost options that can rival leading models from other top labs for certain use cases—while also signaling it’s progressing toward building its own general-purpose frontier model. ([axios.com](https://www.axios.com/2026/11/17/microsoft-ai-models-openai-anthropic-ignite?utm_source=openai))  
- **Google** has been rolling AI deeper into consumer surfaces (notably Search) with an update reported as being powered by its newest **Gemini 4 “Hydrogen”** model. ([androidcentral.com](https://www.androidcentral.com/apps-software/ai/visual-flair-googles-gemini-4-hydrogen-ai-search-a-lot-more-casual?utm_source=openai))  

## 2) “Agentic AI” is moving from demos to real deployments (and real risk)
- Research is converging on agents that can **plan multi-step workflows, use tools/APIs, retrieve information (RAG), and coordinate in multi-agent setups**—with a growing literature cataloging capabilities and open problems. ([link.springer.com](https://link.springer.com/article/10.1007/s44163-026-02342-5?utm_source=openai))  
- Microsoft Research highlighted work on agents learning usable “skills” from **tutorial-like multimodal resources** (i.e., turning documentation/videos into executable workflows). ([microsoft.com](https://www.microsoft.com/en-us/research/articles/resource2skill-teaching-ai-agents-to-learn-skills-from-tutorials-and-other-multimodal-resources/?utm_source=openai))  
- At the same time, agents are becoming a **policy and legal flashpoint**: California has reportedly sued OpenAI seeking court-ordered changes after what was described as a “Hugging Face hack” involving autonomous agents. ([apnews.com](https://apnews.com/article/1dd7be56134b4f09fb2fb974803edc69?utm_source=openai))  

## 3) Regulation is becoming more concrete—especially around “frontier” thresholds
- The White House published **Executive Order 14409 (June 2, 2026)** on AI innovation and security, including government processes around assessing high-end systems. ([whitehouse.gov](https://www.whitehouse.gov/wp-content/uploads/2026/06/eo-14409.pdf?utm_source=openai))  
- A Congressional Research Service writeup summarizes that the order called for a **classified benchmarking process** to determine whether a system qualifies as a **“covered frontier model”** (with deadlines specified in mid-2026). ([everycrsreport.com](https://www.everycrsreport.com/files/2026-07-09_IF13268_27c6b7744b8ad38961f4c3c00689ce5b8fe1d63c.pdf?utm_source=openai))  

## 4) Compute, chips, and infrastructure are the bottleneck—and the battlefield
- AI’s power demand and data-center buildout are under scrutiny; reporting notes signs of a **data-center construction slowdown** alongside growing attention to energy impacts. ([axios.com](https://www.axios.com/newsletters/axios-future-of-energy-db9b4190-e1c8-11f1-9adf-df0950ba531f?utm_source=openai))  
- On the hardware/software stack, there’s momentum toward **heterogeneous inference** (splitting workloads across CPU/GPU/NPU) and OS/runtime layers that make local inference easier. ([tomshardware.com](https://www.tomshardware.com/software/linux/cyanogen-co-founder-unveils-kora-a-linux-os-that-splits-ai-models-across-the-cpu-gpu-and-npu-snapdragon-x2-elite-and-hexagon-npu-get-full-support-first?utm_source=openai))  
- Internationally, Huawei described “SuperCluster” concepts aimed at scaling AI compute by linking massive numbers of chips. ([livescience.com](https://www.livescience.com/technology/computing/huawei-unveils-supercluster-architecture-designed-to-make-1-million-ai-chips-work-as-a-single-computer?utm_source=openai))  

## 5) Geopolitics: export controls and “AI supply chain” controls are tightening
- U.S. policy focus continues to be on preventing **indirect access** to advanced American AI technology (chips, infrastructure, and related pathways), per recent reporting. ([apnews.com](https://apnews.com/article/60f868d3bb430b85a8657b27d421096e?utm_source=openai))  

## 6) AI creation tools keep expanding (with more “control” emphasis)
- Creator software (e.g., Adobe ecosystem announcements around Adobe Max) continues integrating AI features, alongside messaging that some users want non-AI workflows and more control over how AI is used. ([digitalcameraworld.com](https://www.digitalcameraworld.com/tech/live/the-biggest-lightroom-and-photoshop-updates-could-be-just-around-the-corner-heres-how-to-watch-adobe-maxs-biggest-announcements?utm_source=openai))  

If you tell me whether you care most about **model releases**, **AI agents**, **regulation**, **hardware/NPUs**, or **enterprise adoption**, I can zoom in and list the most important recent announcements in that slice (with dates and who shipped what).
```

## Using Multiple Plugins

You can enable multiple plugins in a single request:

```json lines theme={null}
{
  "model": "openai/gpt-5.2",
  "input": [...],
  "plugins": [
    { "id": "web", "max_results": 3 },
    { "id": "response-healing" }
  ],
  "text": {
    "format": {
      "type": "json_schema",
      "name": "...",
      "schema": { ... }
    }
  }
}
```

## Default Plugin Settings

Organization admins and individual users can configure default plugin settings that apply to all API requests. This is useful for:

* Enabling plugins like web search or response healing by default across all requests
* Setting consistent plugin configurations without modifying application code
* Enforcing plugin settings that cannot be overridden by individual requests

To configure default plugin settings:

1. Navigate to [Settings > Plugins](https://openrouter.ai/settings/plugins)
2. Toggle plugins on/off to enable them by default
3. Click the configure button to customize plugin settings
4. Optionally enable "Prevent overrides" to enforce settings across all requests

> [!WARNING]
>
> In organizations, the Plugins settings page is only accessible to admins.

> [!NOTE]
>
> When "Prevent overrides" is enabled for a plugin, individual API requests cannot disable or modify that plugin's configuration. This is useful for enforcing organization-wide policies.

### Plugin precedence

Plugin settings are applied in the following order of precedence:

1. **Request-level settings**: Plugin configurations in the `plugins` array of individual requests
2. **Account defaults**: Settings configured in the Plugins settings page

If a plugin is enabled in your account defaults but not specified in a request, the default configuration will be applied. If you specify a plugin in your request, those settings will override the defaults.

If you want the account setting to take precedence, toggle on "Prevent overrides" in the config for the plugin. It will then be impossible for generations to override the config.

### Disabling a default plugin

If a plugin is enabled by default in your account settings, you can disable it for a specific request by passing `"enabled": false` in the plugins array:

```json lines theme={null}
{
  "model": "openai/gpt-5.2",
  "input": [...],
  "plugins": [
    { "id": "web", "enabled": false }
  ]
}
```

This will turn off the web search plugin for that particular request, even if it's enabled in your account defaults.

## Model Variants as Plugin Shortcuts

> [!WARNING]
>
> **Deprecated**
>
> The `:online` variant and the web search plugin are deprecated. Use the [`openrouter:web_search` server tool](server-tools/web-search.md) instead.

Some plugins have convenient model variant shortcuts. For example, appending `:online` to any model ID enables web search:

```json lines theme={null}
{
  "model": "openai/gpt-5.2:online"
}
```

This is equivalent to:

```json lines theme={null}
{
  "model": "openai/gpt-5.2",
  "plugins": [{ "id": "web" }]
}
```

See [Model Variants](../routing/model-variants/online.md) for more information about available shortcuts.
