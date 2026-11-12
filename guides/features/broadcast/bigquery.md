> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Google BigQuery

> Send traces to Google BigQuery

[Google BigQuery](https://cloud.google.com/bigquery) is a serverless cloud data warehouse. OpenRouter can stream traces directly into a BigQuery table for custom analytics, long-term storage, and business intelligence. Each request becomes one row, so you can sum tokens and costs without filtering by observation type. See [rows and aggregation](#rows-and-aggregation) for details.

## Step 1: Choose a project and enable the BigQuery API

1. Open the [Google Cloud Console](https://console.cloud.google.com/) and create or select a project.
2. Copy the project ID (not the project name). It is the lowercase identifier shown in **IAM & Admin > Settings**.
3. In **APIs & Services > Library**, search for **BigQuery API** and click **Enable**.

## Step 2: Create the dataset

1. Open **BigQuery > Explorer**, select the project, and choose **Create dataset**.
2. Choose a dataset ID, such as `openrouter`.
3. Choose the dataset location carefully. A dataset's region cannot be changed after creation, so pick a location allowed by your data-residency requirements.

![BigQuery Datasets](https://mintcdn.com/openrouter-d02e98a0/dix9mCYX39AwXdtx/assets/guides/features/broadcast/bigquery/bigquery-datasets.png?fit=max\&auto=format\&n=dix9mCYX39AwXdtx\&q=85\&s=2329f9f455cf028c5e1b3c698ad28f3b)

## Step 3: Create the traces table

Create the `openrouter_traces` table in your dataset. You can find the exact SQL in the OpenRouter dashboard when configuring the destination — click **View Setup Instructions**. Replace `my-gcp-project` in the DDL with your project ID (and the dataset or table IDs if you chose different ones), then run it in the BigQuery SQL workspace:

![BigQuery Table Setup](https://mintcdn.com/openrouter-d02e98a0/dix9mCYX39AwXdtx/assets/guides/features/broadcast/bigquery/bigquery-setup-instructions.png?fit=max\&auto=format\&n=dix9mCYX39AwXdtx\&q=85\&s=cd9c13d47e7a97af61d051fd9029ca56)

Once created, the table appears in your dataset:

![BigQuery Dataset Tables](https://mintcdn.com/openrouter-d02e98a0/dix9mCYX39AwXdtx/assets/guides/features/broadcast/bigquery/bigquery-dataset-tables.png?fit=max\&auto=format\&n=dix9mCYX39AwXdtx\&q=85\&s=f4c5fcbabc160dd13bd6fd9caa1409dc)

## Step 4: Create a service account

1. Open **IAM & Admin > Service Accounts** in the project and click **Create service account** (e.g., `openrouter-broadcast`).
2. Grant it the **BigQuery Data Editor** role on the trace dataset (not at the organization or project level): open the dataset's menu in BigQuery, choose **Share > Permissions**, add the service account email, and select **BigQuery Data Editor**. Do not grant BigQuery Job User — this destination uses streaming inserts and does not create query jobs.
3. Open the service account's **Keys** tab, choose **Add key > Create new key**, select **JSON**, and download the key.

Keep the downloaded key private. It contains a private signing key and should not be committed to source control.

## Step 5: Enable Broadcast in OpenRouter

Go to [Settings > Observability](https://openrouter.ai/settings/observability) and toggle **Enable Broadcast**.

![Enable Broadcast](https://mintcdn.com/openrouter-d02e98a0/PSwwwiCqAD_BNeni/assets/guides/features/broadcast/arize/broadcast-enable.png?fit=max\&auto=format\&n=PSwwwiCqAD_BNeni\&q=85\&s=a48ecd5df85b4e6f3982c8402671f631)

## Step 6: Configure BigQuery

Click the edit icon next to **Google BigQuery** and enter:

![BigQuery Configuration](https://mintcdn.com/openrouter-d02e98a0/dix9mCYX39AwXdtx/assets/guides/features/broadcast/bigquery/bigquery-config.png?fit=max\&auto=format\&n=dix9mCYX39AwXdtx\&q=85\&s=97fe4f247e43674b5f0559a9215c0732)

* **Google Cloud project ID**: The project ID containing the dataset.
* **Service-account key JSON**: The complete contents of the downloaded JSON key file.
* **BigQuery dataset**: The dataset ID created above (default: `openrouter`).
* **BigQuery table**: The table ID created above (default: `openrouter_traces`).

## Step 7: Test and save

Click **Test Connection** to verify the setup. The connection test reads the table's metadata to verify the project, dataset, table, and credentials, then checks that the credentials hold the row-insert permission, so read-only access fails the test rather than failing on every later trace. The configuration only saves if the test passes.

## Step 8: Send a test trace

Click **Send Trace**, or make an API request through OpenRouter, and query your BigQuery table to verify the trace was received:

```sql lines theme={null}
SELECT
  trace_id,
  span_id,
  timestamp,
  model,
  status,
  total_tokens,
  total_cost
FROM `my-gcp-project.openrouter.openrouter_traces`
ORDER BY timestamp DESC
LIMIT 20;
```

![BigQuery Table Preview](https://mintcdn.com/openrouter-d02e98a0/dix9mCYX39AwXdtx/assets/guides/features/broadcast/bigquery/bigquery-table-preview.png?fit=max\&auto=format\&n=dix9mCYX39AwXdtx\&q=85\&s=3b0c86822f67a2109efb3487233366fc)

## Example queries

### Cost analysis by model

```sql lines theme={null}
SELECT
  DATE(timestamp) as day,
  model,
  SUM(total_cost) as total_cost,
  SUM(total_tokens) as total_tokens,
  COUNT(*) as request_count
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE timestamp >= TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 30 DAY)
  AND status = 'ok'
GROUP BY day, model
ORDER BY day DESC, total_cost DESC;
```

### User activity analysis

```sql lines theme={null}
SELECT
  user_id,
  COUNT(DISTINCT trace_id) as trace_count,
  COUNT(DISTINCT session_id) as session_count,
  SUM(total_tokens) as total_tokens,
  SUM(total_cost) as total_cost,
  AVG(duration_ms) as avg_duration_ms
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE timestamp >= TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 7 DAY)
GROUP BY user_id
ORDER BY total_cost DESC;
```

### Error analysis

```sql lines theme={null}
SELECT
  trace_id,
  timestamp,
  model,
  level,
  finish_reason,
  metadata,
  input,
  output
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE status = 'error'
  AND timestamp >= TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 1 HOUR)
ORDER BY timestamp DESC;
```

### Provider performance comparison

```sql lines theme={null}
SELECT
  provider_name,
  model,
  AVG(duration_ms) as avg_duration_ms,
  APPROX_QUANTILES(duration_ms, 100)[OFFSET(50)] as p50_duration_ms,
  APPROX_QUANTILES(duration_ms, 100)[OFFSET(95)] as p95_duration_ms,
  COUNT(*) as request_count
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE timestamp >= TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 7 DAY)
  AND status = 'ok'
GROUP BY provider_name, model
HAVING request_count >= 10
ORDER BY avg_duration_ms;
```

### Usage by API key

```sql lines theme={null}
SELECT
  api_key_name,
  COUNT(DISTINCT trace_id) as trace_count,
  SUM(total_cost) as total_cost,
  SUM(prompt_tokens) as prompt_tokens,
  SUM(completion_tokens) as completion_tokens
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE timestamp >= TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 30 DAY)
GROUP BY api_key_name
ORDER BY total_cost DESC;
```

### Accessing JSON columns

The `attributes`, `input`, `output`, `metadata`, `model_parameters`, and `resource_attributes` columns are `JSON` typed. Use BigQuery's JSON functions to query nested fields:

```sql lines theme={null}
SELECT
  trace_id,
  JSON_VALUE(metadata, '$.custom_field') as custom_value,
  JSON_VALUE(attributes, '$."gen_ai.request.model"') as requested_model
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE JSON_VALUE(metadata, '$.custom_field') IS NOT NULL;
```

To parse input messages:

```sql lines theme={null}
SELECT
  trace_id,
  JSON_VALUE(input, '$.messages[0].role') as first_message_role,
  JSON_VALUE(input, '$.messages[0].content') as first_message_content
FROM `my-gcp-project.openrouter.openrouter_traces`
LIMIT 10;
```

## Schema design

The dashboard-generated `CREATE TABLE` statement is the source of truth for setup. The field reference below describes the current schema without duplicating the generated SQL.

### Field reference

| Column | BigQuery type | Meaning |
| - | - | - |
| `trace_id` | `STRING NOT NULL` | Trace identifier shared by all observations in a trace. |
| `span_id` | `STRING NOT NULL` | Unique identifier for this observation. |
| `parent_span_id` | `STRING` | Parent observation identifier, or `NULL` for an unparented observation. |
| `user_id` | `STRING` | End-user identifier from the request. |
| `session_id` | `STRING` | Session identifier used to group related requests. |
| `organization_id` | `STRING` | Organization that owns the trace. |
| `entity_id` | `STRING NOT NULL` | Entity that owns the trace. |
| `api_key_name` | `STRING` | User-defined name of the API key used for the request. |
| `timestamp` | `TIMESTAMP NOT NULL` | Trace creation timestamp. |
| `start_time` | `TIMESTAMP NOT NULL` | Observation start time. |
| `end_time` | `TIMESTAMP` | Observation end time, or `NULL` when unavailable. |
| `duration_ms` | `FLOAT64` | Observation duration in milliseconds. |
| `model` | `STRING` | Model name used for the observation. |
| `provider_name` | `STRING` | Provider name for the observation. |
| `provider_slug` | `STRING` | Provider slug identifier. |
| `status` | `STRING NOT NULL` | `ok` or `error`; `error` is emitted only when `level` is `ERROR`. |
| `level` | `STRING NOT NULL` | Observation level: `DEBUG`, `INFO`, `DEFAULT`, `WARNING`, or `ERROR`. |
| `finish_reason` | `STRING` | Completion finish reason, such as `stop` or `length`; not an enum. |
| `prompt_tokens` | `INT64 NOT NULL` | Input/prompt token count. |
| `completion_tokens` | `INT64 NOT NULL` | Output/completion token count. |
| `total_tokens` | `INT64 NOT NULL` | Total token count. |
| `cached_tokens` | `INT64 NOT NULL` | Cached prompt token count. |
| `cache_write_tokens` | `INT64` | Prompt tokens written to the provider prompt cache. Added in schema version 2; tables created from version 1 don't have this column. `NULL` when the provider did not report them, or when the destination's **Include cache\_write\_tokens** setting is off. The setting is off by default; turn it on after the table has this column. |
| `reasoning_tokens` | `INT64 NOT NULL` | Reasoning/thinking token count. |
| `input_cost` | `FLOAT64 NOT NULL` | Input cost in USD. |
| `output_cost` | `FLOAT64 NOT NULL` | Output cost in USD. |
| `total_cost` | `FLOAT64 NOT NULL` | Total cost in USD. |
| `input_unit_price` | `FLOAT64` | Price per input token in USD. |
| `output_unit_price` | `FLOAT64` | Price per output token in USD. |
| `span_type` | `STRING NOT NULL` | Observation type; `GENERATION` for every row except the rare trace that has no generation. |
| `span_kind` | `STRING NOT NULL` | Derived from `span_type`: `GENERATION` → `llm`, `EVENT` → `tool`, and `SPAN` → `workflow`. |
| `operation_name` | `STRING NOT NULL` | Operation type derived from the API surface, such as `chat`, `embeddings`, or `image_generation`. |
| `attributes` | `JSON` | OpenTelemetry-style attributes for compatibility. |
| `input` | `JSON` | Input data, such as request messages. |
| `output` | `JSON` | Output data, such as response messages. |
| `metadata` | `JSON` | Combined custom, request, guardrail, and provider-attempt metadata, including per-attempt detail in `provider_responses`. |
| `tags` | `ARRAY<STRING>` | Trace tags. |
| `model_parameters` | `JSON` | Model parameters, such as temperature. |
| `resource_attributes` | `JSON` | Resource attributes, including `service.name` and the Broadcast source. |
| `schema_version` | `INT64` | Broadcast schema version; currently defaults to `2`. |

### Field ownership and custom metadata

OpenRouter populates all columns except for the following caller-controlled values:

* `trace_id` can be set with `trace.trace_id`. If supplied, the same trace ID can span multiple API requests.
* `parent_span_id` can be set with `trace.parent_span_id`.
* `user_id` comes from the request `user` field.
* `session_id` comes from the request `session_id` field.
* Custom values are stored in the `metadata` `JSON` column.

Additional keys in `trace` are merged into `metadata` using their original keys. Top-level request `metadata.<k>` values are also placed in `metadata`, under the key `metadata_<k>`. There is no separate database column for each custom key. `trace_name` and `generation_name` affect internal trace and observation names but have no dedicated table columns. `trace.span_name` is accepted as a reserved request field but is currently ignored.

### Rows and aggregation

Unlike the Snowflake and ClickHouse destinations, BigQuery receives one row per generation, not one row per observation. Each API request produces a single `GENERATION` row:

* `span_id` is the generation ID.
* `parent_span_id` is `NULL` unless the request set `trace.parent_span_id`.
* Per-attempt provider detail is in `metadata.provider_responses`, and phase timings are in the `openrouter_*` fields of `attributes`.

The moderation, provider-attempt, and post-generation spans aren't written as separate rows, so you can sum tokens and costs without filtering on `span_type`. If you set `trace.trace_id` across requests, several rows share one `trace_id`, so count requests with `span_id` rather than `trace_id`.

BigQuery deduplicates streaming inserts on `(trace_id, span_id)` on a best-effort basis only, so a retried insert can still land a duplicate row. Deduplicate on `(trace_id, span_id)` to remove duplicates. Rows that BigQuery permanently rejects, or that still fail after transient retries, are dropped rather than redelivered, so deduplication can't recover missing rows.

### Typed columns

The field reference above identifies commonly queried identifiers, timestamps, model information, token metrics, and cost metrics as typed columns for efficient filtering and aggregation.

### JSON columns

Less commonly accessed and variable-structure data is stored in the `JSON` columns identified in the field reference above. The `tags` column is a repeated `STRING` column (`ARRAY<STRING>`). Use BigQuery's `JSON_VALUE` and `JSON_QUERY` functions to query the JSON fields.

## Custom Metadata

Custom metadata from the `trace` field is stored in the `metadata` JSON column. You can query it using BigQuery's JSON functions.

### Supported Metadata Keys

| Key | BigQuery Mapping | Description |
| - | - | - |
| `trace_id` | `trace_id` column | Custom trace identifier for grouping |
| `parent_span_id` | `parent_span_id` column | Parent span identifier for linking to an existing trace |
| Additional `trace` keys | `metadata` JSON | Custom values stored under their original keys |
| Request `metadata.<k>` | `metadata.metadata_<k>` | Request metadata stored with the `metadata_` prefix |

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

```sql lines theme={null}
SELECT
  trace_id,
  JSON_VALUE(metadata, '$.department') as department,
  JSON_VALUE(metadata, '$.quarter') as quarter,
  JSON_VALUE(metadata, '$.model_version') as model_version,
  total_cost,
  total_tokens
FROM `my-gcp-project.openrouter.openrouter_traces`
WHERE JSON_VALUE(metadata, '$.department') IS NOT NULL
ORDER BY timestamp DESC;
```

### Additional Context

* The `user` field maps to the `user_id` typed column
* The `session_id` field maps to the `session_id` typed column
* Additional custom keys from `trace` are stored in the `metadata` JSON column for flexible querying
* `trace_name` and `generation_name` affect internal names but have no dedicated table columns
* `trace.span_name` is reserved and currently ignored

## Troubleshooting

* **Project not found or permission denied**: Confirm that the configured project ID is the project containing the dataset and that the service account belongs to the expected project.
* **Table not found**: Confirm the dataset and table IDs and that the table was created in the configured dataset location.
* **403 permission denied**: Grant the service account **BigQuery Data Editor** on the dataset. Project-level access may be restricted by organization policy, so verify the dataset permission directly.
* **400 invalid or schema mismatch**: Compare the table schema with the DDL from the setup instructions. In particular, timestamps must be `TIMESTAMP`, nested trace fields must be `JSON`, and `tags` must be `ARRAY<STRING>`.

## Additional resources

* [BigQuery Documentation](https://cloud.google.com/bigquery/docs)
* [Streaming Data into BigQuery](https://cloud.google.com/bigquery/docs/streaming-data-into-bigquery)
* [JSON Functions in GoogleSQL](https://cloud.google.com/bigquery/docs/reference/standard-sql/json_functions)

## Privacy Mode

When [Privacy Mode](../broadcast.md#privacy-mode) is enabled for this destination, prompt and completion content and provider error text are excluded from traces. All other trace data — token usage, costs, timing, model information, and custom metadata — is still sent normally. See [Privacy Mode](../broadcast.md#privacy-mode) for details.
