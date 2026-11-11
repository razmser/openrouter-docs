> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Authentication

> API Authentication

You can cover model costs with OpenRouter API keys.

Our API authenticates requests using Bearer tokens. This allows you to use `curl` or the [OpenAI SDK](https://platform.openai.com/docs/frameworks) directly with OpenRouter.

> [!WARNING]
>
> API keys on OpenRouter are more powerful than keys used directly for model APIs.
>
> They allow users to set credit limits for apps, and they can be used in [OAuth](../guides/overview/auth/oauth.md) flows.

## Accepted credentials

Send one credential per request in the `Authorization` header as `Bearer <credential>`. For clients built on the Anthropic SDK, you can also send an API key (not an access token) in the `x-api-key` header. OpenRouter accepts the following credential types:

| Credential | Format | How you get it |
| - | - | - |
| API key | `sk-or-v1-` followed by 64 lowercase hexadecimal characters, for example `sk-or-v1-0123…cdef` (73 characters in total). | Create one on the [API keys page](https://openrouter.ai/keys), or receive one through [OAuth PKCE](../guides/overview/auth/oauth.md). [Management keys](../guides/overview/auth/management-api-keys.md) use the same format. |
| OpenRouter access token | A signed JWT (three base64url segments separated by `.`) with `typ: at+jwt`, issuer `https://openrouter.ai`, and an `inference` or `management` scope. Signed with `ES256`; public keys are at `https://openrouter.ai/api/v1/oauth/jwks`. Valid for at most 15 minutes. | Exchange a JWT from your own identity provider with [workload identity federation](../guides/overview/auth/workload-identity-federation.md). |
| OpenRouter sign-in (OIDC) access token | A signed JWT issued by `https://clerk.openrouter.ai` that carries the `inference` scope. | Sign in to OpenRouter through an OIDC client, for example [Claude Desktop with OpenRouter sign-in](https://openrouter.ai/docs/cookbook/coding-agents/claude-desktop-oidc). |

Send the credential exactly as issued, with no extra whitespace or quotes. OpenRouter treats a bearer that starts with `sk-or-v1-` as an API key. It treats a JWT as an access token only when its issuer is `https://openrouter.ai` or `https://clerk.openrouter.ai`, and rejects any other bearer. OpenRouter also rejects an expired JWT and a JWT without the scope the endpoint requires. Some endpoints accept only an API key, so an access token with the `inference` scope doesn't replace an API key everywhere. To use a token from your own identity provider, exchange it for an OpenRouter access token first; OpenRouter doesn't accept third-party JWTs directly.

## Using an API key

To use an API key, [first create your key](https://openrouter.ai/keys). Give it a name and choose a credit limit (or no limit). Once a key has used its credit limit, requests with it are rejected until you raise the limit on the key's page, or, for a daily, weekly, or monthly limit, until the limit resets. Keys created for you during onboarding get a \$100 credit limit and expire after 180 days.

> [!WARNING]
>
> We recommend setting a credit limit on every key. A key with no limit lets a leaked key or a runaway agent spend your entire balance, including any auto top-ups. If you need a key without a limit, keep it out of client-side code and rotate it promptly if you suspect it has been [exposed](#if-your-key-has-been-exposed).

If you're calling the OpenRouter API directly, set the `Authorization` header to a Bearer token with your API key.

If you're using the OpenAI Typescript SDK, set the `api_base` to `https://openrouter.ai/api/v1` and the `apiKey` to your API key.

```typescript title="TypeScript SDK" lines theme={null}
import { OpenRouter } from '@openrouter/sdk';

const openRouter = new OpenRouter({
  apiKey: '<OPENROUTER_API_KEY>',
  httpReferer: '<YOUR_SITE_URL>', // Optional. Site URL for rankings on openrouter.ai.
  appTitle: '<YOUR_SITE_NAME>', // Optional. Site title for rankings on openrouter.ai.
});

const response = await openRouter.responses.send({
  responsesRequest: {
    model: 'openai/gpt-5.2',
    input: 'Say this is a test',
    stream: false,
  },
});

if (!('output' in response)) {
  throw new Error('Expected a non-streaming response');
}

console.log([...response.output].reverse().find((item) => item.type === 'message'));
```

```python title="Python (OpenAI SDK)" lines theme={null}
from openai import OpenAI

client = OpenAI(
  base_url="https://openrouter.ai/api/v1",
  api_key="<OPENROUTER_API_KEY>",
)

response = client.responses.create(
  extra_headers={
    "HTTP-Referer": "<YOUR_SITE_URL>",  # Optional. Site URL for rankings on openrouter.ai.
    "X-OpenRouter-Title": "<YOUR_SITE_NAME>",     # Optional. Site title for rankings on openrouter.ai.
  },
  model="openai/gpt-5.2",
  instructions="You are a helpful assistant.",
  input="Hello!",
)

reply = response.output_text
```

```typescript title="TypeScript (OpenAI SDK)" expandable lines theme={null}
import OpenAI from 'openai';

const openai = new OpenAI({
  baseURL: 'https://openrouter.ai/api/v1',
  apiKey: '<OPENROUTER_API_KEY>',
  defaultHeaders: {
    'HTTP-Referer': '<YOUR_SITE_URL>', // Optional. Site URL for rankings on openrouter.ai.
    'X-OpenRouter-Title': '<YOUR_SITE_NAME>', // Optional. Site title for rankings on openrouter.ai.
  },
});

async function main() {
  const response = await openai.responses.create({
    model: 'openai/gpt-5.2',
    input: 'Say this is a test',
  });

  console.log(response.output_text);
}

main();
```

```typescript title="TypeScript (Raw API)" lines theme={null}
fetch('https://openrouter.ai/api/v1/responses', {
  method: 'POST',
  headers: {
    Authorization: 'Bearer <OPENROUTER_API_KEY>',
    'HTTP-Referer': '<YOUR_SITE_URL>', // Optional. Site URL for rankings on openrouter.ai.
    'X-OpenRouter-Title': '<YOUR_SITE_NAME>', // Optional. Site title for rankings on openrouter.ai.
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    model: 'openai/gpt-5.2',
    input: 'What is the meaning of life?',
  }),
});
```

```shell title="cURL" lines theme={null}
curl https://openrouter.ai/api/v1/responses \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -d '{
  "model": "openai/gpt-5.2",
  "instructions": "You are a helpful assistant.",
  "input": "Hello!"
}'
```

To stream responses, see [Streaming](streaming.md).

## If your key has been exposed

> [!WARNING]
>
> You must protect your API keys and never commit them to public repositories.

OpenRouter is a GitHub secret scanning partner, and has other methods to detect exposed keys. If we determine that your key has been compromised, you will receive an email notification.

If you receive such a notification or suspect your key has been exposed, immediately visit [your key settings page](https://openrouter.ai/settings/keys) to delete the compromised key and create a new one.

Using environment variables and keeping keys out of your codebase is strongly recommended.
