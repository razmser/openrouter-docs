> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# ClickHouse

> Send traces to ClickHouse

[ClickHouse](https://clickhouse.com) is a fast, open-source columnar database for real-time analytics. OpenRouter can stream traces directly to your ClickHouse database for high-performance analytics and custom dashboards.

## Step 1: Create the traces table

Before connecting OpenRouter, create the `OPENROUTER_TRACES` table in your ClickHouse database. You can find the exact SQL in the OpenRouter dashboard when configuring the destination:

![ClickHouse Setup Instructions](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/clickhouse/broadcast-clickhouse-setup.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=4cacbda77bf7632cb9a5910ba8ece0b3)

## Step 2: Set up permissions

Ensure your ClickHouse user has CREATE TABLE permissions:

```sql lines theme={null}
GRANT CREATE TABLE ON your_database.* TO your_database_user;
```

## Step 3: Enable Broadcast in OpenRouter

Go to [Settings > Observability](https://openrouter.ai/settings/observability) and toggle **Enable Broadcast**.

![Enable Broadcast](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/arize/broadcast-enable.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=a48ecd5df85b4e6f3982c8402671f631)

## Step 4: Configure ClickHouse

Click the edit icon next to **ClickHouse** and enter:

![ClickHouse Configuration](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/clickhouse/broadcast-clickhouse-config.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=5b23936118f8bf9c6f8acadc6b4d8fd9)

* **Host**: Your ClickHouse HTTP endpoint (e.g., `https://clickhouse.example.com:8123`)
* **Database**: Target database name (default: `default`)
* **Table**: Table name (default: `OPENROUTER_TRACES`)
* **Username**: ClickHouse username for authentication (defaults to `default`)
* **Password**: ClickHouse password for authentication

> [!TIP]
>
> For ClickHouse Cloud, your host URL is typically `https://{instance}.{region}.clickhouse.cloud:8443`. You can find this in your ClickHouse Cloud console [under **Connect**](https://clickhouse.com/docs/cloud/guides/sql-console/gather-connection-details).

## Step 5: Test and save

Click **Test Connection** to verify the setup. The configuration only saves if the test passes.

## Step 6: Send a test trace

Make an API request through OpenRouter and query your ClickHouse table to verify the trace was received.

## Example queries

### Cost analysis by model

```sql lines theme={null}
SELECT
  toDate(TIMESTAMP) as day,
  MODEL,
  sum(TOTAL_COST) as total_cost,
  sum(TOTAL_TOKENS) as total_tokens,
  count() as request_count
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= now() - INTERVAL 30 DAY
  AND STATUS = 'ok'
  AND SPAN_TYPE = 'GENERATION'
GROUP BY day, MODEL
ORDER BY day DESC, total_cost DESC;
```

### User activity analysis

```sql lines theme={null}
SELECT
  USER_ID,
  uniqExact(TRACE_ID) as trace_count,
  uniqExact(SESSION_ID) as session_count,
  sum(TOTAL_TOKENS) as total_tokens,
  sum(TOTAL_COST) as total_cost,
  avg(DURATION_MS) as avg_duration_ms
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= now() - INTERVAL 7 DAY
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
  METADATA,
  INPUT,
  OUTPUT
FROM OPENROUTER_TRACES
WHERE STATUS = 'error'
  AND TIMESTAMP >= now() - INTERVAL 1 HOUR
ORDER BY TIMESTAMP DESC;
```

### Provider performance comparison

```sql lines theme={null}
SELECT
  PROVIDER_NAME,
  MODEL,
  avg(DURATION_MS) as avg_duration_ms,
  quantile(0.5)(DURATION_MS) as p50_duration_ms,
  quantile(0.95)(DURATION_MS) as p95_duration_ms,
  count() as request_count
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= now() - INTERVAL 7 DAY
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
  uniqExact(TRACE_ID) as trace_count,
  sum(TOTAL_COST) as total_cost,
  sum(PROMPT_TOKENS) as prompt_tokens,
  sum(COMPLETION_TOKENS) as completion_tokens
FROM OPENROUTER_TRACES
WHERE TIMESTAMP >= now() - INTERVAL 30 DAY
  AND SPAN_TYPE = 'GENERATION'
GROUP BY API_KEY_NAME
ORDER BY total_cost DESC;
```

### Accessing JSON columns

ClickHouse stores JSON data as strings. Use `JSONExtract` functions to query nested fields:

```sql lines theme={null}
SELECT
  TRACE_ID,
  JSONExtractString(METADATA, 'custom_field') as custom_value,
  JSONExtractString(ATTRIBUTES, 'gen_ai.request.model') as requested_model
FROM OPENROUTER_TRACES
WHERE JSONHas(METADATA, 'custom_field');
```

To parse input messages:

```sql lines theme={null}
SELECT
  TRACE_ID,
  JSONExtractString(
    JSONExtractRaw(INPUT, 'messages'),
    1, 'role'
  ) as first_message_role,
  JSONExtractString(
    JSONExtractRaw(INPUT, 'messages'),
    1, 'content'
  ) as first_message_content
FROM OPENROUTER_TRACES
WHERE SPAN_TYPE = 'GENERATION'
LIMIT 10;
```

## Schema design

The dashboard-generated `CREATE TABLE` statement is the source of truth for setup. The field reference below describes the current schema without duplicating the generated SQL.

### Field reference

| Column | ClickHouse type | Meaning |
| - | - | - |
| `TRACE_ID` | `String` | Trace identifier shared by all observations in a trace. |
| `SPAN_ID` | `String` | Unique identifier for this observation. |
| `PARENT_SPAN_ID` | `Nullable(String)` | Parent observation identifier, or `NULL` for an unparented observation. |
| `USER_ID` | `Nullable(String)` | End-user identifier from the request. |
| `SESSION_ID` | `Nullable(String)` | Session identifier used to group related requests. |
| `ORGANIZATION_ID` | `Nullable(String)` | Organization that owns the trace. |
| `ENTITY_ID` | `String` | Entity that owns the trace. |
| `API_KEY_NAME` | `Nullable(String)` | User-defined name of the API key used for the request. |
| `TIMESTAMP` | `DateTime64(3)` | Trace creation timestamp. |
| `START_TIME` | `DateTime64(3)` | Observation start time. |
| `END_TIME` | `Nullable(DateTime64(3))` | Observation end time, or `NULL` when unavailable. |
| `DURATION_MS` | `Nullable(Float64)` | Observation duration in milliseconds. |
| `MODEL` | `Nullable(String)` | Model name used for the observation. |
| `PROVIDER_NAME` | `Nullable(String)` | Provider name for the observation. |
| `PROVIDER_SLUG` | `Nullable(String)` | Provider slug identifier. |
| `STATUS` | `String` | `ok` or `error`; `error` is emitted only when `LEVEL` is `ERROR`. |
| `LEVEL` | `String` | Observation level: `DEBUG`, `INFO`, `DEFAULT`, `WARNING`, or `ERROR`. |
| `FINISH_REASON` | `Nullable(String)` | Completion finish reason, such as `stop` or `length`; not an enum. |
| `PROMPT_TOKENS` | `UInt64` | Input/prompt token count. |
| `COMPLETION_TOKENS` | `UInt64` | Output/completion token count. |
| `TOTAL_TOKENS` | `UInt64` | Total token count. |
| `CACHED_TOKENS` | `UInt64` | Cached prompt token count. |
| `CACHE_WRITE_TOKENS` | `Nullable(UInt64)` | Prompt tokens written to the provider prompt cache. Added in schema version 2; tables created from version 1 don't have this column. `NULL` when the provider did not report them, or when the destination's **Include cache\_write\_tokens** setting is off. The setting is off by default; turn it on after the table has this column. |
| `REASONING_TOKENS` | `UInt64` | Reasoning/thinking token count. |
| `INPUT_COST` | `Decimal(18, 8)` | Input cost in USD. |
| `OUTPUT_COST` | `Decimal(18, 8)` | Output cost in USD. |
| `TOTAL_COST` | `Decimal(18, 8)` | Total cost in USD. |
| `INPUT_UNIT_PRICE` | `Nullable(Decimal(18, 10))` | Price per input token in USD. |
| `OUTPUT_UNIT_PRICE` | `Nullable(Decimal(18, 10))` | Price per output token in USD. |
| `SPAN_TYPE` | `String` | Observation type: `GENERATION`, `SPAN`, or `EVENT`. |
| `SPAN_KIND` | `String` | Derived from `SPAN_TYPE`: `GENERATION` → `llm`, `EVENT` → `tool`, and `SPAN` → `workflow`. |
| `OPERATION_NAME` | `String` | Operation type derived from the API surface, such as `chat`, `embeddings`, or `image_generation`. |
| `ATTRIBUTES` | `Nullable(String)` | OpenTelemetry-style attributes for compatibility, serialized as JSON. |
| `INPUT` | `Nullable(String)` | Input data, such as request messages, serialized as JSON. |
| `OUTPUT` | `Nullable(String)` | Output data, such as response messages, serialized as JSON. |
| `METADATA` | `Nullable(String)` | Combined custom, request, guardrail, and provider-attempt metadata as JSON. |
| `TAGS` | `Array(Nullable(String))` | Trace tags array. |
| `MODEL_PARAMETERS` | `Nullable(String)` | Model parameters, such as temperature, serialized as JSON. |
| `RESOURCE_ATTRIBUTES` | `Nullable(String)` | Resource attributes, including `service.name` and the Broadcast source, serialized as JSON. |
| `SCHEMA_VERSION` | `UInt16` | Broadcast schema version; currently defaults to `2`. |

### Field ownership and custom metadata

OpenRouter populates all columns except for the following caller-controlled values:

* `TRACE_ID` can be set with `trace.trace_id`. If supplied, the same trace ID can span multiple API requests.
* `PARENT_SPAN_ID` can be set with `trace.parent_span_id`.
* `USER_ID` comes from the request `user` field.
* `SESSION_ID` comes from the request `session_id` field.
* Custom values are stored in the `METADATA` JSON column.

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

Delivery is at least once and the table is a plain `MergeTree`, so deduplicate on `(TRACE_ID, SPAN_ID)` for idempotent ingestion.

### Typed columns

The field reference above identifies commonly queried identifiers, timestamps, model information, token metrics, and cost metrics as typed columns for efficient filtering and aggregation.

### String columns for JSON

Less commonly accessed and variable-structure data is stored in the JSON string columns identified in the field reference above. Use ClickHouse's `JSONExtract*` functions to query these fields.

## Custom Metadata

Custom metadata from the `trace` field is stored in the `METADATA` column as a JSON string. You can query it using ClickHouse's `JSONExtract` functions.

### Supported Metadata Keys

| Key | ClickHouse Mapping | Description |
| - | - | - |
| `trace_id` | `TRACE_ID` column | Custom trace identifier for grouping |
| `parent_span_id` | `PARENT_SPAN_ID` column | Parent span identifier for linking to an existing trace |
| Additional `trace` keys | `METADATA` JSON | Custom values stored under their original keys |
| Request `metadata.<k>` | `METADATA` JSON key `metadata_<k>` | Request metadata stored with the `metadata_` prefix |

### Example

```json lines theme={null}
{
  "model": "openai/gpt-4o",
  "messages": [{ "role": "user", "content": "Analyze these metrics..." }],
  "user": "user_12345",
  "session_id": "session_abc",
  "trace": {
    "trace_name": "Metrics Analysis Pipeline",
    "generation_name": "Analyze Trends",
    "team": "data-engineering",
    "pipeline_version": "2.0",
    "data_source": "clickhouse_metrics"
  }
}
```

### Querying Custom Metadata

Use ClickHouse's JSON functions to query your custom metadata:

```sql lines theme={null}
SELECT
  TRACE_ID,
  JSONExtractString(METADATA, 'team') as team,
  JSONExtractString(METADATA, 'pipeline_version') as pipeline_version,
  JSONExtractString(METADATA, 'data_source') as data_source,
  TOTAL_COST,
  TOTAL_TOKENS
FROM OPENROUTER_TRACES
WHERE JSONHas(METADATA, 'team')
  AND SPAN_TYPE = 'GENERATION'
ORDER BY TIMESTAMP DESC;
```

### Additional Context

* The `user` field maps to the `USER_ID` typed column
* The `session_id` field maps to the `SESSION_ID` typed column
* Additional custom keys from `trace` are stored in the `METADATA` JSON string column
* `trace_name` and `generation_name` affect internal names but have no dedicated table columns
* `trace.span_name` is reserved and currently ignored
* For high-performance filtering on metadata fields, consider creating materialized columns with `ALTER TABLE ... ADD COLUMN`

## Additional resources

* [ClickHouse HTTP Interface Documentation](https://clickhouse.com/docs/en/interfaces/http)
* [ClickHouse SQL Reference](https://clickhouse.com/docs/en/sql-reference)
* [ClickHouse Cloud](https://clickhouse.com/cloud)

## Privacy Mode

When [Privacy Mode](../broadcast.md#privacy-mode) is enabled for this destination, prompt and completion content and provider error text are excluded from traces. All other trace data — token usage, costs, timing, model information, and custom metadata — is still sent normally. See [Privacy Mode](../broadcast.md#privacy-mode) for details.
