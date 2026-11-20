> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# PydanticAI

> Using OpenRouter with PydanticAI

## Using PydanticAI

[PydanticAI](https://github.com/pydantic/pydantic-ai) provides a high-level interface for working with various LLM providers, including OpenRouter.

### Installation

```bash lines theme={null}
pip install 'pydantic-ai-slim[openai]'
```

### Configuration

You can use OpenRouter with PydanticAI through its OpenAI-compatible interface:

```python lines theme={null}
from pydantic_ai import Agent
from pydantic_ai.models.openai import OpenAIModel

model = OpenAIModel(
    "anthropic/claude-sonnet-4.6",  # or any other OpenRouter model
    base_url="https://openrouter.ai/api/v1",
    api_key="sk-or-...",
)

agent = Agent(model)
result = await agent.run("What is the meaning of life?")
print(result)
```

```text title="Output" theme={null}
The meaning of life is one of humanity's oldest and most debated questions. Here are some perspectives:

**Philosophical views:**
- **Existentialism** (Sartre, Camus): Life has no inherent meaning; we create our own
- **Aristotle**: Living virtuously and pursuing *eudaimonia* (flourishing/well-being)
- **Stoicism**: Living according to reason and nature

**Religious/Spiritual views:**
- Fulfilling a divine purpose
- Spiritual growth or enlightenment
- Love, service, and connection to something greater

**Scientific perspective:**
- Biologically, survival and reproduction
- Though many find this incomplete as a full answer

**Practical answers people commonly find meaningful:**
- Relationships and love
- Contributing to others
- Personal growth
- Creating something lasting
- Experiencing joy and beauty

**The honest answer** is that there's no single universally agreed-upon answer. This may actually be useful - it means you have genuine freedom to determine what makes life meaningful *to you*.

The question itself might matter as much as any answer - it pushes us to reflect on what we actually value.

What draws you to the question? I'm happy to explore any angle more deeply.
```

The output above is the answer text only. `print(result)` prints the whole run result object that wraps this text. To print just the answer, print the result's text attribute: `result.output` in current PydanticAI releases, `result.data` in older ones.

For more details about using PydanticAI with OpenRouter, see the [PydanticAI documentation](https://ai.pydantic.dev/models/#api_key-argument).
