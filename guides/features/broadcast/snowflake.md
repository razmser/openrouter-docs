> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Snowflake

> Send traces to Snowflake

[Snowflake](https://snowflake.com) is a cloud data warehouse platform. OpenRouter can stream traces directly to your Snowflake database for custom analytics, long-term storage, and business intelligence.

## Step 1: Create the traces table

Before connecting OpenRouter, create the `OPENROUTER_TRACES` table in your Snowflake database. You can find the exact SQL in the OpenRouter dashboard when configuring the destination:

![Snowflake Table Setup](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/snowflake/snowflake-table-setup.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=83994af0ee94bbff8486e910111bfe04)

## Step 2: Create access credentials

Generate a [Programmatic Access Token](https://docs.snowflake.com/en/user-guide/programmatic-access-tokens) with `ACCOUNTADMIN` permissions in the Snowflake UI under **Settings > Authentication**.

![Snowflake PAT](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/snowflake/snowflake-pat.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=111ae5fbdde62174613ae3ce4b0abad7)

## Step 3: Enable Broadcast in OpenRouter

Go to [Settings > Observability](https://openrouter.ai/settings/observability) and toggle **Enable Broadcast**.

![Enable Broadcast](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/arize/broadcast-enable.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=a48ecd5df85b4e6f3982c8402671f631)

## Step 4: Configure Snowflake

Click the edit icon next to **Snowflake** and enter:

* **Account**: Your Snowflake account identifier (e.g., `eac52885.us-east-1`). You can find your account region and your account number at the end of your Snowflake instance's URL: [https://app.snowflake.com/us-east-1/eac52885](https://app.snowflake.com/us-east-1/eac52885); together these make your account identifier.
* **Token**: Your Programmatic Access Token.
* **Database**: Target database name (default: `SNOWFLAKE_LEARNING_DB`).
* **Schema**: Target schema name (default: `PUBLIC`).
* **Table**: Table name (default: `OPENROUTER_TRACES`).
* **Warehouse**: Compute warehouse name (default: `COMPUTE_WH`).

## Step 5: Test and save

Click **Test Connection** to verify the setup. The configuration only saves if the test passes.

## Step 6: Send a test trace

Make an API request through OpenRouter and query your Snowflake table to verify the trace was received.

![Snowflake Test Trace](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/snowflake/snowflake-test-trace.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=35f3639a8aa372dd3b5635a2e9cb84dc)

## Example queries

### Cost analysis by model

```sql lines theme={null}
SELECT
  DATE_TRUNC('day', TIMESTAMP) as day,
  MODEL,
  SUM(TOTAL_COST) as total_cost,
  SUM(TOTAL_TOKENS) as total_tokens,
  COUNT(*) as request_count
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= DATEADD(day, -30, CURRENT_TIMESTAMP())
  AND STATUS = 'ok'
  AND SPAN_TYPE = 'GENERATION'
GROUP BY day, MODEL
ORDER BY day DESC, total_cost DESC;
```

### User activity analysis

```sql lines theme={null}
SELECT
  USER_ID,
  COUNT(DISTINCT TRACE_ID) as trace_count,
  COUNT(DISTINCT SESSION_ID) as session_count,
  SUM(TOTAL_TOKENS) as total_tokens,
  SUM(TOTAL_COST) as total_cost,
  AVG(DURATION_MS) as avg_duration_ms
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= DATEADD(day, -7, CURRENT_TIMESTAMP())
  AND SPAN_TYPE = 'GENERATION'
GROUP BY USER_ID
ORDER BY total_cost DESC;
```

### Error analysis

```sql lines theme={null}
SELECT
  TRACE_ID,
  TIMESTAMP,
  MODEL,
  LEVEL,
  FINISH_REASON,
  METADATA as user_metadata,
  INPUT,
  OUTPUT
FROM OPENROUTER_TRACES
WHERE STATUS = 'error'
  AND TIMESTAMP >= DATEADD(hour, -1, CURRENT_TIMESTAMP())
ORDER BY TIMESTAMP DESC;
```

### Provider performance comparison

```sql lines theme={null}
SELECT
  PROVIDER_NAME,
  MODEL,
  AVG(DURATION_MS) as avg_duration_ms,
  PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY DURATION_MS) as p50_duration_ms,
  PERCENTILE_CONT(0.95) WITHIN GROUP (ORDER BY DURATION_MS) as p95_duration_ms,
  COUNT(*) as request_count
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= DATEADD(day, -7, CURRENT_TIMESTAMP())
  AND STATUS = 'ok'
  AND SPAN_TYPE = 'GENERATION'
GROUP BY PROVIDER_NAME, MODEL
HAVING request_count >= 10
ORDER BY avg_duration_ms;
```

### Usage by API key

```sql lines theme={null}
SELECT
  API_KEY_NAME,
  COUNT(DISTINCT TRACE_ID) as trace_count,
  SUM(TOTAL_COST) as total_cost,
  SUM(PROMPT_TOKENS) as prompt_tokens,
  SUM(COMPLETION_TOKENS) as completion_tokens
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= DATEADD(day, -30, CURRENT_TIMESTAMP())
  AND SPAN_TYPE = 'GENERATION'
GROUP BY API_KEY_NAME
ORDER BY total_cost DESC;
```

### Accessing VARIANT columns

```sql lines theme={null}
SELECT
  TRACE_ID,
  METADATA:custom_field::STRING as custom_value,
  ATTRIBUTES:"gen_ai.request.model"::STRING as requested_model
FROM OPENROUTER_TRACES
WHERE METADATA:custom_field IS NOT NULL;
```

### Parsing input messages

```sql lines theme={null}
SELECT
  TRACE_ID,
  INPUT:messages[0]:role::STRING as first_message_role,
  INPUT:messages[0]:content::STRING as first_message_content
FROM OPENROUTER_TRACES
WHERE SPAN_TYPE = 'GENERATION';
```

## Schema design

The dashboard-generated `CREATE TABLE` statement is the source of truth for setup. The field reference below describes the current schema without duplicating the generated SQL.

### Field reference

| Column | Snowflake type | Meaning |
| - | - | - |
| `TRACE_ID` | `VARCHAR(128) NOT NULL` | Trace identifier shared by all observations in a trace. |
| `SPAN_ID` | `VARCHAR(128) NOT NULL` | Unique identifier for this observation. |
| `PARENT_SPAN_ID` | `VARCHAR(128)` | Parent observation identifier, or `NULL` for an unparented observation. |
| `USER_ID` | `VARCHAR(256)` | End-user identifier from the request. |
| `SESSION_ID` | `VARCHAR(256)` | Session identifier used to group related requests. |
| `ORGANIZATION_ID` | `VARCHAR(256)` | Organization that owns the trace. |
| `ENTITY_ID` | `VARCHAR(256) NOT NULL` | Entity that owns the trace. |
| `API_KEY_NAME` | `VARCHAR(256)` | User-defined name of the API key used for the request. |
| `TIMESTAMP` | `TIMESTAMP_NTZ NOT NULL` | Trace creation timestamp. |
| `START_TIME` | `TIMESTAMP_NTZ NOT NULL` | Observation start time. |
| `END_TIME` | `TIMESTAMP_NTZ` | Observation end time, or `NULL` when unavailable. |
| `DURATION_MS` | `NUMBER(18, 3)` | Observation duration in milliseconds. |
| `MODEL` | `VARCHAR(256)` | Model name used for the observation. |
| `PROVIDER_NAME` | `VARCHAR(256)` | Provider name for the observation. |
| `PROVIDER_SLUG` | `VARCHAR(256)` | Provider slug identifier. |
| `STATUS` | `VARCHAR(256) NOT NULL` | `ok` or `error`; `error` is emitted only when `LEVEL` is `ERROR`. |
| `LEVEL` | `VARCHAR(64) NOT NULL` | Observation level: `DEBUG`, `INFO`, `DEFAULT`, `WARNING`, or `ERROR`. |
| `FINISH_REASON` | `VARCHAR(256)` | Completion finish reason, such as `stop` or `length`; not an enum. |
| `PROMPT_TOKENS` | `NUMBER(18, 0) NOT NULL` | Input/prompt token count. |
| `COMPLETION_TOKENS` | `NUMBER(18, 0) NOT NULL` | Output/completion token count. |
| `TOTAL_TOKENS` | `NUMBER(18, 0) NOT NULL` | Total token count. |
| `CACHED_TOKENS` | `NUMBER(18, 0) NOT NULL` | Cached prompt token count. |
| `CACHE_WRITE_TOKENS` | `NUMBER(18, 0)` | Prompt tokens written to the provider prompt cache. Added in schema version 2; tables created from version 1 don't have this column. `NULL` when the provider did not report them, or when the destination's **Include cache\_write\_tokens** setting is off. The setting is off by default; turn it on after the table has this column. |
| `REASONING_TOKENS` | `NUMBER(18, 0) NOT NULL` | Reasoning/thinking token count. |
| `INPUT_COST` | `NUMBER(18, 8) NOT NULL` | Input cost in USD. |
| `OUTPUT_COST` | `NUMBER(18, 8) NOT NULL` | Output cost in USD. |
| `TOTAL_COST` | `NUMBER(18, 8) NOT NULL` | Total cost in USD. |
| `INPUT_UNIT_PRICE` | `NUMBER(18, 10)` | Price per input token in USD. |
| `OUTPUT_UNIT_PRICE` | `NUMBER(18, 10)` | Price per output token in USD. |
| `SPAN_TYPE` | `VARCHAR(64) NOT NULL` | Observation type: `GENERATION`, `SPAN`, or `EVENT`. |
| `SPAN_KIND` | `VARCHAR(64) NOT NULL` | Derived from `SPAN_TYPE`: `GENERATION` → `llm`, `EVENT` → `tool`, and `SPAN` → `workflow`. |
| `OPERATION_NAME` | `VARCHAR(256) NOT NULL` | Operation type derived from the API surface, such as `chat`, `embeddings`, or `image_generation`. |
| `ATTRIBUTES` | `VARIANT` | OpenTelemetry-style attributes for compatibility. |
| `INPUT` | `VARIANT` | Input data, such as request messages. |
| `OUTPUT` | `VARIANT` | Output data, such as response messages. |
| `METADATA` | `VARIANT` | Combined custom, request, guardrail, and provider-attempt metadata. |
| `TAGS` | `VARIANT` | Trace tags array. |
| `MODEL_PARAMETERS` | `VARIANT` | Model parameters, such as temperature. |
| `RESOURCE_ATTRIBUTES` | `VARIANT` | Resource attributes, including `service.name` and the Broadcast source. |
| `SCHEMA_VERSION` | `NUMBER(5, 0) NOT NULL` | Broadcast schema version; currently defaults to `2`. |

### Field ownership and custom metadata

OpenRouter populates all columns except for the following caller-controlled values:

* `TRACE_ID` can be set with `trace.trace_id`. If supplied, the same trace ID can span multiple API requests.
* `PARENT_SPAN_ID` can be set with `trace.parent_span_id`.
* `USER_ID` comes from the request `user` field.
* `SESSION_ID` comes from the request `session_id` field.
* Custom values are stored in the `METADATA` `VARIANT` column.

Additional keys in `trace` are merged into `METADATA` using their original keys. Top-level request `metadata.<k>` values are also placed in `METADATA`, under the key `metadata_<k>`. There is no separate database column for each custom key. `trace_name` and `generation_name` affect internal trace and observation names but have no dedicated table columns. `trace.span_name` is accepted as a reserved request field but is currently ignored.

### Observation rows and aggregation

Broadcast writes one row per observation, not one row per API request. A typical request produces:

* One root `GENERATION` row with `SPAN_ID` equal to the generation ID. Its `PARENT_SPAN_ID` is `NULL` unless the request set `trace.parent_span_id`, so identify it by `SPAN_TYPE = 'GENERATION'`, not by a null parent.
* An optional `<generation_id>:moderation` `SPAN` row.
* One `<generation_id>:attempt-<i>` `SPAN` row for each provider attempt.
* An optional `<generation_id>:generation` `SPAN` row.

All rows share `TRACE_ID`. Child rows use the generation ID as `PARENT_SPAN_ID`.

> [!WARNING]
>
> Only the root `GENERATION` row carries the request's tokens and cost; the other rows report zero. Filter `SPAN_TYPE = 'GENERATION'` for per-request counts, averages, and error rates: a failed provider attempt has `STATUS = 'error'` even when a fallback then served the request.

Delivery is at least once and Snowflake's primary key is informational, so deduplicate on `(TRACE_ID, SPAN_ID)` for idempotent ingestion.

### Typed columns

The field reference above identifies commonly queried identifiers, timestamps, model information, token metrics, and cost metrics as typed columns for efficient filtering and aggregation.

### VARIANT columns

Less commonly accessed and variable-structure data is stored in the `VARIANT` columns identified in the field reference above. This design balances query performance with schema flexibility and storage efficiency.

## Custom Metadata

Custom metadata from the `trace` field is stored in the `METADATA` VARIANT column. You can query it using Snowflake's semi-structured data functions.

### Supported Metadata Keys

| Key | Snowflake Mapping | Description |
| - | - | - |
| `trace_id` | `TRACE_ID` column | Custom trace identifier for grouping |
| `parent_span_id` | `PARENT_SPAN_ID` column | Parent span identifier for linking to an existing trace |
| Additional `trace` keys | `METADATA` | Custom values stored under their original keys |
| Request `metadata.<k>` | `METADATA:metadata_<k>` | Request metadata stored with the `metadata_` prefix |

### Example

```json lines theme={null}
{
  "model": "openai/gpt-4o",
  "messages": [{ "role": "user", "content": "Forecast next quarter revenue..." }],
  "user": "user_12345",
  "session_id": "session_abc",
  "trace": {
    "trace_name": "Revenue Forecasting",
    "generation_name": "Generate Forecast",
    "department": "finance",
    "quarter": "Q2-2026",
    "model_version": "v3"
  }
}
```

### Querying Custom Metadata

Use Snowflake's VARIANT column syntax to query your custom metadata:

```sql lines theme={null}
SELECT
  TRACE_ID,
  METADATA:department::STRING as department,
  METADATA:quarter::STRING as quarter,
  METADATA:model_version::STRING as model_version,
  TOTAL_COST,
  TOTAL_TOKENS
FROM OPENROUTER_TRACES
WHERE METADATA:department IS NOT NULL
  AND SPAN_TYPE = 'GENERATION'
ORDER BY TIMESTAMP DESC;
```

### Additional Context

* The `user` field maps to the `USER_ID` typed column
* The `session_id` field maps to the `SESSION_ID` typed column
* Additional custom keys from `trace` are stored in the `METADATA` VARIANT column for flexible querying
* `trace_name` and `generation_name` affect internal names but have no dedicated table columns
* `trace.span_name` is reserved and currently ignored
* You can create materialized views on frequently queried metadata fields for better performance

## Privacy Mode

When [Privacy Mode](../broadcast.md#privacy-mode) is enabled for this destination, prompt and completion content and provider error text are excluded from traces. All other trace data — token usage, costs, timing, model information, and custom metadata — is still sent normally. See [Privacy Mode](../broadcast.md#privacy-mode) for details.
