> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# API Changelog

> Changes to the OpenRouter API, generated from the OpenAPI specification on every release.

Entries on this page are generated automatically from [OpenAPI specification](api_reference/overview.md) diffs when releases ship. Breaking changes are reviewed by a human before publication. See [API Versioning](api_reference/versioning.md) for what counts as a breaking change and how deprecations are announced. Endpoint paths are shown relative to the API base URL (`https://openrouter.ai/api/v1`).

**November 12, 2026**

## Modified endpoints

* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): request schema updated; description updated; response schema updated
* [`POST /workspaces/{id}/members/add`](api/api-reference/workspaces/bulk-add-members-to-a-workspace.md): description updated
* [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment): description updated; response schema updated
* [`POST /responses`](api/api-reference/responses/create-a-response.md): description updated; response schema updated

## New schemas

* `CreditPurchaseUnavailableResponse`
  * Used by [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment)
* `ResponsesBadRequestResponse`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesBadRequestResponseErrorData`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ContentFilterReadEntry`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)

## Modified schemas

* `BulkAddWorkspaceMembersRequest`: description updated
  * Used by [`POST /workspaces/{id}/members/add`](api/api-reference/workspaces/bulk-add-members-to-a-workspace.md)
* `BulkAddWorkspaceMembersResponse`: description updated
  * Used by [`POST /workspaces/{id}/members/add`](api/api-reference/workspaces/bulk-add-members-to-a-workspace.md)
* `CreateWorkspaceRequest`: description updated
  * Used by [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `UpdateWorkspaceRequest`: description updated
  * Used by [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
* `ObservabilityOtelCollectorDestination`: new property `config.metricsEndpoint`; new property `config.shouldSendMetrics`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `OutputToolSearchServerToolItem`: new property `catalog_index_note`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponseIncludesEnum`: enum property\_added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `Guardrail`: example modified; \$ref modified

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `OutputWebFetchServerToolItem`: new property `retrieved_at`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**November 11, 2026**

## Breaking changes

* `ExtractionsRequest`: required `state` property removedNo action needed
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ChangeGuardrailPolicyAssignmentRequest`: required `workspace_id` property removedNo action needed
  * Used by [`PUT /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/change-an-api-key-policy-assignment.md), [`PUT /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/change-a-member-policy-assignment.md)
* `CreateBudgetGuardrailPolicyRequest`: required `workspace_id` property removedNo action needed
  * Used by [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md)
* `CreateModelAvailabilityGuardrailPolicyRequest`: required `workspace_id` property removedNo action needed
  * Used by [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md)
* `CreateModerationGuardrailPolicyRequest`: required `workspace_id` property removedNo action needed
  * Used by [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md)
* `UpdateBudgetGuardrailPolicyRequest`: required `workspace_id` property removedNo action needed
  * Used by [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `UpdateModelAvailabilityGuardrailPolicyRequest`: required `workspace_id` property removedNo action needed
  * Used by [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `UpdateModerationGuardrailPolicyRequest`: required `workspace_id` property removedNo action needed
  * Used by [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md)
* [`GET /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/get-an-api-key-policy-assignment.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/get-a-member-policy-assignment.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/budget`](api/api-reference/guardrail-policies/list-budget-policies.md): required changed from `true` to `false`No action needed
* [`DELETE /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/delete-a-budget-policy.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/get-a-budget-policy.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/list-model-availability-policies.md): required changed from `true` to `false`No action needed
* [`DELETE /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/delete-a-model-availability-policy.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/get-a-model-availability-policy.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/moderation`](api/api-reference/guardrail-policies/list-moderation-policies.md): required changed from `true` to `false`No action needed
* [`DELETE /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/delete-a-moderation-policy.md): required changed from `true` to `false`No action needed
* [`GET /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/get-a-moderation-policy.md): required changed from `true` to `false`No action needed
* `VideoGenerationRequest.duration`: minimum changed from `1` to `-1`No action needed
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

## Modified endpoints

* [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md): description updated
* [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md): description updated
* [`GET /guardrails/assignments/keys`](api/api-reference/guardrails/list-all-key-assignments.md): description updated
* [`GET /guardrails/assignments/members`](api/api-reference/guardrails/list-all-member-assignments.md): description updated
* [`DELETE /guardrails/{id}`](api/api-reference/guardrails/delete-a-guardrail.md): description updated
* [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md): description updated
* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): description updated
* [`GET /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/list-key-assignments-for-a-guardrail.md): description updated
* [`POST /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/bulk-assign-keys-to-a-guardrail.md): description updated
* [`POST /guardrails/{id}/assignments/keys/remove`](api/api-reference/guardrails/bulk-unassign-keys-from-a-guardrail.md): description updated
* [`GET /guardrails/{id}/assignments/members`](api/api-reference/guardrails/list-member-assignments-for-a-guardrail.md): description updated
* [`POST /guardrails/{id}/assignments/members`](api/api-reference/guardrails/bulk-assign-members-to-a-guardrail.md): description updated
* [`POST /guardrails/{id}/assignments/members/remove`](api/api-reference/guardrails/bulk-unassign-members-from-a-guardrail.md): description updated
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): description updated
* [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md): description updated
* [`DELETE /observability/destinations/{id}`](api/api-reference/observability/delete-an-observability-destination.md): description updated
* [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md): description updated
* [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md): description updated
* [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md): description updated
* [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment): description updated; response schema updated
* [`GET /guardrails/assignments/keys`](api/api-reference/guardrails/list-all-key-assignments.md): new parameter `workspace_id`
* [`GET /guardrails/assignments/members`](api/api-reference/guardrails/list-all-member-assignments.md): new parameter `workspace_id`
* [`GET /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/get-an-api-key-policy-assignment.md): description updated
* [`GET /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/get-a-member-policy-assignment.md): description updated
* [`GET /guardrails/policies/budget`](api/api-reference/guardrail-policies/list-budget-policies.md): description updated
* [`DELETE /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/delete-a-budget-policy.md): description updated
* [`GET /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/get-a-budget-policy.md): description updated
* [`GET /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/list-model-availability-policies.md): description updated
* [`DELETE /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/delete-a-model-availability-policy.md): description updated
* [`GET /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/get-a-model-availability-policy.md): description updated
* [`GET /guardrails/policies/moderation`](api/api-reference/guardrail-policies/list-moderation-policies.md): description updated
* [`DELETE /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/delete-a-moderation-policy.md): description updated
* [`GET /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/get-a-moderation-policy.md): description updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md): description updated
* [`POST /batches`](api/api-reference/batch/create-a-batch.md): description updated

## New response codes

* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): now returns `401`
* [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md): now returns `401`

## Modified schemas

* `CreateGuardrailRequest`: description updated
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `CreateObservabilityDestinationRequest`: description updated
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ExtractionAsset`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDateAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDateField`: new property `unit`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDatetimeAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDatetimeField`: new property `unit`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDurationAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDurationField`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionEstimateField`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionForecastField`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionListAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionListField`: new property `integer`; new property `unit`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionNumberAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionNumberField`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTextAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTextField`: new property `unit`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTimeAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTimeField`: new property `unit`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionsRequest`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `UpdateObservabilityDestinationRequest`: description updated
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
* `ChangeGuardrailPolicyAssignmentRequest`: description updated
  * Used by [`PUT /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/change-an-api-key-policy-assignment.md), [`PUT /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/change-a-member-policy-assignment.md)
* `CreateBudgetGuardrailPolicyRequest`: description updated
  * Used by [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md)
* `CreateModelAvailabilityGuardrailPolicyRequest`: description updated
  * Used by [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md)
* `CreateModerationGuardrailPolicyRequest`: description updated
  * Used by [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md)
* `UpdateBudgetGuardrailPolicyRequest`: description updated
  * Used by [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `UpdateModelAvailabilityGuardrailPolicyRequest`: description updated
  * Used by [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `UpdateModerationGuardrailPolicyRequest`: description updated
  * Used by [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **18 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderOptions`: new property `speechify`

  **15 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ChatRequest`:
  * new property `reasoning.context`
  * new property `reasoning.enabled`
  * new property `reasoning.exclude`
  * new property `reasoning.mode`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `BYOKKey`: description updated

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: description updated
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `UpdateBYOKKeyRequest`: description updated
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `VideoGenerationRequest`: description updated
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `VideoModel`: description updated
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `SpeechInput`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `BatchObject`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchSubmitBody`: enum property\_added
  * Used by [`POST /batches`](api/api-reference/batch/create-a-batch.md)

**November 10, 2026**

## Breaking changes

* [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment): content `application/json` object removedNo action needed
* `ExtractionListAnswer.spans`: type changed from `array` to `array | null`Action required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: handle a `null` entry in `spans`.** `spans` still has one entry per item of `value`, in the same order, but an entry is now `null` when that item has no offsets in the state text, for example a list item read from an image or a document. Before this release such a response returned 502; it now returns 200. Check each entry for `null` before you read its `[start, end)` offsets. Responses whose list items all come from the state text are unchanged.

## New endpoints

* [`POST /presets/{slug}/restore`](api/api-reference/presets/restore-a-preset.md): Restore a preset
* [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment): Buy credits with a machine payment
* [`GET /credits/purchases/{id}`](https://openrouter.ai/docs/api/api-reference/credits/get-a-credit-purchase): Get a credit purchase
* [`GET /credits/purchases/SKILL.md`](https://openrouter.ai/docs/api/api-reference/credits/agent-skill-for-buying-openrouter-credits): Agent skill for buying OpenRouter credits
* [`GET /credits/purchases/setup`](https://openrouter.ai/docs/api/api-reference/credits/agent-setup-guide-for-buying-credits-with-a-machine-payment): Agent setup guide for buying credits with a machine payment

## Modified endpoints

* [`GET /presets`](api/api-reference/presets/list-presets.md): new parameter `workspace_id`
* [`GET /presets/{slug}`](api/api-reference/presets/get-a-preset.md): new parameter `workspace_id`
* [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md): description updated
* [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md): description updated
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): description updated
* [`GET /presets/{slug}/versions`](api/api-reference/presets/list-versions-of-a-preset.md): new parameter `workspace_id`
* [`GET /presets/{slug}/versions/{version}`](api/api-reference/presets/get-a-specific-version-of-a-preset.md): new parameter `workspace_id`
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): description updated
* [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md): description updated
* [`DELETE /byok/{id}`](api/api-reference/byok/delete-a-byok-provider-credential.md): description updated
* [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md): description updated
* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): description updated
* [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment): response schema updated; description updated
* [`GET /analytics/meta`](api/api-reference/analytics/get-available-analytics-metrics-and-dimensions.md): description updated
* [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md): description updated

## New response codes

* [`GET /presets`](api/api-reference/presets/list-presets.md): now returns `404`
* [`POST /auth/keys/code`](api/api-reference/oauth/create-authorization-code.md): now returns `503`

## New schemas

* `CreateCreditPurchaseRequest`
  * Used by [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment)
* `CreditPurchase`
  * Used by [`GET /credits/purchases/{id}`](https://openrouter.ai/docs/api/api-reference/credits/get-a-credit-purchase), [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment)
* `CreditPurchaseResponse`
  * Used by [`GET /credits/purchases/{id}`](https://openrouter.ai/docs/api/api-reference/credits/get-a-credit-purchase), [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment)
* `CreditPurchasePaymentRequired`
  * Used by [`POST /credits/purchases`](https://openrouter.ai/docs/api/api-reference/credits/buy-credits-with-a-machine-payment)

## Modified schemas

* `DeferredBm25Search`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredRegexSearch`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ImageGenerationRequest`: enum property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `ReasoningFormat`: enum property\_added

  **6 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKKey`: description updated

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: description updated
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `UpdateBYOKKeyRequest`: description updated
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `ExtractionListAnswer`: description updated
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)

**November 9, 2026**

## Breaking changes

* `DeferredToolsControl.scope`: enum `client` property removedAction required

  * **Migration: remove `"scope": "client"` from `deferred_tools`.** `deferred_tools.scope` now accepts only `"all"` (the default when omitted) or `"mcp"`; requests or saved presets sending `"scope": "client"` now return 400. Omit `scope` or set `"scope": "all"` to defer across all eligible tools, or set `"scope": "mcp"` to defer MCP tools only.

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `DeferredBm25Search`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredRegexSearch`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsControl`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenResponsesErrorField`: enum property\_added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesErrorField`: enum property\_added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**November 8, 2026**

## Modified schemas

* `DeferredBm25Search`: new property `spread`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsControl`: description updated; new property `announce_catalog_changes`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputToolSearchServerToolItem`: new property `catalog_changes`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredBm25Search`: new property `miss_sources`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredRegexSearch`: new property `miss_sources`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsControl`: new property `min_deferred_tools`; description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredBm25Search`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredRegexSearch`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**November 7, 2026**

## Modified schemas

* `ImageGenerationServerToolConfig`: example modified; description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ImageGenerationServerTool_OpenRouter`: example modified

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterServerTool`: description updated

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsControl`: new property `cascade_mode`; description updated; enum property\_added

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FileSearchServerTool`: description updated

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredBm25Search`: new property `siblings`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredRegexSearch`: new property `siblings`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsControl`: new property `hint`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputToolSearchServerToolItem`: new property `sources`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**November 6, 2026**

## New endpoints

* [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md): List workspace-wide policies
* [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md): Create a workspace-wide policy
* [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md): Update a workspace-wide policy
* [`DELETE /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/delete-a-workspace-wide-policy.md): Delete a workspace-wide policy
* [`GET /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/get-an-api-key-policy-assignment.md): Get an API key policy assignment
* [`PUT /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/change-an-api-key-policy-assignment.md): Change an API key policy assignment
* [`GET /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/get-a-member-policy-assignment.md): Get a member policy assignment
* [`PUT /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/change-a-member-policy-assignment.md): Change a member policy assignment
* [`GET /guardrails/policies/budget`](api/api-reference/guardrail-policies/list-budget-policies.md): List budget policies
* [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md): Create a budget policy
* [`GET /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/get-a-budget-policy.md): Get a budget policy
* [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md): Update a budget policy
* [`DELETE /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/delete-a-budget-policy.md): Delete a budget policy
* [`GET /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/list-model-availability-policies.md): List model availability policies
* [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md): Create a model availability policy
* [`GET /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/get-a-model-availability-policy.md): Get a model availability policy
* [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md): Update a model availability policy
* [`DELETE /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/delete-a-model-availability-policy.md): Delete a model availability policy
* [`GET /guardrails/policies/moderation`](api/api-reference/guardrail-policies/list-moderation-policies.md): List moderation policies
* [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md): Create a moderation policy
* [`GET /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/get-a-moderation-policy.md): Get a moderation policy
* [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md): Update a moderation policy
* [`DELETE /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/delete-a-moderation-policy.md): Delete a moderation policy

## Modified endpoints

* [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md): description updated
* [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md): description updated; new parameter `workspace_id`
* [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md): description updated; new parameter `workspace_id`
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): description updated; new parameter `workspace_id`

## New schemas

* `AccountGuardrailPolicy`
  * Used by [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md), [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `AccountGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `AccountGuardrailPolicyResponse`
  * Used by [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `BudgetAccountGuardrailPolicy`
  * Used by [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md), [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `BudgetAccountGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `BudgetGuardrailPolicy`
  * Used by [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md), [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `BudgetGuardrailPolicyDetail`
  * Used by [`GET /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/get-a-budget-policy.md)
* `BudgetGuardrailPolicyDetailResponse`
  * Used by [`GET /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/get-a-budget-policy.md)
* `BudgetGuardrailPolicyResponse`
  * Used by [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md), [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `BudgetGuardrailPolicySummary`
  * Used by [`GET /guardrails/policies/budget`](api/api-reference/guardrail-policies/list-budget-policies.md)
* `ChangeGuardrailPolicyAssignmentRequest`
  * Used by [`PUT /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/change-an-api-key-policy-assignment.md), [`PUT /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/change-a-member-policy-assignment.md)
* `ChangeGuardrailPolicyAssignmentResponse`
  * Used by [`PUT /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/change-an-api-key-policy-assignment.md), [`PUT /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/change-a-member-policy-assignment.md)
* `CreateBudgetGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md)
* `CreateModelAvailabilityGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md)
* `CreateModerationGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md)
* `DeleteGuardrailPolicyResponse`

  **4 endpoints using this schema**

  * [`DELETE /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/delete-a-workspace-wide-policy.md)
  * [`DELETE /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/delete-a-budget-policy.md)
  * [`DELETE /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/delete-a-model-availability-policy.md)
  * [`DELETE /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/delete-a-moderation-policy.md)
* `GuardrailBudgetPolicyAuthoringConfig`

  **4 endpoints using this schema**

  * [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md)
  * [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md)
  * [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
  * [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `GuardrailBudgetPolicyConfig`

  **7 endpoints using this schema**

  * [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md)
  * [`GET /guardrails/policies/budget`](api/api-reference/guardrail-policies/list-budget-policies.md)
  * [`GET /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/get-a-budget-policy.md)
  * [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md)
  * [`POST /guardrails/policies/budget`](api/api-reference/guardrail-policies/create-a-budget-policy.md)
  * [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
  * [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `GuardrailModelAvailabilityPolicyAuthoringConfig`

  **4 endpoints using this schema**

  * [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md)
  * [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md)
  * [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
  * [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `GuardrailModelAvailabilityPolicyConfig`

  **7 endpoints using this schema**

  * [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md)
  * [`GET /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/list-model-availability-policies.md)
  * [`GET /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/get-a-model-availability-policy.md)
  * [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md)
  * [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md)
  * [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
  * [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `GuardrailModerationPolicyConfig`

  **7 endpoints using this schema**

  * [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md)
  * [`GET /guardrails/policies/moderation`](api/api-reference/guardrail-policies/list-moderation-policies.md)
  * [`GET /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/get-a-moderation-policy.md)
  * [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md)
  * [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md)
  * [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
  * [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md)
* `GuardrailPolicyAssignmentResponse`
  * Used by [`GET /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/get-an-api-key-policy-assignment.md), [`GET /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/get-a-member-policy-assignment.md)
* `GuardrailPolicyAssignmentState`

  **4 endpoints using this schema**

  * [`GET /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/get-an-api-key-policy-assignment.md)
  * [`GET /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/get-a-member-policy-assignment.md)
  * [`PUT /guardrails/policies/assignments/api-keys/{hash}`](api/api-reference/guardrail-policies/change-an-api-key-policy-assignment.md)
  * [`PUT /guardrails/policies/assignments/members/{member_id}`](api/api-reference/guardrail-policies/change-a-member-policy-assignment.md)
* `ListAccountGuardrailPoliciesResponse`
  * Used by [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md)
* `ListBudgetGuardrailPoliciesResponse`
  * Used by [`GET /guardrails/policies/budget`](api/api-reference/guardrail-policies/list-budget-policies.md)
* `ListModelAvailabilityGuardrailPoliciesResponse`
  * Used by [`GET /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/list-model-availability-policies.md)
* `ListModerationGuardrailPoliciesResponse`
  * Used by [`GET /guardrails/policies/moderation`](api/api-reference/guardrail-policies/list-moderation-policies.md)
* `ModelAvailabilityAccountGuardrailPolicy`
  * Used by [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md), [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `ModelAvailabilityAccountGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `ModelAvailabilityGuardrailPolicy`
  * Used by [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md), [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `ModelAvailabilityGuardrailPolicyDetail`
  * Used by [`GET /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/get-a-model-availability-policy.md)
* `ModelAvailabilityGuardrailPolicyDetailResponse`
  * Used by [`GET /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/get-a-model-availability-policy.md)
* `ModelAvailabilityGuardrailPolicyResponse`
  * Used by [`POST /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/create-a-model-availability-policy.md), [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `ModelAvailabilityGuardrailPolicySummary`
  * Used by [`GET /guardrails/policies/model-availability`](api/api-reference/guardrail-policies/list-model-availability-policies.md)
* `ModerationAccountGuardrailPolicy`
  * Used by [`GET /guardrails/policies/account`](api/api-reference/guardrail-policies/list-workspace-wide-policies.md), [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `ModerationAccountGuardrailPolicyRequest`
  * Used by [`POST /guardrails/policies/account`](api/api-reference/guardrail-policies/create-a-workspace-wide-policy.md), [`PUT /guardrails/policies/account/{id}`](api/api-reference/guardrail-policies/update-a-workspace-wide-policy.md)
* `ModerationGuardrailPolicy`
  * Used by [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md), [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md)
* `ModerationGuardrailPolicyDetail`
  * Used by [`GET /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/get-a-moderation-policy.md)
* `ModerationGuardrailPolicyDetailResponse`
  * Used by [`GET /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/get-a-moderation-policy.md)
* `ModerationGuardrailPolicyResponse`
  * Used by [`POST /guardrails/policies/moderation`](api/api-reference/guardrail-policies/create-a-moderation-policy.md), [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md)
* `ModerationGuardrailPolicySummary`
  * Used by [`GET /guardrails/policies/moderation`](api/api-reference/guardrail-policies/list-moderation-policies.md)
* `UpdateBudgetGuardrailPolicyRequest`
  * Used by [`PUT /guardrails/policies/budget/{id}`](api/api-reference/guardrail-policies/update-a-budget-policy.md)
* `UpdateModelAvailabilityGuardrailPolicyRequest`
  * Used by [`PUT /guardrails/policies/model-availability/{id}`](api/api-reference/guardrail-policies/update-a-model-availability-policy.md)
* `UpdateModerationGuardrailPolicyRequest`
  * Used by [`PUT /guardrails/policies/moderation/{id}`](api/api-reference/guardrail-policies/update-a-moderation-policy.md)

## Modified schemas

* `UpdatePrivateEndpointRequest`: description updated
  * Used by [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
* `DeferredToolsControl`: new property `interface`; new property `scope`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DecisionsNoulAnswer`: new property `confidence`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)

**November 5, 2026**

## Breaking changes

* spec: OutputMcpServerToolItem object removedNo action needed
* `OutputMcpServerToolItem`: schema object removedNo action needed
* `OutputItems`: openrouter:mcp `#/components/schemas/OutputMcpServerToolItem` object removedNo action needed
  * These types were never returned or used, so no migration should be necessary, other than handling exhaustive switch statements.
* spec: additionalProperties object addedNo action needed
* spec: removed enum from `connector_id` No action needed
* `DecisionsChoiceQuestion`: required `instructions` property removedNo action needed
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * `instructions` is now optional and nullable. Requests that omit it, or send `null`, are accepted instead of rejected with a 400 before routing.
* `DecisionsNoulQuestion`: required `instructions` property removedNo action needed
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * `instructions` is now optional and nullable; callers that still send it are unaffected.
* `DecisionsNoulQuestion.criteria`: required `false` property removedNo action needed
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * The `false` side is now optional and nullable, so a question can supply one side only.
* `DecisionsNoulQuestion.criteria`: required `true` property removedNo action needed
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * The `true` side is now optional and nullable, so a question can supply one side only.
* `DecisionsScoreQuestion`: required `instructions` property removedNo action needed
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * `instructions` is now optional and nullable; callers that still send it are unaffected.
* `McpServerTool`: additionalProperties `additionalProperties` object addedNo action needed

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpServerTool.connector_id`: removed enum from `connector_id` No action needed
  * `connector_id` now accepts any string instead of a fixed enum, so existing connector IDs continue to work and new provider-defined connectors are forwarded as written. Only generated SDK type names move: the closed `connector_id` enum is replaced by a plain string, so typed SDK callers pass connector IDs as string literals instead of enum members.
* [`POST /auth/keys/code`](api/api-reference/oauth/create-authorization-code.md): properties `spawn_agent` object removedNo action needed
* [`POST /auth/keys/code`](api/api-reference/oauth/create-authorization-code.md): properties `spawn_cloud` object removedNo action needed

## Modified endpoints

* [`GET /organization/members`](api/api-reference/organization/list-organization-members.md): description updated; response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): extension `x-speakeasy-pagination` added

## New schemas

* `DeferredToolsDetails`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpCallArgumentsDeltaEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpCallArgumentsDoneEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpCallCompletedEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpCallFailedEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpCallInProgressEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpListToolsCompletedEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpListToolsFailedEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpListToolsInProgressEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpServerToolParameters`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpServerTool_OpenRouter`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemMcpApprovalRequest`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemMcpCall`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemMcpListTools`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ToolChoiceMcp`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `ChatUsage`: new property `deferred_tools_details`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
* `DeferredToolsControl`: description updated; enum property\_added

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputToolSearchServerToolItem`:

  * new property `arguments`
  * new property `call_id`
  * new property `catalog_index`
  * new property `format`
  * new property `hint`
  * new property `turn_call_ids`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `PrivateEndpointCheck`: deprecated property\_added; description updated
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md), [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `RangeCapability`: format property\_added
  * Used by [`GET /images/models`](api/api-reference/images/list-image-generation-models.md), [`GET /images/models/{author}/{slug}/endpoints`](api/api-reference/images/list-endpoints-for-an-image-model.md)
* `VideoGenerationRequest`: format property\_added
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `OutputItems`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `StreamEvents`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SpeechInputReference`: example property\_added
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceAudioInput`: example property\_added
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceImageInput`: example property\_added
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `ImageGenerationRequest`:
  * new property `frame_count`
  * new property `frame_duration_ms`
  * new property `markup`
  * description updated
  * enum property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `AdditionalToolsItem`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentResponsesRejected`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `BaseResponsesResult`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CreateWorkspaceRequest`: enum property\_added
  * Used by [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `DecisionsChoiceQuestion`: new union variant added
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `DecisionsNoulQuestion`: new union variant added
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `DecisionsScoreQuestion`: new union variant added
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ImageGenerationRequest`: description updated
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `McpCallItem`: new property `approval_request_id`; new property `status`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `OpenAIResponsesToolChoice`: new union variant added

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemAddedEvent`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemDoneEvent`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderName`: enum property\_added

  **18 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderOptions`: new property `river`

  **15 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ResponsesRequest`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ToolSearchOutputItem`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `UpdateWorkspaceRequest`: enum property\_added
  * Used by [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
* `DecisionsResponse`: new property `usage.cost_details`; new property `usage.is_byok`; property `cost` updated
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ChatRequest`: new property `reasoning.max_tokens`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)

**November 4, 2026**

## Breaking changes

* `UpdatePrivateEndpointParametersRequest`: schema object removedAction required
  * **Migration: use [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) with `declared_parameters`.** The deprecated `PUT /private-endpoints/{id}/parameters` endpoint and its `UpdatePrivateEndpointParametersRequest` schema have been removed and now return 404. Send `{ "declared_parameters": [...] }` to [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) (`UpdatePrivateEndpointRequest`) instead.
* `UpdatePrivateEndpointPricingRequest`: schema object removedAction required
  * **Migration: use [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) with `pricing`.** The deprecated `PUT /private-endpoints/{id}/pricing` endpoint and its `UpdatePrivateEndpointPricingRequest` schema have been removed and now return 404. Send `{ "pricing": { ... } }` to [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) (`UpdatePrivateEndpointRequest`) instead.
* `CreatePrivateEndpointRequest`: properties `max_completion_tokens` object removedAction required
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * **Migration: move `max_completion_tokens` to `settings.max_completion_tokens`.** `POST /private-endpoints` no longer reads a top-level `max_completion_tokens` field (a top-level value is ignored). Pass `{ "settings": { "max_completion_tokens": ... } }` instead, matching [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md). Response objects continue to include `max_completion_tokens`.
* `/private-endpoints/{id}/parameters`: endpoint object removedAction required
  * **Migration: use [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) with `declared_parameters`.** The deprecated `PUT /private-endpoints/{id}/parameters` endpoint has been removed and now returns 404. Send `{ "declared_parameters": [...] }` to [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) instead.
* `/private-endpoints/{id}/pricing`: endpoint object removedAction required
  * **Migration: use [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) with `pricing`.** The deprecated `PUT /private-endpoints/{id}/pricing` endpoint has been removed and now returns 404. Send `{ "pricing": { ... } }` to [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md) instead.
* `EndpointRef`: schema object removedNo action needed
* `EndpointSummary`: schema object removedNo action needed
* `EndpointTestProfile`: schema object removedNo action needed
* `ProviderEndpointStats`: schema object removedNo action needed
* `ProviderEndpointStatsAvailable`: schema object removedNo action needed
* `ProviderEndpointStatsUnavailable`: schema object removedNo action needed
* `ProviderEndpoints`: schema object removedNo action needed
* `ProviderEndpointsResponse`: schema object removedNo action needed
* `/providers/{provider_slug}/endpoints`: endpoint object removedNo action needed

## New endpoints

* `GET /providers/{provider_slug}/endpoints`: List a provider's endpoints with provider-wide stats

## Modified endpoints

* [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md): description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md): description updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated

## New schemas

* `Extractions`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `EndpointRef`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `EndpointSummary`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `EndpointTestProfile`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `ProviderEndpointStats`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `ProviderEndpointStatsAvailable`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `ProviderEndpointStatsUnavailable`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `ProviderEndpoints`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `ProviderEndpointsResponse`
  * Used by `GET /providers/{provider_slug}/endpoints`
* `DecisionsRefusalAnswer`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `DecisionsUrlCitationAnnotation`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `CompactionTriggerItem`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputCompactionItem`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemCompaction`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **15 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `parallel`

  **15 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `GenerationResponse`: property `api_type` updated
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `PerfLast30mByWorkload`: new property `extractions`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `DecisionsResponse`: new property `annotations`; description updated; new union variant added
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `STTRequest`:
  * description updated
  * new property `provider.allow_fallbacks`
  * new property `provider.ignore`
  * new property `provider.only`
  * new property `provider.order`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `SpeechRequest`:
  * description updated
  * new property `provider.allow_fallbacks`
  * new property `provider.ignore`
  * new property `provider.only`
  * new property `provider.order`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `VideoGenerationRequest`:
  * description updated
  * new property `provider.ignore`
  * new property `provider.only`
  * new property `provider.order`
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `WorkspaceMember`: description updated; enum property\_added
  * Used by [`GET /workspaces/{id}/members`](api/api-reference/workspaces/list-workspace-members.md), [`POST /workspaces/{id}/members/add`](api/api-reference/workspaces/bulk-add-members-to-a-workspace.md)
* `AlignmentResponsesRejected`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BaseResponsesResult`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemAddedEvent`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemDoneEvent`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItems`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**November 3, 2026**

## Modified endpoints

* [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md): description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): new parameter `endpoints`

## New schemas

* `DecisionsUsageInputTokensDetails`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)

## Modified schemas

* `DecisionsBoxQuestion`: description updated
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `DecisionsRequest`: description updated
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ReasoningFormat`: enum property\_added

  **6 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DecisionsResponse`: new property `usage.input_tokens_details`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ResponseIncludesEnum`: enum property\_added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **15 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `pearl-research`

  **15 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ProviderOptions`: new property `antdigital`

  **15 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**November 2, 2026**

## Modified schemas

* `CreateGuardrailRequest`: description updated
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`: description updated

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `UpdateGuardrailRequest`: description updated
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)

**October 31, 2026**

## Breaking changes

* `PrivateProviderDataPolicy`: schema object removedAction required
  * **Migration: remove references to `PrivateProviderDataPolicy` and `data_policy`.** Private providers no longer accept or return a configurable `data_policy`; newly created private providers automatically apply a permissive policy (no prompt retention, training, or publication) so their endpoints pass account and guardrail data-policy filters.
* `CreatePrivateProviderRequest`: properties `data_policy` object removedAction required
  * Used by [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
  * **Migration: omit `data_policy` when creating a private provider.** Generated SDKs and Terraform configurations remove `data_policy` from `POST /private-providers` (raw HTTP `POST` requests that still include `data_policy` succeed and ignore the field). Newly created private providers are automatically recorded as not retaining, training on, or publishing prompts.
* `PrivateProvider`: properties `data_policy` object removedAction required

  * **Migration: stop reading `data_policy` from private provider responses.** `GET /private-providers`, `GET /private-providers/{slug}`, `POST /private-providers`, and `PATCH /private-providers/{slug}` no longer include `data_policy` on `PrivateProvider` objects. Existing private providers retain the routing policy they were created with.

  **4 endpoints using this schema**

  * [`GET /private-providers`](api/api-reference/private-providers/list-private-providers.md)
  * [`GET /private-providers/{slug}`](api/api-reference/private-providers/get-a-private-provider.md)
  * [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
  * [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `PrivateProvider`: required `data_policy` property removedNo action needed

  * Companion to the `PrivateProvider` `data_policy` removal above.

  **4 endpoints using this schema**

  * [`GET /private-providers`](api/api-reference/private-providers/list-private-providers.md)
  * [`GET /private-providers/{slug}`](api/api-reference/private-providers/get-a-private-provider.md)
  * [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
  * [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `UpdatePrivateProviderRequest`: properties `data_policy` object removedAction required
  * Used by [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
  * **Migration: remove `data_policy` from `PATCH /private-providers/{slug}` requests.** `data_policy` is ignored on updates, and a `PATCH` body containing only `data_policy` now returns 400 (`Provide at least one field to update`) instead of 200. Remove `PATCH` calls that only updated `data_policy`, or include another updatable field such as `display_name` or `base_url`.

## Modified endpoints

* [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md): description updated

## Modified schemas

* `CreatePrivateProviderRequest`: description updated; example property\_added
  * Used by [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `PrivateProvider`: example modified

  **4 endpoints using this schema**

  * [`GET /private-providers`](api/api-reference/private-providers/list-private-providers.md)
  * [`GET /private-providers/{slug}`](api/api-reference/private-providers/get-a-private-provider.md)
  * [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
  * [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)

**October 30, 2026**

## Breaking changes

* `CreateExternalUserRequest.user`: pattern `^[^\u0000]+$` modifiedNo action needed
  * Used by [`POST /external-users`](api/api-reference/external-users/register-an-external-user.md)
* `ExternalUser.user`: pattern `^[^\u0000]+$` modifiedNo action needed

  **4 endpoints using this schema**

  * [`GET /external-users`](api/api-reference/external-users/list-registered-external-users.md)
  * [`GET /external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md)
  * [`PATCH /external-users/{user}`](api/api-reference/external-users/update-a-registered-external-user.md)
  * [`POST /external-users`](api/api-reference/external-users/register-an-external-user.md)
* `VaultSecretWriteRequest.value`: maxLength `65536` modifiedNo action needed
  * Used by [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md), [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md)
* [`GET /external-users`](api/api-reference/external-users/list-registered-external-users.md): pattern `^[^\u0000]+$` modifiedNo action needed
* [`DELETE /external-users/{user}`](api/api-reference/external-users/deactivate-a-registered-external-user.md): pattern `^[^\u0000]+$` modifiedNo action needed
* [`GET /external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md): pattern `^[^\u0000]+$` modifiedNo action needed
* [`PATCH /external-users/{user}`](api/api-reference/external-users/update-a-registered-external-user.md): pattern `^[^\u0000]+$` modifiedNo action needed
* `ExtractionDateField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionDatetimeField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionDurationField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionEstimateField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionForecastField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionListField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionNumberField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionTextField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionTimeField`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the field schema.** Each entry in `fields` now rejects unknown keys instead of dropping them silently. Before this release a per-field key such as `top_n`, `threshold`, or a misspelled `descripton` returned 200 and had no effect; it now returns 400 with a validation error naming the key. The accepted keys per field type are unchanged, so a request that already validated against the documented schema needs no change.
* `ExtractionsRequest`: additionalProperties `false` object addedAction required
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * **Migration: remove keys that are not in the request schema.** The top level of the request body now rejects unknown keys instead of dropping them silently; such a request returns 400 with a validation error naming the key. Also removed in this release: `provider.options.scaledown.context_chars`, which was accepted but never changed the response (`context` is not returned); delete it from ScaleDown requests. Additive changes you may opt into: list answers now carry a per-item `confidences` array, ScaleDown accepts `format: "pdf"` assets and answers read from them report `source: "document"`, and Inception Mercury can extract every text field in one upstream question with `provider.options.inception.group_fields: true` (default stays one question per field).

## New endpoints

* [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md): Submit an Extractions request

## Modified endpoints

* [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md): request schema updated
* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): request schema updated
* [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md): description updated
* [`DELETE /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/delete-an-intern-secret.md): description updated; parameter `name` updated
* [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md): description updated
* [`DELETE /vault/secrets/{name}`](api/api-reference/vault/delete-a-workspace-secret.md): description updated; parameter `name` updated
* [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md): description updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): new parameter `client`
* [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md): response schema updated
* [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md): response schema updated
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): response schema updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): description updated; response schema updated
* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): description updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated

## New response codes

* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): now returns `403`
* [`DELETE /keys/{hash}`](api/api-reference/api-keys/delete-an-api-key.md): now returns `403`
* [`GET /keys/{hash}`](api/api-reference/api-keys/get-a-single-api-key.md): now returns `403`

## New schemas

* `ClassifierFiltersFilter`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `ClassifierScalarFilter`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `ClassifierScalarFilterOperator`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `ClassifierSetFilter`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `ClassifierSetFilterOperator`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `Filter`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `Operator`
  * Used by [`GET /analytics/meta`](api/api-reference/analytics/get-available-analytics-metrics-and-dimensions.md)
* `ScalarFilter`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `ScalarFilterOperator`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `SetFilter`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `SetFilterOperator`
  * Used by [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md)
* `ExtractionDateAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDateField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDatetimeAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDatetimeField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDurationAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDurationField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionEstimateAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionEstimateField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionForecastAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionForecastField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionForecastStep`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionListAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionListField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionNumberAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionNumberField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTextAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTextField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTimeAnswer`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTimeField`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionsRequest`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionsResponse`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionsUsage`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionAsset`
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)

## Modified schemas

* `ImageGenerationRequest`: description updated
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `VaultSecretWriteRequest`: description updated
  * Used by [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md), [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md)
* `GenerationResponse`: property `api_type` updated
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ProviderOptions`: description updated

  **15 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ResponsesRequest`: new property `access_programs`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ExtractionDateAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDatetimeAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionDurationAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionEstimateAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionForecastAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionListAnswer`: new property `confidences`; description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionNumberAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTextAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionTimeAnswer`: description updated; enum property\_added
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `ExtractionsRequest`: description updated; \$ref modified
  * Used by [`POST /api/alpha/extractions`](api/api-reference/alphaextractions/submit-an-extractions-request.md)
* `Model`: new property `endpoints` (always present)

  **4 endpoints using this schema**

  * [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md)
  * [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)
  * [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md)
  * [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md)
* `ModelResponse`: example modified
  * Used by [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)

**October 29, 2026**

## Breaking changes

* `UpdatePrivateEndpointRequest`: required `upstream_model_id` property removedNo action needed
  * Used by [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
  * **Migration: no action.** `PATCH /private-endpoints/{id}` is now a merge patch over every field an owner controls (`pricing`, `declared_parameters`, `settings`, and the draft-only upstream fields), so no single field is required and only the keys you send change. A request that still sends `upstream_model_id` is accepted on a draft endpoint; on an active endpoint it returns 409 `already_active`, as before. `PUT /private-endpoints/{id}/pricing` and `PUT /private-endpoints/{id}/parameters` were deprecated aliases of this route and have since been removed; send `pricing` or `declared_parameters` to `PATCH /private-endpoints/{id}` instead.

## New endpoints

* [`GET /private-providers`](api/api-reference/private-providers/list-private-providers.md): List private providers
* [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md): Create a private provider
* [`GET /private-providers/{slug}`](api/api-reference/private-providers/get-a-private-provider.md): Get a private provider
* [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md): Update a private provider
* [`DELETE /private-providers/{slug}`](api/api-reference/private-providers/delete-a-private-provider.md): Delete a private provider

## Modified endpoints

* [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md): description updated
* [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters-deprecated): deprecated property\_added; description updated
* [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing-deprecated): deprecated property\_added; description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated

## New schemas

* `CreatePrivateProviderRequest`
  * Used by [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `PrivateEndpointQuantization`

  **5 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters-deprecated)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing-deprecated)
* `PrivateEndpointReasoningReturnMechanism`

  **5 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters-deprecated)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing-deprecated)
* `PrivateEndpointSettings`

  **4 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters-deprecated)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing-deprecated)
* `PrivateProvider`

  **4 endpoints using this schema**

  * [`GET /private-providers`](api/api-reference/private-providers/list-private-providers.md)
  * [`GET /private-providers/{slug}`](api/api-reference/private-providers/get-a-private-provider.md)
  * [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
  * [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `PrivateProviderDataPolicy`
  * Used by [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `UpdatePrivateEndpointSettingsRequest`
  * Used by [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md), [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `UpdatePrivateProviderRequest`
  * Used by [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)

## Modified schemas

* `CreatePrivateEndpointRequest`: new property `settings`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `PrivateEndpoint`: example modified; new property `settings` (always present)

  **4 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters-deprecated)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing-deprecated)
* `UpdatePrivateEndpointRequest`:
  * description updated
  * example property\_added
  * new property `declared_parameters`
  * new property `pricing`
  * new property `settings`
  * Used by [`PATCH /private-endpoints/{id}`](api/api-reference/private-endpoints/update-a-private-endpoint.md)
* `CreatePrivateProviderRequest`: minLength property\_added; maxLength property\_added; pattern property\_added
  * Used by [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `PrivateProvider`: minLength property\_added; property `prompt_retention_days` updated; description updated

  **4 endpoints using this schema**

  * [`GET /private-providers`](api/api-reference/private-providers/list-private-providers.md)
  * [`GET /private-providers/{slug}`](api/api-reference/private-providers/get-a-private-provider.md)
  * [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
  * [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `PrivateProviderDataPolicy`: maximum property\_added; minimum property\_added
  * Used by [`POST /private-providers`](api/api-reference/private-providers/create-a-private-provider.md)
* `UpdatePrivateProviderRequest`: minLength property\_added; property `prompt_retention_days` updated; maxLength property\_added
  * Used by [`PATCH /private-providers/{slug}`](api/api-reference/private-providers/update-a-private-provider.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `kt`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `JevRouterPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**October 28, 2026**

## Breaking changes

* `ObservabilityS3Destination.config.roleArn`: pattern narrowed from `^arn:aws(?:-[a-z]+)*:iam::\d{12}:role\/[\w+=,.@/-]{1,512}$` to `^arn:aws:iam::\d{12}:role\/[\w+=,.@/-]{1,512}$`Action required

  * **Migration: `roleArn` accepts only roles in the commercial AWS partition (`arn:aws:iam::`).** OpenRouter assumes your role from the commercial partition, which cannot assume roles in AWS GovCloud (`arn:aws-us-gov`) or China (`arn:aws-cn`), so destinations with those ARNs never delivered traces. `POST` and `PATCH` requests with such an ARN now fail validation; recreate the destination with a role in the commercial partition.
  * **Migration: the role's trust policy must require the destination's external ID.** In the same release, IAM role destinations started verifying that the trust policy carries an `sts:ExternalId` condition. Test Connection, Send Trace, and live delivery return 403 for a role that accepts any external ID; add the condition to the trust policy and the role is accepted within 5 minutes.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ChatDeveloperMessage.configuration_update`: additionalProperties `false` object removedNo action needed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * **Migration: no action.** `configuration_update` on `ChatDeveloperMessage` is now a reference to the named `ConfigurationUpdate` schema instead of an inline object. The accepted value is unchanged: omit it, send `null`, or send an object with `reasoning`. Only generated SDK type names move; raw HTTP requests are unaffected.
* `ChatDeveloperMessage.configuration_update`: properties `reasoning` object removedNo action needed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * **Migration: no action.** `configuration_update` on `ChatDeveloperMessage` is now a reference to the named `ConfigurationUpdate` schema instead of an inline object. The accepted value is unchanged: omit it, send `null`, or send an object with `reasoning`. Only generated SDK type names move; raw HTTP requests are unaffected.
* `ChatDeveloperMessage.configuration_update`: required `reasoning` property removedNo action needed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * **Migration: no action.** `configuration_update` on `ChatDeveloperMessage` is now a reference to the named `ConfigurationUpdate` schema instead of an inline object. The accepted value is unchanged: omit it, send `null`, or send an object with `reasoning`. Only generated SDK type names move; raw HTTP requests are unaffected.
* `ChatSystemMessage.configuration_update`: additionalProperties `false` object removedNo action needed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * **Migration: no action.** `configuration_update` on `ChatSystemMessage` is now a reference to the named `ConfigurationUpdate` schema instead of an inline object. The accepted value is unchanged: omit it, send `null`, or send an object with `reasoning`. Only generated SDK type names move; raw HTTP requests are unaffected.
* `ChatSystemMessage.configuration_update`: properties `reasoning` object removedNo action needed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * **Migration: no action.** `configuration_update` on `ChatSystemMessage` is now a reference to the named `ConfigurationUpdate` schema instead of an inline object. The accepted value is unchanged: omit it, send `null`, or send an object with `reasoning`. Only generated SDK type names move; raw HTTP requests are unaffected.
* `ChatSystemMessage.configuration_update`: required `reasoning` property removedNo action needed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * **Migration: no action.** `configuration_update` on `ChatSystemMessage` is now a reference to the named `ConfigurationUpdate` schema instead of an inline object. The accepted value is unchanged: omit it, send `null`, or send an object with `reasoning`. Only generated SDK type names move; raw HTTP requests are unaffected.

## Modified endpoints

* [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md): now returns 400 `parameters_invalid` when `declared_parameters` includes `tool_choice` without `tools`, matching `PUT /private-endpoints/{id}/parameters`; the create response does not echo `declared_parameters` or `tested_parameters`, read them back from `GET /private-endpoints/{id}`
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): request schema updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): request schema updated
* [`GET /vault/interns/{internId}/connections`](api/api-reference/vault/list-the-connections-an-intern-can-use.md):
  * description updated
  * response schema updated
  * response now always includes `routing`
  * response now always includes `routing_text`
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New response codes

* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): now returns `401`
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): now returns `404`
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): now returns `408`
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): now returns `409`
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): now returns `429`
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): now returns `408`
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): now returns `409`
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): now returns `429`

## New schemas

* `ConfigurationUpdate`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `VaultRoutingTable`
  * Used by [`GET /vault/interns/{internId}/connections`](api/api-reference/vault/list-the-connections-an-intern-can-use.md)

## Modified schemas

* `ChatDeveloperMessage`: new union variant added; type property\_removed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `ChatSystemMessage`: new union variant added; type property\_removed
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `WebSearchStatus`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `particle-ai`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `CreateGuardrailRequest`: new property `enforce_first_party_harness_models`
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`: new property `enforce_first_party_harness_models`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `OrganizationSettings`: description updated
  * Used by [`GET /organization/settings`](api/api-reference/organization/get-organization-settings.md), [`PATCH /organization/settings`](api/api-reference/organization/update-organization-settings.md)
* `UpdateGuardrailRequest`: new property `enforce_first_party_harness_models`
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
* `UpdateOrganizationSettingsRequest`: description updated
  * Used by [`PATCH /organization/settings`](api/api-reference/organization/update-organization-settings.md)

**October 27, 2026**

## Breaking changes

* `ObservabilityS3Destination.config`: required `accessKeyId` property removedNo action needed

  * **Migration: no action for existing destinations.** S3 destinations now support IAM role authentication (`authMode: "iam_role"` with `provider: "aws"`, `roleArn`, and `region`), where OpenRouter assumes a role in your AWS account instead of storing access keys. `accessKeyId` and `secretAccessKey` are now optional in the schema because IAM role destinations have none. `authMode` defaults to `access_keys`, and in that mode both keys are still required on create and update, so existing requests and destinations behave exactly as before.
  * **Migration for clients that read destinations:** if your code or a generated SDK type assumes `config.accessKeyId` and `config.secretAccessKey` are always present in `GET /observability/destinations` responses, handle them as optional; they are absent on IAM role destinations. Check `config.authMode` to tell the two apart.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination.config`: required `secretAccessKey` property removedNo action needed

  * Same change as above: required only when `authMode` is `access_keys` (the default).

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)

## New endpoints

* [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters): Set private endpoint supported parameters

## Modified endpoints

* [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md): description updated

## New response codes

* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): now returns `503`
* [`POST /generation/feedback`](api/api-reference/generations/submit-feedback-for-a-generation.md): now returns `403`
* [`POST /generation/feedback`](api/api-reference/generations/submit-feedback-for-a-generation.md): now returns `503`
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): now returns `503`
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): now returns `503`
* [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md): now returns `503`
* [`GET /presets`](api/api-reference/presets/list-presets.md): now returns `503`
* [`GET /presets/{slug}`](api/api-reference/presets/get-a-preset.md): now returns `503`
* [`GET /presets/{slug}/versions`](api/api-reference/presets/list-versions-of-a-preset.md): now returns `503`
* [`GET /presets/{slug}/versions/{version}`](api/api-reference/presets/get-a-specific-version-of-a-preset.md): now returns `503`

## New schemas

* `PrivateEndpointDeclaredParameter`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md), [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters)
* `PrivateEndpointParameterCheck`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md), [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `UpdatePrivateEndpointParametersRequest`
  * Used by [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters)
* `DecisionsImageAsset`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)

## Modified schemas

* `ObservabilityS3Destination`:

  * new property `config.authMode`
  * new property `config.externalId`
  * new property `config.provider`
  * new property `config.roleArn`
  * property `region` updated

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `CreatePrivateEndpointRequest`: new property `declared_parameters`; new property `max_completion_tokens`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `PrivateEndpoint`:

  * example modified
  * new property `declared_parameters` (always present)
  * new property `max_completion_tokens`
  * new property `tested_parameters` (always present)

  **4 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
  * [`PUT /private-endpoints/{id}/parameters`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-supported-parameters)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointValidation`: new property `parameters`
  * Used by [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `PrivateEndpointValidationNullable`: new property `parameters`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `DecisionsRequest`: new property `assets`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `primalabs`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**October 26, 2026**

## New schemas

* `AnthropicToolUnion`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

## Modified schemas

* `VideoModel`: enum property\_added
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `MessagesToolAdditionBlock`: description updated; new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

**October 23, 2026**

## Breaking changes

* `CreateInternRequest`: schema object removedAction required
* `DeleteInternRequest`: schema object removedAction required
* `DeleteInternResponse`: schema object removedAction required
* `Intern`: schema object removedAction required
* `InternApprovalMode`: schema object removedAction required
* `InternChatAssistantMessage`: schema object removedAction required
* `InternChatChoice`: schema object removedAction required
* `InternChatCompletionChunk`: schema object removedAction required
* `InternChatCompletionRequest`: schema object removedAction required
* `InternChatDelta`: schema object removedAction required
* `InternChatDeveloperMessage`: schema object removedAction required
* `InternChatEchoedToolCall`: schema object removedAction required
* `InternChatEchoedToolCallFunction`: schema object removedAction required
* `InternChatError`: schema object removedAction required
* `InternChatErrorMetadata`: schema object removedAction required
* `InternChatErrorResponse`: schema object removedAction required
* `InternChatMessage`: schema object removedAction required
* `InternChatMessageContent`: schema object removedAction required
* `InternChatPromptTokensDetails`: schema object removedAction required
* `InternChatSteeredResponse`: schema object removedAction required
* `InternChatStreamError`: schema object removedAction required
* `InternChatStreamingResponse`: schema object removedAction required
* `InternChatSystemMessage`: schema object removedAction required
* `InternChatTextPart`: schema object removedAction required
* `InternChatToolCall`: schema object removedAction required
* `InternChatToolCallFunction`: schema object removedAction required
* `InternChatToolMessage`: schema object removedAction required
* `InternChatUsage`: schema object removedAction required
* `InternChatUserMessage`: schema object removedAction required
* `InternConnection`: schema object removedAction required
* `InternConnectionList`: schema object removedAction required
* `InternDaemonAccess`: schema object removedAction required
* `InternInvokeAcceptedResponse`: schema object removedAction required
* `InternInvokeRequest`: schema object removedAction required
* `InternLifecycleError`: schema object removedAction required
* `InternListResponse`: schema object removedAction required
* `ProvisionInternResponse`: schema object removedAction required
* `SignInternDaemonRequest`: schema object removedAction required
* `SignInternDaemonResponse`: schema object removedAction required
* `SuspendInternResponse`: schema object removedAction required
* `UpdateInternRequest`: schema object removedAction required
* `/interns`: endpoint object removedAction required
* `/interns/{internId}`: endpoint object removedAction required
* `/interns/{internId}/chat/completions`: endpoint object removedAction required
* `/interns/{internId}/connections`: endpoint object removedAction required
* `/interns/{internId}/daemon`: endpoint object removedAction required
* `/interns/{internId}/daemon-access`: endpoint object removedAction required
* `/interns/{internId}/daemon-access/sign`: endpoint object removedAction required
* `/interns/{internId}/daemon/sign`: endpoint object removedAction required
* `/interns/{internId}/icon`: endpoint object removedAction required
* `/interns/{internId}/invoke`: endpoint object removedAction required
* `/interns/{internId}/provision`: endpoint object removedAction required
* `/interns/{internId}/suspend`: endpoint object removedAction required
* \$.tags: Interns object removedAction required

## Modified endpoints

* [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md): response schema updated

## New response codes

* [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md): now returns `403`

## Modified schemas

* `ChatStreamChunk`: property `metadata` updated
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
* `MessagesRequest`: title property\_added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ObservabilityWebhookDestination`: property `method` updated

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `OpenResponsesErrorField`: title property\_added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**October 22, 2026**

## Modified endpoints

* `GET /interns`: description updated
* `POST /interns`: description updated; response schema updated
* `DELETE /interns/{internId}`: description updated; response schema updated
* `GET /interns/{internId}`: description updated
* `PATCH /interns/{internId}`: description updated; response schema updated
* `GET /interns/{internId}/connections`: description updated
* `GET /interns/{internId}/daemon`: description updated
* `GET /interns/{internId}/daemon-access`: description updated
* `POST /interns/{internId}/daemon-access/sign`: description updated
* `POST /interns/{internId}/daemon/sign`: description updated
* `GET /interns/{internId}/icon`: description updated
* `POST /interns/{internId}/provision`: description updated; response schema updated
* `POST /interns/{internId}/suspend`: description updated; response schema updated

## New response codes

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): now returns `403`
* [`DELETE /byok/{id}`](api/api-reference/byok/delete-a-byok-provider-credential.md): now returns `403`
* [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md): now returns `403`
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): now returns `403`
* [`DELETE /observability/destinations/{id}`](api/api-reference/observability/delete-an-observability-destination.md): now returns `403`
* [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md): now returns `403`
* [`GET /scim/group-mappings`](api/api-reference/scim/list-scim-group-mappings.md): now returns `403`
* [`POST /scim/group-mappings`](api/api-reference/scim/create-a-scim-group-mapping.md): now returns `403`
* [`DELETE /scim/group-mappings/{id}`](api/api-reference/scim/delete-a-scim-group-mapping.md): now returns `403`
* [`GET /scim/group-mappings/{id}`](api/api-reference/scim/get-a-scim-group-mapping.md): now returns `403`
* [`PATCH /scim/group-mappings/{id}`](api/api-reference/scim/update-a-scim-group-mapping.md): now returns `403`
* [`GET /scim/groups`](api/api-reference/scim/list-scim-groups.md): now returns `403`
* [`POST /scim/sync-jobs`](api/api-reference/scim/start-a-scim-directory-sync.md): now returns `403`
* [`GET /scim/sync-jobs/{id}`](api/api-reference/scim/get-scim-directory-sync-status.md): now returns `403`
* [`POST /generation/feedback`](api/api-reference/generations/submit-feedback-for-a-generation.md): now returns `409`
* [`GET /external-users`](api/api-reference/external-users/list-registered-external-users.md): now returns `403`
* [`GET /external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md): now returns `403`
* [`GET /presets`](api/api-reference/presets/list-presets.md): now returns `403`
* [`GET /presets/{slug}`](api/api-reference/presets/get-a-preset.md): now returns `403`
* [`GET /presets/{slug}/versions`](api/api-reference/presets/list-versions-of-a-preset.md): now returns `403`
* [`GET /presets/{slug}/versions/{version}`](api/api-reference/presets/get-a-specific-version-of-a-preset.md): now returns `403`

## Modified schemas

* `PrivateEndpointPricing`: description updated

  **4 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)

**October 21, 2026**

## Breaking changes

* `CreateEndUserRequest`: schema object removedAction required
  * Renamed to `CreateExternalUserRequest`; the shape is unchanged, so HTTP callers need no change. The Python SDK (`openrouter` 1.3.70 and later) and TypeScript SDK (`@openrouter/sdk` 1.5.0 and later) replace the `CreateEndUserRequest` model with `CreateExternalUserRequest`.
* `EndUser`: schema object removedAction required
  * Renamed to `ExternalUser`; the shape is unchanged, so HTTP callers need no change. The Python SDK (`openrouter` 1.3.70 and later) and TypeScript SDK (`@openrouter/sdk` 1.5.0 and later) replace the `EndUser` model with `ExternalUser`.
* `EndUserResponse`: schema object removedAction required
  * Renamed to `ExternalUserResponse`; the shape is unchanged, so HTTP callers need no change. The Python SDK (`openrouter` 1.3.70 and later) and TypeScript SDK (`@openrouter/sdk` 1.5.0 and later) replace the `EndUserResponse` model with `ExternalUserResponse`.
* `ListEndUsersResponse`: schema object removedAction required
  * Renamed to `ListExternalUsersResponse`; the shape is unchanged, so HTTP callers need no change. The Python SDK (`openrouter` 1.3.70 and later) and TypeScript SDK (`@openrouter/sdk` 1.5.0 and later) replace the `ListEndUsersResponse` model with `ListExternalUsersResponse`.
* `UpdateEndUserRequest`: schema object removedAction required
  * Renamed to `UpdateExternalUserRequest`; the shape is unchanged, so HTTP callers need no change. The Python SDK (`openrouter` 1.3.70 and later) and TypeScript SDK (`@openrouter/sdk` 1.5.0 and later) replace the `UpdateEndUserRequest` model with `UpdateExternalUserRequest`.
* `/end-users`: endpoint object removedAction required
  * Requests to `/end-users` continue to work and are forwarded to [`/external-users`](api/api-reference/external-users/list-registered-external-users.md), so HTTP callers need no change. In the Python SDK (`openrouter` 1.3.70 and later), switch `client.end_users` to `client.external_users`; the old namespace was removed. In the TypeScript SDK (`@openrouter/sdk` 1.5.0 and later), use `externalUsers` for new code; `endUsers` remains available as a compatibility alias. Method names (`list`, `create`, `get`, `update`, `delete`) are unchanged.
* `/end-users/{user}`: endpoint object removedAction required
  * Requests to `/end-users/{user}` continue to work and are forwarded to [`/external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md), so HTTP callers need no change. Python SDK users switch to `external_users`; TypeScript SDK users can migrate to `externalUsers` while `endUsers` remains available as a compatibility alias, as described on the `/end-users` entry above.
* `GET /interns/{internId}/icon`: content `image/jpeg` object removedNo action needed
  * The response is now declared as `image/*`. The bytes served and their `Content-Type` headers are unchanged.
* `GET /interns/{internId}/icon`: content `image/png` object removedNo action needed
  * The response is now declared as `image/*`. The bytes served and their `Content-Type` headers are unchanged.
* \$.tags: End Users object removedNo action needed
  * Documentation tag renamed to External Users. No API change.
* [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md): x-speakeasy-sse-sentinel `[DONE]` object removedAction required
  * Streams now end at the `message_stop` event and no longer send a trailing `data: [DONE]` frame, matching the Anthropic Messages protocol. Clients that detected the end of a `/messages` stream by waiting for `[DONE]` must terminate on `message_stop` on success, and on the `error` event or stream closure on failure. Anthropic's official SDKs already expect this.
* `BulkAssignMembersRequest`: `member_user_ids` now accepts at most 500 itemsAction required
  * Requests with more than 500 member user IDs now return `400`; previously they were accepted. Split larger lists into batches of 500 or fewer, matching the existing limit on the key assignment endpoints.
  * Used by [`POST /guardrails/{id}/assignments/members`](api/api-reference/guardrails/bulk-assign-members-to-a-guardrail.md)
* `BulkUnassignMembersRequest`: `member_user_ids` now accepts at most 500 itemsAction required
  * Requests with more than 500 member user IDs now return `400`; previously they were accepted. Split larger lists into batches of 500 or fewer, matching the existing limit on the key assignment endpoints.
  * Used by [`POST /guardrails/{id}/assignments/members/remove`](api/api-reference/guardrails/bulk-unassign-members-from-a-guardrail.md)
* `InternDaemonAccess`: required `viewer` property addedAction required
  * Used by `GET /interns/{internId}/daemon`, `GET /interns/{internId}/daemon-access`

## New endpoints

* [`GET /external-users`](api/api-reference/external-users/list-registered-external-users.md): List registered external users
* [`POST /external-users`](api/api-reference/external-users/register-an-external-user.md): Register an external user
* [`GET /external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md): Get a registered external user
* [`PATCH /external-users/{user}`](api/api-reference/external-users/update-a-registered-external-user.md): Update a registered external user
* [`DELETE /external-users/{user}`](api/api-reference/external-users/deactivate-a-registered-external-user.md): Deactivate a registered external user
* `GET /interns/{internId}/connections`: List an intern's connections

## Modified endpoints

* `GET /interns/{internId}/icon`: response schema updated
* `GET /interns`: response schema updated
* `POST /interns`: response schema updated
* `GET /interns/{internId}`: response schema updated
* `PATCH /interns/{internId}`: response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing): description updated
* [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md): description updated
* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): description updated
* [`POST /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/bulk-assign-keys-to-a-guardrail.md): description updated

## New response codes

* [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md): now returns `403`
* [`GET /guardrails/assignments/keys`](api/api-reference/guardrails/list-all-key-assignments.md): now returns `403`
* [`GET /guardrails/assignments/members`](api/api-reference/guardrails/list-all-member-assignments.md): now returns `403`
* [`DELETE /guardrails/{id}`](api/api-reference/guardrails/delete-a-guardrail.md): now returns `403`
* [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md): now returns `403`
* [`GET /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/list-key-assignments-for-a-guardrail.md): now returns `403`
* [`POST /guardrails/{id}/assignments/keys/remove`](api/api-reference/guardrails/bulk-unassign-keys-from-a-guardrail.md): now returns `403`
* [`GET /guardrails/{id}/assignments/members`](api/api-reference/guardrails/list-member-assignments-for-a-guardrail.md): now returns `403`
* [`POST /guardrails/{id}/assignments/members`](api/api-reference/guardrails/bulk-assign-members-to-a-guardrail.md): now returns `403`
* [`POST /guardrails/{id}/assignments/members/remove`](api/api-reference/guardrails/bulk-unassign-members-from-a-guardrail.md): now returns `403`
* [`GET /organization/members`](api/api-reference/organization/list-organization-members.md): now returns `403`
* [`GET /organization/settings`](api/api-reference/organization/get-organization-settings.md): now returns `403`
* [`PATCH /organization/settings`](api/api-reference/organization/update-organization-settings.md): now returns `403`
* [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md): now returns `403`
* [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md): now returns `403`
* [`GET /workspaces/{workspace_ref}/budgets`](api/api-reference/workspaces/list-workspace-budgets.md): now returns `403`
* [`DELETE /workspaces/{workspace_ref}/budgets/{interval}`](api/api-reference/workspaces/delete-a-workspace-budget.md): now returns `403`
* [`GET /workspaces/{workspace_ref}/budgets/{interval}`](api/api-reference/workspaces/get-a-workspace-budget.md): now returns `403`
* [`PUT /workspaces/{workspace_ref}/budgets/{interval}`](api/api-reference/workspaces/create-or-update-a-workspace-budget.md): now returns `403`

## New schemas

* `CreateExternalUserRequest`
  * Used by [`POST /external-users`](api/api-reference/external-users/register-an-external-user.md)
* `ExternalUser`

  **4 endpoints using this schema**

  * [`GET /external-users`](api/api-reference/external-users/list-registered-external-users.md)
  * [`GET /external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md)
  * [`PATCH /external-users/{user}`](api/api-reference/external-users/update-a-registered-external-user.md)
  * [`POST /external-users`](api/api-reference/external-users/register-an-external-user.md)
* `ExternalUserResponse`
  * Used by [`GET /external-users/{user}`](api/api-reference/external-users/get-a-registered-external-user.md), [`PATCH /external-users/{user}`](api/api-reference/external-users/update-a-registered-external-user.md), [`POST /external-users`](api/api-reference/external-users/register-an-external-user.md)
* `ListExternalUsersResponse`
  * Used by [`GET /external-users`](api/api-reference/external-users/list-registered-external-users.md)
* `UpdateExternalUserRequest`
  * Used by [`PATCH /external-users/{user}`](api/api-reference/external-users/update-a-registered-external-user.md)
* `InternConnection`
  * Used by `GET /interns/{internId}/connections`
* `InternConnectionList`
  * Used by `GET /interns/{internId}/connections`

## Modified schemas

* `Intern`: example modified; new property `can_edit`

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `InternListResponse`: example modified
  * Used by `GET /interns`
* `PromptCacheBreakpoint`: description updated; example modified; new property `ttl`

  **6 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `PromptCacheOptions`: description updated

  **6 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum property\_added

  * Added enum value `recursive`.

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `PrivateEndpoint`: example modified
  * Used by [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md), [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint), [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointPricing`: example modified; new property `cache_read`; new property `cache_write`

  **4 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `ProviderName`: enum property\_added

  * Added enum value `Recursive`.

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `recursive`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Added `Recursive` to the `provider_name` enum.
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `InternDaemonAccess`: description updated; example modified; new property `viewer`
  * Used by `GET /interns/{internId}/daemon`, `GET /interns/{internId}/daemon-access`

**October 20, 2026**

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## Modified schemas

* `BYOKProviderSlug`: enum property\_added

  * Added enum value `pareto-alpha`.

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  * Added enum value `ParetoAlpha`.

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `pareto-alpha`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Added `ParetoAlpha` to the `provider_name` enum.
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**October 19, 2026**

## New endpoints

* `GET /interns/{internId}/icon`: Get an intern's icon

## Modified endpoints

* `GET /interns`: response schema updated
* `POST /interns`: response schema updated
* `GET /interns/{internId}`: response schema updated
* `PATCH /interns/{internId}`: response schema updated

## Modified schemas

* `Intern`: example modified; new property `created_by_you`; new property `icon_sha256`

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `InternListResponse`: example modified
  * Used by `GET /interns`
* `BYOKKey`: description updated

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: description updated
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `UpdateBYOKKeyRequest`: description updated
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)

**October 18, 2026**

## New endpoints

* [`GET /vault/interns/{internId}/connections`](api/api-reference/vault/list-the-connections-an-intern-can-use.md): List the connections an intern can use

## Modified endpoints

* `GET /interns/{internId}/daemon`: description updated

## Modified schemas

* `SignInternDaemonRequest`: new property `route`
  * Used by `POST /interns/{internId}/daemon-access/sign`, `POST /interns/{internId}/daemon/sign`
* `SignInternDaemonResponse`: new property `x-ori-invoke-nonce`; new property `x-ori-invoke-signature-v2`
  * Used by `POST /interns/{internId}/daemon-access/sign`, `POST /interns/{internId}/daemon/sign`

**October 17, 2026**

## Modified schemas

* `BatchSubmitBody`: new property `callback_url`
  * Used by [`POST /batches`](api/api-reference/batch/create-a-batch.md)

**October 16, 2026**

## Breaking changes

* `BatchListItem`: required `expires_at` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchListItem`: required `provider` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchObject`: required `expires_at` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchObject`: required `provider` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchPaymentRequiredResponse`: required `expires_at` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
* `BatchPaymentRequiredResponse`: required `provider` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)

## Modified schemas

* `BatchListItem`: new property `expires_at`; new property `provider`
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchObject`: new property `expires_at`; new property `provider`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchPaymentRequiredResponse`: new property `expires_at`; new property `provider`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
* `WebFetchEngineEnum`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchEngineEnum`: description updated

  **8 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**October 15, 2026**

## Breaking changes

* `PublicEndpoint`: required `service_tier` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

## Modified endpoints

* [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md): description updated
* [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md): description updated; response schema updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): new parameter `sort`

## New response codes

* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): now returns `404`
* [`DELETE /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/delete-an-intern-secret.md): now returns `409`
* [`DELETE /vault/secrets/{name}`](api/api-reference/vault/delete-a-workspace-secret.md): now returns `409`
* [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md): now returns `409`

## New schemas

* `PublicServiceTier`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

## Modified schemas

* `ResponsesRequest`: new property `stop`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `PublicEndpoint`: example modified; new property `service_tier`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `TokenExchangeRequest`: description updated; enum property\_added
  * Added `management` to the `scope` enum.
  * Used by [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md)
* `TokenExchangeResponse`: description updated
  * Used by [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md)
* `SpeechInputReferenceImage`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechRequest`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

**October 14, 2026**

## Breaking changes

* `AlignmentRuleRecord`: required `applicable` property addedNo action needed

  * No action required for existing consumers. New response-only field.

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentRuleRecord`: type `number` modifiedAction required

  * `probability` is now `number | null`: it is `null` when `applicable` is `false`. Clients that parse `probability` as a non-null number must handle `null`.

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `PublicEndpoint`: required `supports_diarization` property addedNo action needed
  * No action required for existing consumers. New response-only field.
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

## Modified endpoints

* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): description updated
* [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md): response schema updated; description updated
* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): response schema updated
* [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md): response schema updated

## New response codes

* [`POST /containers/{container_id}/files/{file_id}/promote`](api/api-reference/containers/promote-a-container-file-into-workspace-documents.md): now returns `499`
* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): now returns `499`
* [`POST /files`](api/api-reference/files/upload-a-file.md): now returns `499`
* [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md): now returns `499`
* [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md): now returns `503`
* [`GET /guardrails/assignments/keys`](api/api-reference/guardrails/list-all-key-assignments.md): now returns `400`
* [`GET /guardrails/assignments/keys`](api/api-reference/guardrails/list-all-key-assignments.md): now returns `404`
* [`GET /guardrails/assignments/members`](api/api-reference/guardrails/list-all-member-assignments.md): now returns `400`
* [`GET /guardrails/assignments/members`](api/api-reference/guardrails/list-all-member-assignments.md): now returns `404`

## New schemas

* `AlignmentRule`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ClientClosedRequestResponse`

  **4 endpoints using this schema**

  * [`POST /containers/{container_id}/files/{file_id}/promote`](api/api-reference/containers/promote-a-container-file-into-workspace-documents.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /files`](api/api-reference/files/upload-a-file.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ClientClosedRequestResponseErrorData`

  **4 endpoints using this schema**

  * [`POST /containers/{container_id}/files/{file_id}/promote`](api/api-reference/containers/promote-a-container-file-into-workspace-documents.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /files`](api/api-reference/files/upload-a-file.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ArmorAutoMode`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ArmorContext`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ArmorEnvironmentEntry`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ArmorPlugin`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ArmorRule`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ArmorSafeguardResult`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DecisionsBoxAnswer`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `DecisionsBoxQuestion`
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)

## Modified schemas

* `Alignment`: example modified; description updated; minItems property\_removed

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentPlugin`: example modified; description updated; \$ref modified

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentRuleRecord`: new property `applicable`; description updated

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ChatResult`: new property `alignment`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
* `ChatStreamChunk`: new property `alignment`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
* `OpenResponsesErrorField`: enum property\_added
  * Added `permission_denied` to the `code` enum.
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenResponsesErrorMetadata`: example modified
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesErrorField`: enum property\_added
  * Added `permission_denied` to the `code` enum.
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ChatRequest`: new union variant added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `ChatResult`: new property `safeguard_results`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
* `ChatStreamChunk`: new property `safeguard_results`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ResponsesRequest`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `VideoGenerationResponse`: new property `urls`; description updated
  * Used by [`GET /videos/{jobId}`](api/api-reference/video-generation/poll-video-generation-status.md), [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ListEndpointsResponse`: example modified
  * Used by [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `PublicEndpoint`: example modified; new property `supports_diarization`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `DecisionsRequest`: description updated; new union variant added
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `DecisionsResponse`: description updated; new union variant added
  * Used by [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md), [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)

**October 13, 2026**

## Breaking changes

* `ObservabilityArizeDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: required `broadcast_generation_cost_allocation` property addedNo action needed

  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): required `broadcast_generation_cost_allocation` property addedNo action needed
  * No action required for existing consumers. New required response field; the corresponding field remains optional on create and update requests.

## Modified endpoints

* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): response schema updated
* [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md): response schema updated
* [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md): response schema updated
* [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md): response schema updated

## New schemas

* `OutputArmorBlockedItem`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `OutputItems`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CreateObservabilityDestinationRequest`: new property `broadcast_generation_cost_allocation`
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `CreateObservabilityDestinationResponse`: example modified
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `GetObservabilityDestinationResponse`: example modified
  * Used by [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
* `ListObservabilityDestinationsResponse`: example modified
  * Used by [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
* `ObservabilityArizeDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDestination`: example modified

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: example modified; new property `broadcast_generation_cost_allocation`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `UpdateObservabilityDestinationRequest`: new property `broadcast_generation_cost_allocation`
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
* `UpdateObservabilityDestinationResponse`: example modified
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
* `CreateGuardrailRequest`: new property `allow_safety_retention_google`
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`: new property `allow_safety_retention_google`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `SpeechInput`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechRequest`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `UpdateGuardrailRequest`: new property `allow_safety_retention_google`
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
* `CreateGuardrailRequest`: new property `allow_safety_retention_other`
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`: new property `allow_safety_retention_other`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `UpdateGuardrailRequest`: new property `allow_safety_retention_other`
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)

**October 11, 2026**

## Modified endpoints

* [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md): response schema updated

**October 10, 2026**

## Breaking changes

* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): required `budgets` property addedNo action needed
  * No action required for existing consumers. New response-only field.
* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): required `effective_budget` property addedNo action needed
  * No action required for existing consumers. New response-only field.

## Modified endpoints

* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): response schema updated

## New schemas

* `DeferredBm25Search`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredCustomSearch`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredRegexSearch`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsControl`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `DeferredToolsSearchStrategy`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `KeyBudget`
  * Used by [`GET /key`](api/api-reference/api-keys/get-current-api-key.md)
* `ORAnthropicToolSearchResult`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ORAnthropicToolSearchResultParam`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

## Modified schemas

* `ChatRequest`: new property `deferred_tools`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `CustomTool`: new property `defer_loading`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `MessagesContentBlockStartEvent`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `MessagesRequest`: new property `deferred_tools`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ORAnthropicContentBlock`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `OutputToolSearchServerToolItem`: new property `matches`

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesRequest`: new property `deferred_tools`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `VideoGenerationResponse`: new property `expires_at`
  * Used by [`GET /videos/{jobId}`](api/api-reference/video-generation/poll-video-generation-status.md), [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**October 9, 2026**

## Breaking changes

* `CreateEndUserRequest`: maxLength `256` modifiedNo action needed
  * No action required for existing consumers. The maximum end-user ID length increased from 256 to 512 characters.
  * Used by [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `CreateEndUserRequest`: pattern `^[^\p{Cc}]+$` modifiedNo action needed
  * No action required for existing consumers. The pattern now permits control characters other than NUL.
  * Used by [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `EndUser`: maxLength `256` modifiedNo action needed

  **4 endpoints using this schema**

  * [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users)
  * [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user)
  * [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user)
  * [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `EndUser`: pattern `^[^\p{Cc}]+$` modifiedNo action needed

  **4 endpoints using this schema**

  * [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users)
  * [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user)
  * [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user)
  * [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users): maxLength `256` modifiedNo action needed
* [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users): pattern `^[^\p{Cc}]+$` modifiedNo action needed
* [`DELETE /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/deactivate-a-registered-end-user): maxLength `256` modifiedNo action needed
* [`DELETE /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/deactivate-a-registered-end-user): pattern `^[^\p{Cc}]+$` modifiedNo action needed
* [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user): maxLength `256` modifiedNo action needed
* [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user): pattern `^[^\p{Cc}]+$` modifiedNo action needed
* [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user): maxLength `256` modifiedNo action needed
* [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user): pattern `^[^\p{Cc}]+$` modifiedNo action needed

## Modified endpoints

* [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users): description updated
* [`DELETE /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/deactivate-a-registered-end-user): description updated
* [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user): description updated
* [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user): description updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): description updated; request schema updated
* [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md): description updated
* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): description updated
* [`POST /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/bulk-assign-keys-to-a-guardrail.md): description updated
* `POST /interns`: description updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): description updated

## New response codes

* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): now returns `403`
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): now returns `409`

## Modified schemas

* `CreateEndUserRequest`: description updated
  * Used by [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `EndUser`: description updated

  **4 endpoints using this schema**

  * [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users)
  * [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user)
  * [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user)
  * [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `AlignmentPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**October 8, 2026**

## Modified endpoints

* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): new parameter `include_expired`
* `POST /interns`: description updated; response schema updated

## Modified schemas

* `PublicEndpoint`: description updated
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `JevRouterPlugin`: new property `cost_tier`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BulkAssignKeysRequest`: maxItems property\_added
  * Used by [`POST /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/bulk-assign-keys-to-a-guardrail.md)
* `BulkUnassignKeysRequest`: maxItems property\_added
  * Used by [`POST /guardrails/{id}/assignments/keys/remove`](api/api-reference/guardrails/bulk-unassign-keys-from-a-guardrail.md)

**October 7, 2026**

## New endpoints

* `POST /interns/{internId}/daemon-access/sign`: Sign a daemon request with the caller's identity (deprecated alias)
* `POST /interns/{internId}/daemon/sign`: Sign a daemon request with the caller's identity

## New schemas

* `ToolSearchCallItem`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ToolSearchOutputItem`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SignInternDaemonRequest`
  * Used by `POST /interns/{internId}/daemon-access/sign`, `POST /interns/{internId}/daemon/sign`
* `SignInternDaemonResponse`
  * Used by `POST /interns/{internId}/daemon-access/sign`, `POST /interns/{internId}/daemon/sign`
* `OutputToolSearchCallItem`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `OutputApplyPatchServerToolItem`: new property `error`; \$ref modified

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputDatetimeItem`: new property `error`; \$ref modified

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputImageGenerationServerToolItem`: new property `error`; \$ref modified

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputSearchModelsServerToolItem`: new property `error`; \$ref modified

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputToolSearchServerToolItem`: new property `error`; \$ref modified

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputWebSearchServerToolItem`: new property `error`; \$ref modified

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SwitchyardRouterPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderResponse`: x-speakeasy-unknown-values object\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `OutputItems`: new union variant added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**October 6, 2026**

## Breaking changes

* `BYOKKey`: required `declared_region` property addedNo action needed

  * **No action required for existing consumers.** Responses from BYOK endpoints now include `declared_region` (`"global"`, `"europe"`, `"us"`, or `null`) indicating the key's declared data region.

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): required `last_used_at` property addedNo action needed
  * No action required for existing consumers. API key responses now include `last_used_at`, an ISO 8601 UTC timestamp of the key's most recent recorded usage, or `null` if none has been recorded.
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): required `last_used_at` property addedNo action needed
* [`GET /keys/{hash}`](api/api-reference/api-keys/get-a-single-api-key.md): required `last_used_at` property addedNo action needed
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): required `last_used_at` property addedNo action needed

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): response schema updated
* [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md): response schema updated
* [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md): response schema updated
* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): response schema updated
* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): response schema updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): response schema updated
* [`GET /keys/{hash}`](api/api-reference/api-keys/get-a-single-api-key.md): response schema updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): response schema updated

## New response codes

* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): now returns `409`

## New schemas

* `SpeechInput`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechTurn`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

## Modified schemas

* `BYOKKey`: example modified; new property `declared_region`

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: new property `declared_region`
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyResponse`: example modified
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `GetBYOKKeyResponse`: example modified
  * Used by [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
* `ListBYOKKeysResponse`: example modified
  * Used by [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
* `UpdateBYOKKeyRequest`: new property `declared_region`
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `UpdateBYOKKeyResponse`: example modified
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `SwitchyardRouterPlugin`: new property `judge_model`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SpeechRequest`: new property `instructions`; \$ref modified
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

**October 5, 2026**

## Modified schemas

* `BatchProviderPreferences`: description updated; new property `allow_fallbacks`
  * Used by [`POST /batches`](api/api-reference/batch/create-a-batch.md)

**October 2, 2026**

## Breaking changes

* spec: ^[a-z0-9\*](https://openrouter.ai/docs/\[a-z0-9*-]\{0,61}\[a-z0-9*])?(.[a-z0-9\*](https://openrouter.ai/docs/\[a-z0-9*-]\{0,61}\[a-z0-9*])?)\*\$ modifiedNo action needed

## Modified endpoints

* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): description updated

## Modified schemas

* `ObservabilityClickhouseDestination`: new property `shouldIncludeCacheWriteTokens`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: new property `shouldIncludeCacheWriteTokens`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `STTRequest`: description updated; new property `data_collection`; new property `zdr`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `SpeechRequest`: description updated; new property `data_collection`; new property `zdr`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

**October 1, 2026**

## Breaking changes

* `ActivityItem`: required `cached_tokens` property addedNo action needed
  * Used by [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md)

## Modified endpoints

* [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md): parameter `id` updated
* [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md): parameter `id` updated
* [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md): response schema updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): description updated; response schema updated

## New response codes

* [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md): now returns `400`
* [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md): now returns `400`

## New schemas

* `ChatDynamicServerTool`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)

## Modified schemas

* `ChatFunctionTool`: new union variant added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `ActivityItem`: example modified; new property `cached_tokens`
  * Used by [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md)
* `ActivityResponse`: example modified
  * Used by [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md)
* `ImageGenerationRequest`: enum property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)

**September 30, 2026**

## New endpoints

* [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users): List registered end users
* [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user): Register an end user
* [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user): Get a registered end user
* [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user): Update a registered end user
* [`DELETE /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/deactivate-a-registered-end-user): Deactivate a registered end user
* [`GET /organization/settings`](api/api-reference/organization/get-organization-settings.md): Get organization settings
* [`PATCH /organization/settings`](api/api-reference/organization/update-organization-settings.md): Update organization settings

## Modified endpoints

* [`GET /containers/{container_id}/files`](api/api-reference/containers/list-container-files.md): description updated

## New schemas

* `Alignment`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentAllowedCallRecord`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentBlockedCallRecord`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentCallRecord`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentChatAudio`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentChatImage`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentChatRejected`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentChatToolCall`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentPlugin`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentRejected`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentResponsesRejected`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentRuleRecord`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AlignmentUnavailableCallRecord`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenResponsesErrorField`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenResponsesErrorMetadata`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CreateEndUserRequest`
  * Used by [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `EndUser`

  **4 endpoints using this schema**

  * [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users)
  * [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user)
  * [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user)
  * [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `EndUserResponse`
  * Used by [`GET /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/get-a-registered-end-user), [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user), [`POST /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/register-an-end-user)
* `ListEndUsersResponse`
  * Used by [`GET /end-users`](https://openrouter.ai/docs/api/api-reference/end-users/list-registered-end-users)
* `UpdateEndUserRequest`
  * Used by [`PATCH /end-users/{user}`](https://openrouter.ai/docs/api/api-reference/end-users/update-a-registered-end-user)
* `OrganizationSettings`
  * Used by [`GET /organization/settings`](api/api-reference/organization/get-organization-settings.md), [`PATCH /organization/settings`](api/api-reference/organization/update-organization-settings.md)
* `UpdateOrganizationSettingsRequest`
  * Used by [`PATCH /organization/settings`](api/api-reference/organization/update-organization-settings.md)

## Modified schemas

* `ChatRequest`: new union variant added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ResponsesRequest`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SwitchyardRouterPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**September 29, 2026**

## Breaking changes

* `JevRouterPlugin`: additionalProperties `false` object addedNo action needed

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `STTInputAudio`: properties `data` object removedNo action needed
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTInputAudio`: properties `format` object removedNo action needed
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTInputAudio`: required `data` property removedNo action needed
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTInputAudio`: required `format` property removedNo action needed
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): required `file` property removedNo action needed

## New endpoints

* [`GET /vault/interns/{internId}/effective-secrets`](api/api-reference/vault/list-the-secrets-an-intern-receives.md): List the secrets an intern receives
* [`GET /tools`](api/api-reference/tools/list-server-tools.md): List server tools
* [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md): Get a server tool

## Modified endpoints

* `GET /interns`: description updated
* `POST /interns`: description updated
* `DELETE /interns/{internId}`: description updated
* `GET /interns/{internId}`: description updated
* `PATCH /interns/{internId}`: description updated
* `GET /interns/{internId}/daemon`: description updated
* `GET /interns/{internId}/daemon-access`: description updated
* `POST /interns/{internId}/provision`: description updated
* `POST /interns/{internId}/suspend`: description updated
* [`GET /vault/interns/{internId}/secrets`](api/api-reference/vault/list-intern-secrets.md): description updated
* [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md): description updated
* [`DELETE /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/delete-an-intern-secret.md): description updated
* [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md): description updated
* [`GET /vault/secrets`](api/api-reference/vault/list-workspace-secrets.md): description updated
* [`DELETE /vault/secrets/{name}`](api/api-reference/vault/delete-a-workspace-secret.md): description updated
* [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md): description updated
* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): description updated; request schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New response codes

* [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md): now returns `410`

## New schemas

* `VaultEffectiveSecret`
  * Used by [`GET /vault/interns/{internId}/effective-secrets`](api/api-reference/vault/list-the-secrets-an-intern-receives.md)
* `VaultEffectiveSecretListResponse`
  * Used by [`GET /vault/interns/{internId}/effective-secrets`](api/api-reference/vault/list-the-secrets-an-intern-receives.md)
* `JevRouterPlugin`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `STTEntity`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTInlineInputAudio`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTUrlInputAudio`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `GetToolResponse`
  * Used by [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ListToolsResponse`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md)
* `ServerTool`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolDetails`
  * Used by [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolEngine`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolExecutedBy`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolInputName`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolNativeModel`
  * Used by [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolNativeSupport`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolOutputName`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)
* `ServerToolPrice`
  * Used by [`GET /tools`](api/api-reference/tools/list-server-tools.md), [`GET /tools/{name}`](api/api-reference/tools/get-a-server-tool.md)

## Modified schemas

* `OutputFusionServerToolItem`: description updated

  **4 endpoints using this schema**

  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ChatRequest`: new union variant added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ResponsesRequest`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `JevRouterPlugin`: new property `allowed_models`; description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `elevenlabs`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `STTInputAudio`:
  * new union variant added
  * description updated
  * example property\_removed
  * type property\_removed
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTRequest`: description updated; new property `diarize`; new property `keyterms`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTResponse`: new property `entities`; new property `language_confidence`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTSegment`: new property `channel`; new property `speaker_label`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTWord`:
  * new property `channel`
  * new property `speaker_label`
  * new property `type`
  * description updated
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `ChatRequest`: description updated; enum property\_added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `ResponsesRequest`: description updated; enum property\_added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ServiceTier`: enum property\_added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SpeechRequest`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

**September 28, 2026**

## Breaking changes

* `PublicEndpoint`: required `native_tools` property addedNo action needed
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

## New endpoints

* `GET /interns/{internId}/daemon`: Get an intern's daemon access
* [`GET /private-endpoints`](api/api-reference/private-endpoints/list-private-endpoints.md): List private endpoints
* [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md): Create a private endpoint
* [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md): Get a private endpoint
* [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint): Update a draft private endpoint
* [`DELETE /private-endpoints/{id}`](api/api-reference/private-endpoints/delete-a-private-endpoint.md): Delete a private endpoint
* [`POST /private-endpoints/{id}/activate`](api/api-reference/private-endpoints/activate-a-validated-private-endpoint.md): Activate a validated private endpoint
* [`POST /private-endpoints/{id}/disable`](api/api-reference/private-endpoints/disable-a-private-endpoint.md): Disable a private endpoint
* [`POST /private-endpoints/{id}/enable`](api/api-reference/private-endpoints/enable-a-private-endpoint.md): Enable a private endpoint
* [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing): Set private endpoint pricing
* [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md): Validate a draft private endpoint

## Modified endpoints

* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): response schema updated
* [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md): response schema updated
* `GET /interns/{internId}/daemon-access`: deprecated property\_added; description updated

## New schemas

* `CreatePrivateEndpointRequest`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `CreatePrivateEndpointValidationFailedResponse`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `DeletePrivateEndpointResponse`
  * Used by [`DELETE /private-endpoints/{id}`](api/api-reference/private-endpoints/delete-a-private-endpoint.md)
* `ListPrivateEndpointsResponse`
  * Used by [`GET /private-endpoints`](api/api-reference/private-endpoints/list-private-endpoints.md)
* `ManagedPrivateEndpoint`

  **4 endpoints using this schema**

  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/activate`](api/api-reference/private-endpoints/activate-a-validated-private-endpoint.md)
  * [`POST /private-endpoints/{id}/disable`](api/api-reference/private-endpoints/disable-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/enable`](api/api-reference/private-endpoints/enable-a-private-endpoint.md)
* `ManagedPrivateEndpointResponse`

  **4 endpoints using this schema**

  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/activate`](api/api-reference/private-endpoints/activate-a-validated-private-endpoint.md)
  * [`POST /private-endpoints/{id}/disable`](api/api-reference/private-endpoints/disable-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/enable`](api/api-reference/private-endpoints/enable-a-private-endpoint.md)
* `PrivateEndpoint`
  * Used by [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md), [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint), [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointActivation`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `PrivateEndpointCheck`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md), [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `PrivateEndpointCheckReason`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md), [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `PrivateEndpointDeclaredRegion`

  **7 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/activate`](api/api-reference/private-endpoints/activate-a-validated-private-endpoint.md)
  * [`POST /private-endpoints/{id}/disable`](api/api-reference/private-endpoints/disable-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/enable`](api/api-reference/private-endpoints/enable-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointPricing`

  **4 endpoints using this schema**

  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointResponse`
  * Used by [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md), [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint), [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointStatus`

  **8 endpoints using this schema**

  * [`GET /private-endpoints`](api/api-reference/private-endpoints/list-private-endpoints.md)
  * [`GET /private-endpoints/{id}`](api/api-reference/private-endpoints/get-a-private-endpoint.md)
  * [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/activate`](api/api-reference/private-endpoints/activate-a-validated-private-endpoint.md)
  * [`POST /private-endpoints/{id}/disable`](api/api-reference/private-endpoints/disable-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/enable`](api/api-reference/private-endpoints/enable-a-private-endpoint.md)
  * [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `PrivateEndpointSummary`

  **5 endpoints using this schema**

  * [`GET /private-endpoints`](api/api-reference/private-endpoints/list-private-endpoints.md)
  * [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/activate`](api/api-reference/private-endpoints/activate-a-validated-private-endpoint.md)
  * [`POST /private-endpoints/{id}/disable`](api/api-reference/private-endpoints/disable-a-private-endpoint.md)
  * [`POST /private-endpoints/{id}/enable`](api/api-reference/private-endpoints/enable-a-private-endpoint.md)
* `PrivateEndpointValidation`
  * Used by [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `PrivateEndpointValidationNullable`
  * Used by [`POST /private-endpoints`](api/api-reference/private-endpoints/create-a-private-endpoint.md)
* `PrivateEndpointValidationResponse`
  * Used by [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)
* `UpdatePrivateEndpointPricingRequest`
  * Used by [`PUT /private-endpoints/{id}/pricing`](https://openrouter.ai/docs/api/api-reference/private-endpoints/set-private-endpoint-pricing)
* `UpdatePrivateEndpointRequest`
  * Used by [`PATCH /private-endpoints/{id}`](https://openrouter.ai/docs/api/api-reference/private-endpoints/update-a-draft-private-endpoint)
* `ValidatePrivateEndpointRequest`
  * Used by [`POST /private-endpoints/{id}/validate`](api/api-reference/private-endpoints/validate-a-draft-private-endpoint.md)

## Modified schemas

* `AnthropicWebFetchToolResultError`: enum property\_added
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md), [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `PublicEndpoint`: example modified; new property `native_tools`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

**September 27, 2026**

## New response codes

* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): now returns `504`

**September 25, 2026**

## Breaking changes

* `GET /interns/{internId}/daemon-access`: codes `429` object removedNo action needed
* `SpeechInputReferenceAudioInput`: required `data` property removedNo action needed
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

## New endpoints

* [`GET /batches`](api/api-reference/batch/list-batches.md): List batches
* [`POST /batches`](api/api-reference/batch/create-a-batch.md): Create a batch
* [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md): Get a batch
* [`DELETE /batches/{id}`](api/api-reference/batch/delete-a-batch.md): Delete a batch

## Modified endpoints

* `GET /interns/{internId}/daemon-access`: description updated
* [`POST /audio/speech`](api/api-reference/tts/create-speech.md): description updated
* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New schemas

* `SpeechInputReferenceImage`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceImageInput`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `BatchDeletedObject`
  * Used by [`DELETE /batches/{id}`](api/api-reference/batch/delete-a-batch.md)
* `BatchDeletionOutcome`
  * Used by [`DELETE /batches/{id}`](api/api-reference/batch/delete-a-batch.md)
* `BatchDeletionTargets`
  * Used by [`DELETE /batches/{id}`](api/api-reference/batch/delete-a-batch.md)
* `BatchErrorResponse`

  **4 endpoints using this schema**

  * [`DELETE /batches/{id}`](api/api-reference/batch/delete-a-batch.md)
  * [`GET /batches`](api/api-reference/batch/list-batches.md)
  * [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchListItem`
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchListResponse`
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchListStatus`
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchListTimestamp`
  * Used by [`GET /batches`](api/api-reference/batch/list-batches.md)
* `BatchObject`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchPaymentRequiredResponse`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md)
* `BatchProviderPreferences`
  * Used by [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `BatchSubmitBody`
  * Used by [`POST /batches`](api/api-reference/batch/create-a-batch.md)
* `FinishReason`
  * Used by [`GET /batches/{id}`](api/api-reference/batch/get-a-batch.md), [`POST /batches`](api/api-reference/batch/create-a-batch.md)

## Modified schemas

* `PublicEndpoint`: example modified; new property `supports_image_reference`; new property `supports_multiple_audio_references`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `SpeechInputReference`: description updated; new union variant added
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceAudio`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceAudioInput`: new property `url`; description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceText`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechRequest`: description updated
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `ImageGenerationRequest`: enum property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **14 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /batches`](api/api-reference/batch/create-a-batch.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `respan`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**September 24, 2026**

## New endpoints

* `GET /interns/{internId}/daemon-access`: Get an intern's daemon access

## Modified endpoints

* [`GET /scim/groups`](api/api-reference/scim/list-scim-groups.md): new parameter `display_name`; new parameter `external_id`
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New schemas

* `InternDaemonAccess`
  * Used by `GET /interns/{internId}/daemon-access`

## Modified schemas

* `ProviderPreferences`: new property `options`

  **10 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **13 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
* `ProviderOptions`: new property `scaledown`

  **14 endpoints using this schema**

  * [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md)
  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
  * [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**September 23, 2026**

## Breaking changes

* spec: arguments property addedNo action needed
* spec: call\_id property addedNo action needed
* spec: input property addedNo action needed
* spec: name property addedNo action needed
* spec: type property addedNo action needed
* \$.components: allOf object removedNo action needed
* \$.components: anyOf object removedNo action needed
* `CustomToolCallItem`: allOf `allOf` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `call_id` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `input` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `name` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `type` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FunctionCallItem`: allOf `allOf` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FunctionCallItem`: required `arguments` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FunctionCallItem`: required `call_id` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FunctionCallItem`: required `name` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FunctionCallItem`: required `type` property addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## New endpoints

* `POST /interns/{internId}/invoke`: Start an intern run without waiting for it

## New schemas

* `InternInvokeAcceptedResponse`
  * Used by `POST /interns/{internId}/invoke`
* `InternInvokeRequest`
  * Used by `POST /interns/{internId}/invoke`

## Modified schemas

* `CustomToolCallItem`:
  * new property `async`
  * new property `call_id`
  * new property `id`
  * new property `input`
  * new property `name`
  * new property `namespace`
  * new property `status`
  * new property `type`
  * type property\_added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FunctionCallItem`:
  * new property `arguments`
  * new property `async`
  * new property `call_id`
  * new property `id`
  * new property `name`
  * new property `namespace`
  * new property `status`
  * new property `subagent_id`
  * new property `subagent_items`
  * new property `type`
  * type property\_added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**September 22, 2026**

## Modified endpoints

* [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md): response schema updated
* [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md): response schema updated
* [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md): response schema updated
* [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md): response schema updated
* [`POST /api/alpha/decisions`](api/api-reference/alphadecisions/submit-a-decisions-request.md): description updated
* `POST /interns/{internId}/chat/completions`: description updated
* `DELETE /interns/{internId}`: description updated; response schema updated
* `POST /interns/{internId}/provision`: description updated; response schema updated
* `POST /interns/{internId}/suspend`: description updated; response schema updated

## New schemas

* `AnthropicSafeguard`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `AnthropicSafeguardResult`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `SwitchyardRouterPlugin`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `CreateWorkspaceRequest`: new property `disabled_server_tools`
  * Used by [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `CreateWorkspaceResponse`: example modified
  * Used by [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `GetWorkspaceResponse`: example modified
  * Used by [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md)
* `ListWorkspacesResponse`: example modified
  * Used by [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md)
* `MessagesDeltaEvent`: new property `safeguard_results`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `MessagesRequest`: new property `safeguards`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `UpdateWorkspaceRequest`: new property `disabled_server_tools`
  * Used by [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
* `UpdateWorkspaceResponse`: example modified
  * Used by [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
* `Workspace`: example modified; new property `disabled_server_tools`

  **4 endpoints using this schema**

  * [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md)
  * [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md)
  * [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
  * [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `ResponsesRequest`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ChatRequest`: new union variant added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ResponsesRequest`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**September 21, 2026**

## Breaking changes

* `InternChatErrorMetadata`: required `retryable` property addedNo action needed
  * Used by `POST /interns/{internId}/chat/completions`
* `BYOKKey`: required `declared_zdr` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)

## Modified endpoints

* `GET /interns`: description updated; parameter `status` updated; response schema updated
* `POST /interns`: description updated; parameter `Idempotency-Key` updated; response schema updated
* `DELETE /interns/{internId}`: response schema updated; description updated
* `GET /interns/{internId}`: response schema updated; description updated
* `PATCH /interns/{internId}`: response schema updated; description updated
* `POST /interns/{internId}/chat/completions`: response schema updated; description updated
* `POST /interns/{internId}/provision`: description updated; response schema updated
* `POST /interns/{internId}/suspend`: description updated; response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): response schema updated
* [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md): response schema updated
* [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md): response schema updated
* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): response schema updated
* `POST /interns/{internId}/chat/completions`: description updated
* `POST /interns`: description updated
* `DELETE /interns/{internId}`: description updated
* `PATCH /interns/{internId}`: description updated

## New response codes

* `PATCH /interns/{internId}`: now returns `409`
* `POST /interns/{internId}/chat/completions`: now returns `408`
* `POST /interns/{internId}/provision`: now returns `400`
* `POST /interns/{internId}/provision`: now returns `413`
* `POST /interns/{internId}/suspend`: now returns `400`
* `POST /interns/{internId}/suspend`: now returns `413`
* `POST /interns/{internId}/chat/completions`: now returns `202`
* `POST /interns`: now returns `415`
* `DELETE /interns/{internId}`: now returns `415`
* `PATCH /interns/{internId}`: now returns `415`
* `POST /interns/{internId}/provision`: now returns `415`
* `POST /interns/{internId}/suspend`: now returns `415`

## New schemas

* `XSearchOptions`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `InternChatSteeredResponse`
  * Used by `POST /interns/{internId}/chat/completions`

## Modified schemas

* `InternChatError`: example modified
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatErrorMetadata`: example modified; new property `retryable`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatErrorResponse`: example modified
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatStreamError`: example modified
  * Used by `POST /interns/{internId}/chat/completions`
* `InternLifecycleError`: example modified; new property `metadata`

  **7 endpoints using this schema**

  * `DELETE /interns/{internId}`
  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
  * `POST /interns/{internId}/provision`
  * `POST /interns/{internId}/suspend`
* `VideoGenerationRequest`: enum property\_added
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `VideoModel`: enum property\_added
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `ChatWebSearchShorthand`: new property `x_search`; description updated
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `Legacy_WebSearchServerTool`: new property `x_search`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `Preview_20250311_WebSearchServerTool`: new property `x_search`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `Preview_WebSearchServerTool`: new property `x_search`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchConfig`: new property `x_search`; description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `WebSearchPlugin`: new property `x_search`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchServerTool`: new property `x_search`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchServerToolConfig`: new property `x_search`; description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKKey`: example modified; new property `declared_zdr`

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: new property `declared_zdr`
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyResponse`: example modified
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `GetBYOKKeyResponse`: example modified
  * Used by [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
* `ListBYOKKeysResponse`: example modified
  * Used by [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
* `UpdateBYOKKeyRequest`: new property `declared_zdr`
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `UpdateBYOKKeyResponse`: example modified
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)

**September 20, 2026**

## Breaking changes

* [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md): x-speakeasy-ignore `true` object removedNo action needed
* [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md): tags `alpha.decisions` property removedNo action needed

## New endpoints

* [`POST /systemone`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-system-one-request-typesafe-sdk-compatible-alias): Submit a System One request (TypeSafe SDK compatible alias)

## Modified endpoints

* [`POST /systemone`](api/api-reference/systemone/submit-a-system-one-request.md): x-speakeasy-name-override object\_added; description updated; tags property\_added

**September 19, 2026**

## Breaking changes

* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): required `organization_id` property addedNo action needed
* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): required `workspace_id` property addedNo action needed
* `CreateInternRequest`: required `workspace_id` property removedNo action needed
  * Used by `POST /interns`
* `InternChatAssistantMessage`: required `content` property removedNo action needed
  * Used by `POST /interns/{internId}/chat/completions`
* `DELETE /interns/{internId}`: requestBody `requestBody` property addedAction required
  * Regenerated SDK clients: pass `{}` when no acknowledgement is needed, or `{ acknowledge_workspace_loss: true }` when deleting the intern also requires acknowledging workspace loss. Raw HTTP clients may continue to omit the body.

## Modified endpoints

* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): response schema updated
* `POST /interns`: description updated; response schema updated
* `POST /interns/{internId}/chat/completions`: description updated
* `DELETE /interns/{internId}`: description updated
* `GET /interns`: new parameter `starting_after`
* [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md): description updated; response schema updated

## New response codes

* `DELETE /interns/{internId}`: now returns `400`
* `DELETE /interns/{internId}`: now returns `413`
* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): now returns `403`

## New schemas

* `DeleteInternRequest`
  * Used by `DELETE /interns/{internId}`

## Modified schemas

* `InternChatCompletionRequest`: description updated
  * Used by `POST /interns/{internId}/chat/completions`
* `CreateInternRequest`: description updated
  * Used by `POST /interns`
* `TokenExchangeRequest`: pattern property\_added
  * Used by [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md)
* `InternChatCompletionChunk`: description updated
  * Used by `POST /interns/{internId}/chat/completions`
* `UpdateInternRequest`: description updated; minLength property\_added; pattern property\_added
  * Used by `PATCH /interns/{internId}`
* `InternListResponse`: new property `next_cursor`
  * Used by `GET /interns`

**September 18, 2026**

## Breaking changes

* [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request): tags `Decisions` property removedNo action needed
* \$.tags: Decisions object removedNo action needed
* `Intern`: properties `createdAt` object removedAction required

  * Update response parsing from `createdAt` to `created_at`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: properties `lastFailureMessage` object removedAction required

  * Update response parsing from `lastFailureMessage` to `last_failure_message`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: properties `updatedAt` object removedAction required

  * Update response parsing from `updatedAt` to `updated_at`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: properties `workspaceId` object removedAction required

  * Update response parsing from `workspaceId` to `workspace_id`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `created_at` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `last_failure_message` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `updated_at` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `workspace_id` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `createdAt` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `lastFailureMessage` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `updatedAt` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `workspaceId` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: properties `stepLabel` object removedAction required

  * Update response parsing from `stepLabel` to `step_label`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: properties `stepNumber` object removedAction required

  * Update response parsing from `stepNumber` to `step_number`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: properties `totalSteps` object removedAction required

  * Update response parsing from `totalSteps` to `total_steps`.

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `step_label` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `step_number` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `total_steps` property addedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `stepLabel` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `stepNumber` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `Intern`: required `totalSteps` property removedNo action needed

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `POST /interns`: properties `createdAt` object removedAction required
  * Update response parsing from `createdAt` to `created_at`.
* `POST /interns`: properties `lastFailureMessage` object removedAction required
  * Update response parsing from `lastFailureMessage` to `last_failure_message`.
* `POST /interns`: properties `updatedAt` object removedAction required
  * Update response parsing from `updatedAt` to `updated_at`.
* `POST /interns`: properties `workspaceId` object removedAction required
  * Update response parsing from `workspaceId` to `workspace_id`.
* `POST /interns`: required `created_at` property addedNo action needed
* `POST /interns`: required `last_failure_message` property addedNo action needed
* `POST /interns`: required `updated_at` property addedNo action needed
* `POST /interns`: required `workspace_id` property addedNo action needed
* `POST /interns`: required `createdAt` property removedNo action needed
* `POST /interns`: required `lastFailureMessage` property removedNo action needed
* `POST /interns`: required `updatedAt` property removedNo action needed
* `POST /interns`: required `workspaceId` property removedNo action needed
* `POST /interns`: properties `stepLabel` object removedAction required
  * Update response parsing from `stepLabel` to `step_label`.
* `POST /interns`: properties `stepNumber` object removedAction required
  * Update response parsing from `stepNumber` to `step_number`.
* `POST /interns`: properties `totalSteps` object removedAction required
  * Update response parsing from `totalSteps` to `total_steps`.
* `POST /interns`: required `step_label` property addedNo action needed
* `POST /interns`: required `step_number` property addedNo action needed
* `POST /interns`: required `total_steps` property addedNo action needed
* `POST /interns`: required `stepLabel` property removedNo action needed
* `POST /interns`: required `stepNumber` property removedNo action needed
* `POST /interns`: required `totalSteps` property removedNo action needed
* `GET /interns/{internId}`: properties `createdAt` object removedAction required
  * Update response parsing from `createdAt` to `created_at`.
* `GET /interns/{internId}`: properties `lastFailureMessage` object removedAction required
  * Update response parsing from `lastFailureMessage` to `last_failure_message`.
* `GET /interns/{internId}`: properties `updatedAt` object removedAction required
  * Update response parsing from `updatedAt` to `updated_at`.
* `GET /interns/{internId}`: properties `workspaceId` object removedAction required
  * Update response parsing from `workspaceId` to `workspace_id`.
* `GET /interns/{internId}`: required `created_at` property addedNo action needed
* `GET /interns/{internId}`: required `last_failure_message` property addedNo action needed
* `GET /interns/{internId}`: required `updated_at` property addedNo action needed
* `GET /interns/{internId}`: required `workspace_id` property addedNo action needed
* `GET /interns/{internId}`: required `createdAt` property removedNo action needed
* `GET /interns/{internId}`: required `lastFailureMessage` property removedNo action needed
* `GET /interns/{internId}`: required `updatedAt` property removedNo action needed
* `GET /interns/{internId}`: required `workspaceId` property removedNo action needed
* `GET /interns/{internId}`: properties `stepLabel` object removedAction required
  * Update response parsing from `stepLabel` to `step_label`.
* `GET /interns/{internId}`: properties `stepNumber` object removedAction required
  * Update response parsing from `stepNumber` to `step_number`.
* `GET /interns/{internId}`: properties `totalSteps` object removedAction required
  * Update response parsing from `totalSteps` to `total_steps`.
* `GET /interns/{internId}`: required `step_label` property addedNo action needed
* `GET /interns/{internId}`: required `step_number` property addedNo action needed
* `GET /interns/{internId}`: required `total_steps` property addedNo action needed
* `GET /interns/{internId}`: required `stepLabel` property removedNo action needed
* `GET /interns/{internId}`: required `stepNumber` property removedNo action needed
* `GET /interns/{internId}`: required `totalSteps` property removedNo action needed
* `PATCH /interns/{internId}`: properties `createdAt` object removedAction required
  * Update response parsing from `createdAt` to `created_at`.
* `PATCH /interns/{internId}`: properties `lastFailureMessage` object removedAction required
  * Update response parsing from `lastFailureMessage` to `last_failure_message`.
* `PATCH /interns/{internId}`: properties `updatedAt` object removedAction required
  * Update response parsing from `updatedAt` to `updated_at`.
* `PATCH /interns/{internId}`: properties `workspaceId` object removedAction required
  * Update response parsing from `workspaceId` to `workspace_id`.
* `PATCH /interns/{internId}`: required `created_at` property addedNo action needed
* `PATCH /interns/{internId}`: required `last_failure_message` property addedNo action needed
* `PATCH /interns/{internId}`: required `updated_at` property addedNo action needed
* `PATCH /interns/{internId}`: required `workspace_id` property addedNo action needed
* `PATCH /interns/{internId}`: required `createdAt` property removedNo action needed
* `PATCH /interns/{internId}`: required `lastFailureMessage` property removedNo action needed
* `PATCH /interns/{internId}`: required `updatedAt` property removedNo action needed
* `PATCH /interns/{internId}`: required `workspaceId` property removedNo action needed
* `PATCH /interns/{internId}`: properties `stepLabel` object removedAction required
  * Update response parsing from `stepLabel` to `step_label`.
* `PATCH /interns/{internId}`: properties `stepNumber` object removedAction required
  * Update response parsing from `stepNumber` to `step_number`.
* `PATCH /interns/{internId}`: properties `totalSteps` object removedAction required
  * Update response parsing from `totalSteps` to `total_steps`.
* `PATCH /interns/{internId}`: required `step_label` property addedNo action needed
* `PATCH /interns/{internId}`: required `step_number` property addedNo action needed
* `PATCH /interns/{internId}`: required `total_steps` property addedNo action needed
* `PATCH /interns/{internId}`: required `stepLabel` property removedNo action needed
* `PATCH /interns/{internId}`: required `stepNumber` property removedNo action needed
* `PATCH /interns/{internId}`: required `totalSteps` property removedNo action needed

## Modified endpoints

* [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request): tags property\_added
* [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request): request schema updated; response schema updated
* `GET /interns`: response schema updated
* `POST /interns`: response schema updated
* `GET /interns/{internId}`: response schema updated
* `PATCH /interns/{internId}`: response schema updated

## Modified schemas

* `DecisionsScoreQuestion`: minItems property\_added
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsChoiceQuestion`: new union variant added; description updated; type property\_removed
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsNoulQuestion`:
  * new union variant added
  * property `false` updated
  * property `true` updated
  * description updated
  * type property\_removed
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsScoreAnswer`: new union variant added; description updated; type property\_removed
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsScoreQuestion`: new union variant added; description updated; type property\_removed
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/alphadecisions/submit-a-decisions-questions-and-answers-request)
* `PublicEndpoint`: new property `decisions`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `Intern`:

  * example modified
  * new property `created_at`
  * new property `last_failure_message`
  * new property `updated_at`
  * new property `workspace_id`
  * new property `step_label`
  * new property `step_number`
  * new property `total_steps`

  **4 endpoints using this schema**

  * `GET /interns`
  * `GET /interns/{internId}`
  * `PATCH /interns/{internId}`
  * `POST /interns`
* `InternListResponse`: example modified
  * Used by `GET /interns`
* `VaultSecret`: description updated

  **5 endpoints using this schema**

  * [`GET /vault/interns/{internId}/secrets`](api/api-reference/vault/list-intern-secrets.md)
  * [`GET /vault/secrets`](api/api-reference/vault/list-workspace-secrets.md)
  * [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md)
  * [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md)
  * [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md)

**September 17, 2026**

## New endpoints

* `POST /interns/{internId}/chat/completions`: Stream a chat completion with an intern
* [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request): Submit a Decisions (questions and answers) request

## Modified endpoints

* [`GET /containers/{container_id}/files`](api/api-reference/containers/list-container-files.md): description updated
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): description updated
* [`POST /responses`](api/api-reference/responses/create-a-response.md): description updated; response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): description updated
* [`GET /models/count`](api/api-reference/models/get-total-count-of-available-models.md): description updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): description updated
* [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request): x-speakeasy-name-override modified

## New schemas

* `InternApprovalMode`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatAssistantMessage`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatChoice`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatCompletionChunk`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatCompletionRequest`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatDelta`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatDeveloperMessage`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatEchoedToolCall`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatEchoedToolCallFunction`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatError`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatErrorMetadata`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatErrorResponse`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatMessage`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatMessageContent`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatPromptTokensDetails`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatStreamError`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatStreamingResponse`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatSystemMessage`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatTextPart`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatToolCall`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatToolCallFunction`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatToolMessage`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatUsage`
  * Used by `POST /interns/{internId}/chat/completions`
* `InternChatUserMessage`
  * Used by `POST /interns/{internId}/chat/completions`
* `DecisionsChoiceAnswer`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsChoiceQuestion`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsNoulAnswer`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsNoulQuestion`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsRequest`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsResponse`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsScoreAnswer`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `DecisionsScoreQuestion`
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)

## Modified schemas

* `AnthropicImageBlockParam`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ContainerFileListResponse`: description updated
  * Used by [`GET /containers/{container_id}/files`](api/api-reference/containers/list-container-files.md)
* `InputImage`: description updated; new property `file_id`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `STTResponse`: new property `confidence`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTWord`: example modified; new property `confidence`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `GenerationResponse`: property `api_type` updated
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ImageOutputModality`: enum property\_added
  * Used by [`GET /images/models`](api/api-reference/images/list-image-generation-models.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `OutputModality`: enum property\_added

  **5 endpoints using this schema**

  * [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md)
  * [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)
  * [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md)
  * [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `ProviderName`: enum property\_added

  **12 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `typesafe`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `DecisionsRequest`: new union variant added; description updated
  * Used by [`POST /api/alpha/decisions`](https://openrouter.ai/docs/api/api-reference/decisions/submit-a-decisions-questions-and-answers-request)
* `VideoGenerationRequest`: new property `previous_job_id`
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `VideoGenerationResponse`: example modified; description updated
  * Used by [`GET /videos/{jobId}`](api/api-reference/video-generation/poll-video-generation-status.md), [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderOptions`: new property `unbiased`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**September 16, 2026**

## Breaking changes

* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): required `free_model_daily_requests` property addedNo action needed
* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): required `allowed_data_regions` property addedNo action needed

## New endpoints

* [`GET /vault/interns/{internId}/secrets`](api/api-reference/vault/list-intern-secrets.md): List intern secrets
* [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md): Copy workspace secrets to an intern
* [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md): Store an intern secret
* [`DELETE /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/delete-an-intern-secret.md): Delete an intern secret
* [`GET /vault/secrets`](api/api-reference/vault/list-workspace-secrets.md): List workspace secrets
* [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md): Store a workspace secret
* [`DELETE /vault/secrets/{name}`](api/api-reference/vault/delete-a-workspace-secret.md): Delete a workspace secret

## Modified endpoints

* [`GET /key`](api/api-reference/api-keys/get-current-api-key.md): response schema updated
* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): request schema updated
* [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md): request schema updated
* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): request schema updated

## New response codes

* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): now returns `504`

## New schemas

* `FreeModelDailyRequests`
  * Used by [`GET /key`](api/api-reference/api-keys/get-current-api-key.md)
* `GatewayTimeoutResponse`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `GatewayTimeoutResponseErrorData`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `VaultSecret`

  **5 endpoints using this schema**

  * [`GET /vault/interns/{internId}/secrets`](api/api-reference/vault/list-intern-secrets.md)
  * [`GET /vault/secrets`](api/api-reference/vault/list-workspace-secrets.md)
  * [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md)
  * [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md)
  * [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md)
* `VaultSecretCopyRequest`
  * Used by [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md)
* `VaultSecretCopyResponse`
  * Used by [`POST /vault/interns/{internId}/secrets/copy`](api/api-reference/vault/copy-workspace-secrets-to-an-intern.md)
* `VaultSecretListResponse`
  * Used by [`GET /vault/interns/{internId}/secrets`](api/api-reference/vault/list-intern-secrets.md), [`GET /vault/secrets`](api/api-reference/vault/list-workspace-secrets.md)
* `VaultSecretResponse`
  * Used by [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md), [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md)
* `VaultSecretWriteRequest`
  * Used by [`PUT /vault/interns/{internId}/secrets/{name}`](api/api-reference/vault/store-an-intern-secret.md), [`PUT /vault/secrets/{name}`](api/api-reference/vault/store-a-workspace-secret.md)

## Modified schemas

* `OutputBashServerToolItem`: new property `error`; \$ref modified
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputShellCallOutputItem`: description updated; new property `error`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputShellServerToolItem`: new property `error`; \$ref modified
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ShellCallOutputItem`: new property `error`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ImageGenerationRequest`: new property `session_id`
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `STTRequest`: new property `session_id`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `SpeechRequest`: new property `session_id`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `VideoGenerationRequest`: new property `session_id`
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**September 15, 2026**

## Modified endpoints

* [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md): description updated
* [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md): request schema updated
* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): request schema updated

## New response codes

* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): now returns `403`
* [`POST /guardrails/{id}/assignments/keys`](api/api-reference/guardrails/bulk-assign-keys-to-a-guardrail.md): now returns `403`

## Modified schemas

* `ImageGenerationRequest`: enum property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `ImageGenerationRequest`: maxLength property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `STTRequest`: new property `user`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `SpeechRequest`: new property `user`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `VideoGenerationRequest`: new property `user`
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ImageGenerationRequest`: new property `trace`
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `STTRequest`: new property `trace`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `SpeechRequest`: new property `trace`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `VideoGenerationRequest`: new property `trace`
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**September 14, 2026**

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New response codes

* [`GET /videos/{jobId}/content`](api/api-reference/video-generation/download-generated-video-content.md): now returns `409`
* [`GET /videos/{jobId}/content`](api/api-reference/video-generation/download-generated-video-content.md): now returns `410`

## Modified schemas

* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `assemblyai`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**September 11, 2026**

## Modified endpoints

* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): request schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## Modified schemas

* `CustomTool`: new property `async`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionPlugin`: example modified; description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionServerToolConfig`: example modified

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionServerTool_OpenRouter`: example modified

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `NamespaceFunctionTool`: new property `async`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponseCustomToolCall`: new property `async`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponseFunctionToolCall`: new property `async`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputCustomToolCallItem`: new property `async`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemCustomToolCall`: new property `async`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemFunctionCall`: new property `async`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesErrorField`: enum property\_added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)

**September 10, 2026**

## Breaking changes

* `/workspaces/{id}/budgets`: endpoint object removedAction required
  * SDK and Terraform callers: rename the path argument from `id` to `workspace_ref` (`workspaceRef` in camelCase clients). The URL value itself is unchanged.
* `/workspaces/{id}/budgets/{interval}`: endpoint object removedAction required
  * SDK and Terraform callers: rename the path argument from `id` to `workspace_ref` (`workspaceRef` in camelCase clients). The URL value itself is unchanged.

## New endpoints

* [`GET /workspaces/{workspace_ref}/budgets`](api/api-reference/workspaces/list-workspace-budgets.md): List workspace budgets
* [`GET /workspaces/{workspace_ref}/budgets/{interval}`](api/api-reference/workspaces/get-a-workspace-budget.md): Get a workspace budget
* [`PUT /workspaces/{workspace_ref}/budgets/{interval}`](api/api-reference/workspaces/create-or-update-a-workspace-budget.md): Create or update a workspace budget
* [`DELETE /workspaces/{workspace_ref}/budgets/{interval}`](api/api-reference/workspaces/delete-a-workspace-budget.md): Delete a workspace budget

**September 9, 2026**

## Breaking changes

* `BYOKKey`: required `is_byok_only` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `BYOKKey`: required `is_required` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated; response schema updated
* [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md): response schema updated
* [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md): response schema updated
* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): response schema updated

## Modified schemas

* `BYOKKey`:

  * example modified
  * new property `is_byok_only`
  * new property `is_required`
  * description updated

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: new property `is_byok_only`; new property `is_required`; description updated
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyResponse`: example modified
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `GetBYOKKeyResponse`: example modified
  * Used by [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
* `ListBYOKKeysResponse`: example modified
  * Used by [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `near-ai`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `UpdateBYOKKeyRequest`: new property `is_byok_only`; new property `is_required`; description updated
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `UpdateBYOKKeyResponse`: example modified
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `AnthropicThinkingBlockBinding`: new property `mismatch_behavior`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

**September 8, 2026**

## Breaking changes

* `SandboxSleepAfterSeconds`: schema object removedAction required
  * Remove `sleep_after_seconds` from bash and shell tool configuration. There is no replacement; container lifecycle now uses the service-managed behavior.
* `BashServerToolConfig`: properties `sleep_after_seconds` object removedAction required

  * Remove `sleep_after_seconds` from bash and shell tool configuration. There is no replacement; container lifecycle now uses the service-managed behavior.

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ShellServerToolConfig`: properties `sleep_after_seconds` object removedAction required

  * Remove `sleep_after_seconds` from bash and shell tool configuration. There is no replacement; container lifecycle now uses the service-managed behavior.

  **4 endpoints using this schema**

  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BYOKProviderSlug`: enum `ncompass` property removedAction required

  * Remove `ncompass` from BYOK and provider configuration. The provider has been retired and has no replacement slug.

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `ProviderName`: enum `NCompass` property removedAction required

  * Remove `ncompass` from BYOK and provider configuration. The provider has been retired and has no replacement slug.

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): enum `ncompass` property removedAction required
  * Remove `ncompass` from BYOK and provider configuration. The provider has been retired and has no replacement slug.
* `BYOKProviderSlug`: enum `prime-intellect` property removedAction required

  * Replace the provider slug and configuration key `prime-intellect` with `primeintellect`.

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `ProviderOptions`: properties `prime-intellect` object removedAction required

  * Replace the provider slug and configuration key `prime-intellect` with `primeintellect`.

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): enum `prime-intellect` property removedAction required
  * Replace the provider slug and configuration key `prime-intellect` with `primeintellect`.

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## Modified schemas

* `ChatDeveloperMessage`: new property `configuration_update`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `ProviderOptions`: new property `primeintellect`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ImageGenerationRequest`: enum property\_added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)

**September 7, 2026**

## Modified schemas

* `STTInputAudio`: pattern property\_added
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)

**September 5, 2026**

## Breaking changes

* `ObservabilityArizeDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: required `regions` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): required `regions` property addedNo action needed

## Modified endpoints

* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): response schema updated
* [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md): response schema updated
* [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md): response schema updated
* [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md): response schema updated

## New schemas

* `ObservabilityDataRegion`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDataRegionInput`
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md), [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)

## Modified schemas

* `CreateObservabilityDestinationRequest`: new property `regions`
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `CreateObservabilityDestinationResponse`: example modified
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `GetObservabilityDestinationResponse`: example modified
  * Used by [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
* `ListObservabilityDestinationsResponse`: example modified
  * Used by [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
* `ObservabilityArizeDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDestination`: example modified

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: example modified; new property `regions`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `UpdateObservabilityDestinationRequest`: new property `regions`
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
* `UpdateObservabilityDestinationResponse`: example modified
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)

**September 4, 2026**

## New endpoints

* [`POST /scim/sync-jobs`](api/api-reference/scim/start-a-scim-directory-sync.md): Start a SCIM directory sync
* [`GET /scim/sync-jobs/{id}`](api/api-reference/scim/get-scim-directory-sync-status.md): Get SCIM directory sync status

## New schemas

* `CreateScimSyncJobResponse`
  * Used by [`POST /scim/sync-jobs`](api/api-reference/scim/start-a-scim-directory-sync.md)
* `GetScimSyncJobResponse`
  * Used by [`GET /scim/sync-jobs/{id}`](api/api-reference/scim/get-scim-directory-sync-status.md)
* `ScimSyncJob`
  * Used by [`GET /scim/sync-jobs/{id}`](api/api-reference/scim/get-scim-directory-sync-status.md), [`POST /scim/sync-jobs`](api/api-reference/scim/start-a-scim-directory-sync.md)
* `ConfigurationUpdateItem`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ConfigurationUpdateReasoning`

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpHttpError`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpProtocolError`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpToolCallError`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `McpToolExecutionError`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `ChatSystemMessage`: new property `configuration_update`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `McpCallItem`: \$ref modified
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesErrorField`: enum property\_added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SandboxSleepAfterSeconds`: description updated; example modified

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**September 3, 2026**

## New endpoints

* [`GET /oauth/jwks`](api/api-reference/oauth/openrouter-access-token-signing-keys.md): OpenRouter access token signing keys
* [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md): Exchange a workload identity token

## Modified endpoints

* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated; request schema updated
* [`DELETE /keys/{hash}`](api/api-reference/api-keys/delete-an-api-key.md): description updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): description updated
* [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md): description updated; request schema updated
* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New response codes

* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): now returns `409`

## New schemas

* `OAuthErrorResponse`
  * Used by [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md)
* `OAuthJwks`
  * Used by [`GET /oauth/jwks`](api/api-reference/oauth/openrouter-access-token-signing-keys.md)
* `TokenExchangeRequest`
  * Used by [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md)
* `TokenExchangeResponse`
  * Used by [`POST /oauth/token`](api/api-reference/oauth/exchange-a-workload-identity-token.md)

## Modified schemas

* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `prime-intellect`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**September 2, 2026**

## Breaking changes

* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): properties `external_api_key` object removedNo action needed
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): properties `external_user` object removedNo action needed

## Modified endpoints

* [`POST /scim/group-mappings`](api/api-reference/scim/create-a-scim-group-mapping.md): description updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated

## New response codes

* [`POST /audio/speech`](api/api-reference/tts/create-speech.md): now returns `403`
* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): now returns `403`
* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): now returns `403`
* [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md): now returns `403`
* [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md): now returns `403`
* [`GET /videos/{jobId}`](api/api-reference/video-generation/poll-video-generation-status.md): now returns `403`
* [`GET /videos/{jobId}/content`](api/api-reference/video-generation/download-generated-video-content.md): now returns `403`

## New schemas

* `GuardrailDataRegion`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)

## Modified schemas

* `CostDetails`: example modified; description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `Usage`: example modified
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ChatContentVideoInput`: new property `processing`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `InputVideo`: new property `processing`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `Legacy_ChatContentVideoInput`: new property `processing`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `OpenRouterMetadata`: example modified; new property `generation_time`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CreateGuardrailRequest`: new property `allowed_data_regions`
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`: example modified; new property `allowed_data_regions`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `UpdateGuardrailRequest`: new property `allowed_data_regions`
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)

**September 1, 2026**

## Breaking changes

* `AnthropicThinkingBlockBinding`: required `prefix_mismatch_behavior` property removedNo action needed
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `AnthropicThinkingBlockBinding`: type `string` modifiedNo action needed
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

## Modified endpoints

* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): description updated
* [`GET /models/count`](api/api-reference/models/get-total-count-of-available-models.md): description updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New schemas

* `AnthropicInputTransformation`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `AnthropicMessageOutputConfig`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `AnthropicOutputEffort`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `AnthropicSystemClearAt`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `AnthropicThinkingBlockBinding`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ORAnthropicServerToolUsage`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `AnthropicContainerSkill`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)

## Modified schemas

* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `AnthropicThinkingDisplay`: enum property\_added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `BaseMessagesResult`: new property `input_transformations`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `MessagesMessageParam`: new property `clear_at`; new property `output_config`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `MessagesStartEvent`: new property `input_transformations`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `MessagesDeltaEvent`: property `server_tool_use` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `AnthropicContainer`: example modified; new property `skills`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `AnthropicSystemClearAt`: enum property\_added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `AnthropicThinkingBlockBinding`: enum property\_added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)

**August 31, 2026**

## Modified schemas

* `CostDetails`: example modified; new property `server_tool_cost`

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `Usage`: example modified
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputCustomToolCallItem`: example modified; new property `status`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemCustomToolCall`: example modified; new property `status`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 30, 2026**

## Modified endpoints

* [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md): description updated; request schema updated
* [`POST /auth/keys/code`](api/api-reference/oauth/create-authorization-code.md): description updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated

**August 28, 2026**

## Breaking changes

* `PublicEndpoint`: required `supports_tool_choice` property addedNo action needed
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

## Modified endpoints

* [`POST /containers/{container_id}/files/{file_id}/promote`](api/api-reference/containers/promote-a-container-file-into-workspace-documents.md): description updated; response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): description updated; new parameter `output_modalities`

## New schemas

* `ToolChoiceSupport`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

## Modified schemas

* `PublicEndpoint`: example modified; new property `supports_tool_choice`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `ollama`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ProviderOptions`: new property `cosine`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**August 27, 2026**

## Modified schemas

* `CreateGuardrailResponse`: example modified
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `GetGuardrailResponse`: example modified
  * Used by [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
* `ListGuardrailsResponse`: example modified
  * Used by [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
* `UpdateGuardrailResponse`: example modified
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)

**August 26, 2026**

## Breaking changes

* [`GET /containers/{container_id}/files`](api/api-reference/containers/list-container-files.md): x-hidden `true` object removedNo action needed
* [`GET /containers/{container_id}/files/{file_id}`](api/api-reference/containers/retrieve-a-container-file.md): x-hidden `true` object removedNo action needed
* [`GET /containers/{container_id}/files/{file_id}/content`](api/api-reference/containers/download-container-file-content.md): x-hidden `true` object removedNo action needed
* [`POST /containers/{container_id}/files/{file_id}/promote`](api/api-reference/containers/promote-a-container-file-into-workspace-documents.md): x-hidden `true` object removedNo action needed
* [`GET /files`](api/api-reference/files/list-files.md): x-hidden `true` object removedNo action needed
* [`POST /files`](api/api-reference/files/upload-a-file.md): x-hidden `true` object removedNo action needed
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): x-hidden `true` object removedNo action needed
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): x-hidden `true` object removedNo action needed
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): x-hidden `true` object removedNo action needed

## Modified endpoints

* [`DELETE /workspaces/{id}`](api/api-reference/workspaces/delete-a-workspace.md): description updated
* [`DELETE /workspaces/{id}`](api/api-reference/workspaces/delete-a-workspace.md): new parameter `confirm_default_workspace_deletion`
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): parameter `file_id` updated
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): parameter `file_id` updated
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): parameter `file_id` updated

## Modified schemas

* `ImageGenerationRequest`: new property `user`
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `ShellCallOutputItem`: new property `container_id`; new property `files`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ContentFilterBuiltinEntry`: description updated

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `ContentFilterBuiltinSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)

**August 25, 2026**

## New endpoints

* [`POST /containers/{container_id}/files/{file_id}/promote`](api/api-reference/containers/promote-a-container-file-into-workspace-documents.md): Promote a container file into workspace documents

## New response codes

* [`POST /audio/speech`](api/api-reference/tts/create-speech.md): now returns `413`
* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): now returns `413`
* [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md): now returns `413`
* [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md): now returns `413`

## New schemas

* `ContainerNetworkPolicy`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ContainerFileIds`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `ContainerAutoEnvironment`: new property `network_policy`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ContainerReferenceEnvironment`: new property `network_policy`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SandboxSleepAfterSeconds`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ContainerAutoEnvironment`: new property `file_ids`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ContainerReferenceEnvironment`: new property `file_ids`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `PublicEndpoint`: description updated
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `TopProviderInfo`: description updated

  **4 endpoints using this schema**

  * [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md)
  * [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)
  * [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md)
  * [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md)
* `CreateGuardrailRequest`: description updated
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `ImagePricingEntry`: enum property\_added
  * Used by [`GET /images/models/{author}/{slug}/endpoints`](api/api-reference/images/list-endpoints-for-an-image-model.md)
* `FusionPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 24, 2026**

## Breaking changes

* `ContainerReferenceEnvironment`: maxLength `20` modifiedNo action needed

  * No action required for existing consumers. The maximum container reference length increased from 20 to 40 characters.

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `/containers/{session_id}/files`: endpoint object removedAction required
  * Use the corresponding `/containers/{container_id}/...` endpoint and pass the canonical `container_id` returned by a bash or shell tool result instead of the original session ID.
* `/containers/{session_id}/files/{file_id}`: endpoint object removedAction required
  * Use the corresponding `/containers/{container_id}/...` endpoint and pass the canonical `container_id` returned by a bash or shell tool result instead of the original session ID.
* `/containers/{session_id}/files/{file_id}/content`: endpoint object removedAction required
  * Use the corresponding `/containers/{container_id}/...` endpoint and pass the canonical `container_id` returned by a bash or shell tool result instead of the original session ID.
* `ObservabilityDatadogDestination`: default `https://api.us5.datadoghq.com` modifiedAction required

  * If your Datadog site is US5 and you relied on the omitted URL default, explicitly set `url` to `https://api.us5.datadoghq.com`. The new default is the US1 endpoint, `https://api.datadoghq.com`.

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): required `external_user` property addedNo action needed
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): required `external_user` property addedAction required
  * Connect client-secret callers must include a non-empty `external_user` when creating a key. Management-key callers should continue to omit this Connect-only field.
* [`GET /keys/{hash}`](api/api-reference/api-keys/get-a-single-api-key.md): required `external_user` property addedNo action needed
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): required `external_user` property addedNo action needed

## New endpoints

* [`GET /containers/{session_id}/files`](api/api-reference/containers/list-container-files.md): List container files
* [`GET /containers/{session_id}/files/{file_id}`](api/api-reference/containers/retrieve-a-container-file.md): Retrieve a container file
* [`GET /containers/{session_id}/files/{file_id}/content`](api/api-reference/containers/download-container-file-content.md): Download container file content
* [`GET /containers/{container_id}/files`](api/api-reference/containers/list-container-files.md): List container files
* [`GET /containers/{container_id}/files/{file_id}`](api/api-reference/containers/retrieve-a-container-file.md): Retrieve a container file
* [`GET /containers/{container_id}/files/{file_id}/content`](api/api-reference/containers/download-container-file-content.md): Download container file content

## Modified endpoints

* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): request schema updated
* [`GET /keys`](api/api-reference/api-keys/list-api-keys.md): response schema updated
* [`POST /keys`](api/api-reference/api-keys/create-a-new-api-key.md): description updated; request schema updated; response schema updated
* [`GET /keys/{hash}`](api/api-reference/api-keys/get-a-single-api-key.md): response schema updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): response schema updated
* [`DELETE /keys/{hash}`](api/api-reference/api-keys/delete-an-api-key.md): description updated
* [`PATCH /keys/{hash}`](api/api-reference/api-keys/update-an-api-key.md): description updated

## New schemas

* `ContainerFile`
  * Used by [`GET /containers/{session_id}/files`](api/api-reference/containers/list-container-files.md), [`GET /containers/{session_id}/files/{file_id}`](api/api-reference/containers/retrieve-a-container-file.md)
* `ContainerFileListResponse`
  * Used by [`GET /containers/{session_id}/files`](api/api-reference/containers/list-container-files.md)

## Modified schemas

* `ContainerFile`: description updated; example modified
  * Used by [`GET /containers/{container_id}/files`](api/api-reference/containers/list-container-files.md), [`GET /containers/{container_id}/files/{file_id}`](api/api-reference/containers/retrieve-a-container-file.md)
* `ContainerReferenceEnvironment`: description updated; example modified

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `MessagesBashToolResultBlock`: new property `container_id`; new property `files`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `MessagesShellToolResultBlock`: new property `container_id`; new property `files`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ORAnthropicBashToolResult`: new property `container_id`; new property `files`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ORAnthropicShellToolResult`: new property `container_id`; new property `files`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `OutputBashServerToolItem`: new property `container_id`; new property `files`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputShellCallOutputItem`: new property `container_id`; new property `files`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputShellServerToolItem`: new property `container_id`; new property `files`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ObservabilityDatadogDestination`: example modified; property `url` updated

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `PricingOverride`: new property `utc_days`

  **6 endpoints using this schema**

  * [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md)
  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)
  * [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md)
  * [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)

**August 22, 2026**

## New schemas

* `ToolSearchServerTool`

  **4 endpoints using this schema**

  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ToolSearchServerToolConfig`

  **4 endpoints using this schema**

  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `AdditionalToolsItem`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ResponsesRequest`: new union variant added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 21, 2026**

## Modified endpoints

* [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md): description updated
* [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md): description updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New response codes

* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): now returns `408`
* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): now returns `413`

## Modified schemas

* `CreateBYOKKeyRequest`: new property `allowed_api_key_hashes`
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `UpdateBYOKKeyRequest`: new property `allowed_api_key_hashes`
  * Used by [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `makora`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**August 20, 2026**

## Breaking changes

* [`GET /analytics/meta`](api/api-reference/analytics/get-available-analytics-metrics-and-dimensions.md): tags `beta.Analytics` property removedNo action needed
* [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md): tags `beta.Analytics` property removedNo action needed
* \$.tags: beta.Analytics object removedNo action needed

## Modified endpoints

* [`GET /analytics/meta`](api/api-reference/analytics/get-available-analytics-metrics-and-dimensions.md): tags property\_added
* [`POST /analytics/query`](api/api-reference/analytics/query-analytics-data.md): tags property\_added
* [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md): description updated

## Modified schemas

* `ReasoningFormat`: enum property\_added

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CreateGuardrailRequest`: description updated
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`: description updated

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)

**August 19, 2026**

## Breaking changes

* `AdvisorNestedTool`: schema object removedAction required
  * Remove `tools` and `max_tool_calls` from advisor tool configuration. Advisors no longer run nested tool-calling loops.
* `AdvisorServerToolConfig`: properties `max_tool_calls` object removedAction required

  * Remove `tools` and `max_tool_calls` from advisor tool configuration. Advisors no longer run nested tool-calling loops.

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AdvisorServerToolConfig`: properties `tools` object removedAction required

  * Remove `tools` and `max_tool_calls` from advisor tool configuration. Advisors no longer run nested tool-calling loops.

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `VideoModel`: required `creativity` property addedNo action needed
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `VideoModel`: required `upscale_factor` property addedNo action needed
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `CustomToolCallItem`: properties `call_id` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: properties `id` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: properties `input` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: properties `name` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: properties `namespace` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: properties `type` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `call_id` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `input` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `name` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: required `type` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## New capabilities

* BYOK API: manage credential restrictions (`allowed_models`, `allowed_user_ids`, `allowed_api_key_hashes`) via create/update. See the [BYOK guide](guides/overview/auth/byok.md#managing-filters-via-the-management-api) for examples and validation rules.

## New schemas

* `FailableToolCallStatus`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `AdvisorServerToolConfig`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AdvisorServerTool_OpenRouter`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `VideoGenerationRequest`: new property `creativity`; new property `upscale_factor`
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `VideoModel`: new property `creativity`; new property `upscale_factor`
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `OutputAdvisorServerToolItem`: description updated; \$ref modified
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputSubagentServerToolItem`: description updated; \$ref modified
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CustomToolCallItem`: allOf object\_added; type property\_removed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 18, 2026**

## Breaking changes

* [`POST /analytics/query`](https://openrouter.ai/docs/api/api-reference/betaanalytics/query-analytics-data): maxItems `10` modifiedAction required
  * Limit `classifier_dimensions.dimension_names` to at most two entries. Split requests that previously queried three or more classifier dimensions.

## Modified endpoints

* [`POST /analytics/query`](https://openrouter.ai/docs/api/api-reference/betaanalytics/query-analytics-data): description updated

## Modified schemas

* `ProviderOptions`: new property `anthropic/2`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**August 17, 2026**

## Breaking changes

* spec: string modifiedNo action needed
* `OutputBashServerToolItem`: type `string` modifiedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): type `string` modifiedNo action needed

## Modified endpoints

* [`DELETE /workspaces/{id}`](api/api-reference/workspaces/delete-a-workspace.md): description updated

## New schemas

* `OutputShellServerToolItem`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ShellCallOutputContent`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `OpenAIResponseFunctionToolCall`: new property `subagent_id`; new property `subagent_items`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputSubagentServerToolItem`: new property `call_id`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SubagentReasoning`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `SubagentServerToolConfig`: new property `inherit_functions`; new property `inherited_function_names`; description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputFilesServerToolItem`: new property `arguments`; new property `call_id`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItems`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputShellCallItem`: new property `arguments`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputShellCallOutputItem`: \$ref modified
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ShellCallItem`: new property `arguments`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ShellCallOutputItem`: example modified; \$ref modified
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `amazon-bedrock/claude-on-aws`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)

**August 14, 2026**

## Modified endpoints

* [`GET /datasets/app-rankings`](api/api-reference/datasets/top-apps-by-token-usage.md): description updated
* [`GET /datasets/rankings-daily`](api/api-reference/datasets/daily-token-totals-for-top-50-models.md): description updated
* [`GET /datasets/session-cost`](api/api-reference/datasets/cost-per-session-by-harness-and-model.md): description updated

## Modified schemas

* `AnthropicRefusalStopDetails`: enum property\_added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `OutputFusionServerToolItem`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 13, 2026**

## Breaking changes

* `MessagesErrorDetail`: schema object removedNo action needed
* `MessagesErrorResponse`: schema object removedNo action needed

## Modified endpoints

* [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md): response schema updated
* [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md): response schema updated; description updated
* [`DELETE /workspaces/{id}`](api/api-reference/workspaces/delete-a-workspace.md): description updated

## New schemas

* `AnthropicMessagesErrorResponse`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)

## Modified schemas

* `ImageGenerationRequest`: description updated
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `WebSearchMode`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 12, 2026**

## New endpoints

* [`GET /datasets/session-cost`](api/api-reference/datasets/cost-per-session-by-harness-and-model.md): Cost per session by harness and model

## Modified endpoints

* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md): description updated; parameter `region` updated
* [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md): description updated
* [`DELETE /workspaces/{id}`](api/api-reference/workspaces/delete-a-workspace.md): description updated; new parameter `confirm_default_settings_deletion`

## New schemas

* `SessionCostItem`
  * Used by [`GET /datasets/session-cost`](api/api-reference/datasets/cost-per-session-by-harness-and-model.md)
* `SessionCostMeta`
  * Used by [`GET /datasets/session-cost`](api/api-reference/datasets/cost-per-session-by-harness-and-model.md)
* `SessionCostResponse`
  * Used by [`GET /datasets/session-cost`](api/api-reference/datasets/cost-per-session-by-harness-and-model.md)

## Modified schemas

* `AutoBetaRouterPlugin`: description updated; maxItems property\_added; maxLength property\_added

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AutoRouterPlugin`: description updated; maxItems property\_added; maxLength property\_added

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 11, 2026**

## Breaking changes

* `UnifiedBenchmarksResponse`: discriminator `discriminator` object removedNo action needed
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `GenerationContentData`: required `error` property addedNo action needed
  * Used by [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md)

## Modified endpoints

* [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md):
  * description updated
  * new parameter `benchmark_type`
  * new parameter `include_run_config`
  * new parameter `search_engine`
  * new parameter `search_surface`
  * parameter `task_type` updated
* [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md): description updated; response schema updated
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New schemas

* `UnifiedBenchmarksSearchItem`
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `UnifiedBenchmarksSearchRunConfig`
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `GenerationContentError`
  * Used by [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md)
* `GenerationContentErrorAttempt`
  * Used by [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md)

## Modified schemas

* `OutputFusionServerToolItem`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchMode`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `MessagesStartEvent`: property `usage` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `UnifiedBenchmarksResponse`: new union variant added
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `GenerationContentData`: description updated; example modified; new property `error`
  * Used by [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md)
* `GenerationContentResponse`: example modified
  * Used by [`GET /generation/content`](api/api-reference/generations/get-stored-prompt-completion-and-error-content-for-a-generation.md)
* `AppRankingsResponse`: example modified
  * Used by [`GET /datasets/app-rankings`](api/api-reference/datasets/top-apps-by-token-usage.md)
* `RankingsDailyMeta`: example modified
  * Used by [`GET /datasets/app-rankings`](api/api-reference/datasets/top-apps-by-token-usage.md), [`GET /datasets/rankings-daily`](api/api-reference/datasets/daily-token-totals-for-top-50-models.md)
* `RankingsDailyResponse`: example modified
  * Used by [`GET /datasets/rankings-daily`](api/api-reference/datasets/daily-token-totals-for-top-50-models.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `databricks`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

**August 10, 2026**

## Breaking changes

* spec: additionalProperties object addedNo action needed
* `CodeInterpreterCallItem`: properties `code` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: properties `container_id` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: properties `id` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: properties `outputs` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: properties `status` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: properties `type` object removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: required `code` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: required `container_id` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: required `id` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: required `outputs` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: required `status` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: required `type` property removedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemWebSearchCall`: additionalProperties `additionalProperties` object addedNo action needed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): properties `code` object removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): properties `container_id` object removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): properties `id` object removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): properties `outputs` object removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): properties `status` object removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): properties `type` object removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): required `code` property removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): required `container_id` property removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): required `id` property removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): required `outputs` property removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): required `status` property removedNo action needed
* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): required `type` property removedNo action needed

## Modified endpoints

* [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md): request schema updated

## New schemas

* `CodeInterpreterCallCodeDeltaEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallCodeDoneEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallCompletedEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallInProgressEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallInterpretingEvent`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterFileOutput`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterImageOutput`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterLogsOutput`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponsesCodeInterpreterCallCodeDelta`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponsesCodeInterpreterCallCodeDone`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponsesCodeInterpreterCallCompleted`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponsesCodeInterpreterCallInProgress`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OpenAIResponsesCodeInterpreterCallInterpreting`
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemCodeInterpreterCall`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `AutoBetaRouterPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AutoRouterPlugin`: example modified; description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `BaseResponsesResult`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `CodeInterpreterCallItem`: allOf object\_added; type property\_removed
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemAddedEvent`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputItemDoneEvent`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `StreamEvents`: new union variant added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 9, 2026**

## Modified schemas

* `FusionServerToolConfig`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 8, 2026**

## Modified schemas

* `VideoModel`: enum property\_added
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `FusionServerToolConfig`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 7, 2026**

## Breaking changes

* `BYOKKey`: type `string` modifiedAction required

  * Allow `workspace_id` to be `null` in BYOK responses. A null value identifies a global credential that is usable across every workspace; do not substitute the default workspace.

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `Guardrail`: type `string` modifiedAction required

  * Allow `workspace_id` to be `null` in guardrail responses. A null value identifies an unscoped legacy guardrail; it does not mean the default workspace or every workspace.

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `ObservabilityArizeDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityArizeDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityArizeDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: required `broadcast_generation_cost` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: required `broadcast_generation_identity` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`: required `broadcast_generation_request_context` property addedNo action needed

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): required `broadcast_generation_cost` property addedNo action needed
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): required `broadcast_generation_identity` property addedNo action needed
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): required `broadcast_generation_request_context` property addedNo action needed

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): description updated
* [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md): description updated
* [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md): response schema updated
* [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md): response schema updated
* [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md): response schema updated
* [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md): response schema updated

## New response codes

* [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md): now returns `403`

## New schemas

* `WebSearchMode`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

## Modified schemas

* `BYOKKey`: description updated

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateBYOKKeyRequest`: description updated
  * Used by [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `CreateGuardrailRequest`: description updated
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `CreateObservabilityDestinationRequest`: new property `broadcast_generation_cost`; new property `broadcast_generation_identity`; new property `broadcast_generation_request_context`
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `CreateObservabilityDestinationResponse`: example modified
  * Used by [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `FusionPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionServerToolConfig`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `GetObservabilityDestinationResponse`: example modified
  * Used by [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
* `Guardrail`: description updated

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `ListObservabilityDestinationsResponse`: example modified
  * Used by [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
* `ObservabilityArizeDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityBraintrustDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityClickhouseDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDatadogDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityDestination`: example modified

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityGrafanaDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangfuseDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityLangsmithDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityNewrelicDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOpikDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityOtelCollectorDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityPosthogDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityRampDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityS3Destination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySentryDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilitySnowflakeDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWeaveDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `ObservabilityWebhookDestination`:

  * example modified
  * new property `broadcast_generation_cost`
  * new property `broadcast_generation_identity`
  * new property `broadcast_generation_request_context`

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `UpdateObservabilityDestinationRequest`: new property `broadcast_generation_cost`; new property `broadcast_generation_identity`; new property `broadcast_generation_request_context`
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
* `UpdateObservabilityDestinationResponse`: example modified
  * Used by [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
* `ChatWebSearchShorthand`: new property `mode`
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `InputReference`: description updated
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `Legacy_WebSearchServerTool`: new property `mode`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `Preview_20250311_WebSearchServerTool`: new property `mode`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `Preview_WebSearchServerTool`: new property `mode`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `VideoGenerationRequest`: description updated
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `WebSearchConfig`: new property `mode`

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `WebSearchPlugin`: new property `mode`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchServerTool`: new property `mode`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchServerToolConfig`: new property `mode`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 5, 2026**

## Modified endpoints

* [`POST /files`](api/api-reference/files/upload-a-file.md): description updated

## Modified schemas

* `FilesServerTool`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**August 4, 2026**

## Modified endpoints

* [`POST /analytics/query`](https://openrouter.ai/docs/api/api-reference/betaanalytics/query-analytics-data): request schema updated

## New response codes

* [`DELETE /workspaces/{id}/budgets/{interval}`](api/api-reference/workspaces/delete-a-workspace-budget.md): now returns `400`

## New schemas

* `GetWorkspaceBudgetResponse`
  * Used by [`GET /workspaces/{id}/budgets/{interval}`](api/api-reference/workspaces/get-a-workspace-budget.md)
* `MessagesBashToolResultBlock`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `MessagesShellToolResultBlock`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ORAnthropicBashToolResult`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ORAnthropicShellToolResult`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)

## Modified schemas

* `ObservabilitySnowflakeDestination`: property `account` updated

  **4 endpoints using this schema**

  * [`GET /observability/destinations`](api/api-reference/observability/list-observability-destinations.md)
  * [`GET /observability/destinations/{id}`](api/api-reference/observability/get-an-observability-destination.md)
  * [`PATCH /observability/destinations/{id}`](api/api-reference/observability/update-an-observability-destination.md)
  * [`POST /observability/destinations`](api/api-reference/observability/create-an-observability-destination.md)
* `MessagesContentBlockStartEvent`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `MessagesRequest`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ORAnthropicContentBlock`: new union variant added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)

**August 3, 2026**

## Breaking changes

* `GenerationResponse`: required `workspace_id` property addedNo action needed
  * No action required for existing consumers. Generation responses now include `workspace_id`, the ID of the workspace the generation belongs to.
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)

## Modified endpoints

* [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md):
  * x-speakeasy-max-method-params object\_added
  * description updated
  * new parameter `group_by`
  * new parameter `workspace_id`
* [`POST /analytics/query`](https://openrouter.ai/docs/api/api-reference/betaanalytics/query-analytics-data): description updated
* [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md): response schema updated

## New schemas

* `SpeechInputReference`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceAudio`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceAudioInput`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `SpeechInputReferenceText`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

## Modified schemas

* `ActivityItem`: new property `workspace_id`
  * Used by [`GET /activity`](api/api-reference/analytics/get-user-activity-grouped-by-endpoint.md)
* `GenerationResponse`: example modified; new property `workspace_id`
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `PublicEndpoint`: example modified; new property `supports_voice_cloning`
  * Used by [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md), [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
* `SpeechRequest`: new property `input_references`
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

**August 1, 2026**

## Modified endpoints

* [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md): description updated
* [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md): description updated

## Modified schemas

* `Workspace`: description updated

  **4 endpoints using this schema**

  * [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md)
  * [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md)
  * [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
  * [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)

**July 31, 2026**

**July 30, 2026**

## Breaking changes

* `SpeechRequest`: required `voice` property removedNo action needed
  * No action required for existing consumers. `voice` is now optional; requests that send it are unaffected.
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)

## New endpoints

* [`GET /scim/group-mappings`](api/api-reference/scim/list-scim-group-mappings.md): List SCIM group mappings
* [`POST /scim/group-mappings`](api/api-reference/scim/create-a-scim-group-mapping.md): Create a SCIM group mapping
* [`GET /scim/group-mappings/{id}`](api/api-reference/scim/get-a-scim-group-mapping.md): Get a SCIM group mapping
* [`PATCH /scim/group-mappings/{id}`](api/api-reference/scim/update-a-scim-group-mapping.md): Update a SCIM group mapping
* [`DELETE /scim/group-mappings/{id}`](api/api-reference/scim/delete-a-scim-group-mapping.md): Delete a SCIM group mapping
* [`GET /scim/groups`](api/api-reference/scim/list-scim-groups.md): List SCIM groups

## Modified endpoints

* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## New schemas

* `CreateScimGroupMappingRequest`
  * Used by [`POST /scim/group-mappings`](api/api-reference/scim/create-a-scim-group-mapping.md)
* `CreateScimGroupMappingResponse`
  * Used by [`POST /scim/group-mappings`](api/api-reference/scim/create-a-scim-group-mapping.md)
* `DeleteScimGroupMappingResponse`
  * Used by [`DELETE /scim/group-mappings/{id}`](api/api-reference/scim/delete-a-scim-group-mapping.md)
* `GetScimGroupMappingResponse`
  * Used by [`GET /scim/group-mappings/{id}`](api/api-reference/scim/get-a-scim-group-mapping.md)
* `ListScimGroupMappingsResponse`
  * Used by [`GET /scim/group-mappings`](api/api-reference/scim/list-scim-group-mappings.md)
* `ListScimGroupsResponse`
  * Used by [`GET /scim/groups`](api/api-reference/scim/list-scim-groups.md)
* `ScimGroup`
  * Used by [`GET /scim/groups`](api/api-reference/scim/list-scim-groups.md)
* `ScimGroupMapping`

  **4 endpoints using this schema**

  * [`GET /scim/group-mappings`](api/api-reference/scim/list-scim-group-mappings.md)
  * [`GET /scim/group-mappings/{id}`](api/api-reference/scim/get-a-scim-group-mapping.md)
  * [`PATCH /scim/group-mappings/{id}`](api/api-reference/scim/update-a-scim-group-mapping.md)
  * [`POST /scim/group-mappings`](api/api-reference/scim/create-a-scim-group-mapping.md)
* `UpdateScimGroupMappingRequest`
  * Used by [`PATCH /scim/group-mappings/{id}`](api/api-reference/scim/update-a-scim-group-mapping.md)
* `UpdateScimGroupMappingResponse`
  * Used by [`PATCH /scim/group-mappings/{id}`](api/api-reference/scim/update-a-scim-group-mapping.md)

## Modified schemas

* `VideoGenerationRequest`: enum property\_added
  * Used by [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `VideoModel`: enum property\_added
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)
* `SpeechRequest`: minLength property\_added
  * Used by [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)
* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `thinkingmachines`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `ChatRequest`: description updated; enum property\_added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `ResponsesErrorField`: enum property\_added
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ResponsesRequest`: description updated; enum property\_added
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)

**July 29, 2026**

## Breaking changes

* `FileMetadata`: schema object removedNo action needed
* `FileDeleteResponse`: discriminator `discriminator` object addedAction required
  * HTTP clients: no change. Requests without a vendor SDK still get the OpenRouter shape (`_shape: "openrouter"`) with the same fields as before. Typed SDK clients: this response type is now a union discriminated by `_shape`. In the TypeScript SDK, the field is named `shape`, so check `shape === "openrouter"` before reading OpenRouter fields such as `id` and `type`.
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileDeleteResponse`: properties `id` object removedNo action needed
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileDeleteResponse`: properties `type` object removedNo action needed
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileDeleteResponse`: required `id` property removedNo action needed
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileDeleteResponse`: required `type` property removedNo action needed
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileListResponse`: discriminator `discriminator` object addedAction required
  * HTTP clients: no change. Requests without a vendor SDK still get the OpenRouter shape (`_shape: "openrouter"`) with the same fields as before. Typed SDK clients: this response type is now a union discriminated by `_shape`. In the TypeScript SDK, the field is named `shape`, so check `shape === "openrouter"` before reading OpenRouter fields such as `cursor`.
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: properties `cursor` object removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: properties `data` object removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: properties `first_id` object removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: properties `has_more` object removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: properties `last_id` object removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: required `cursor` property removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: required `data` property removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: required `first_id` property removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: required `has_more` property removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileListResponse`: required `last_id` property removedNo action needed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)

## Modified endpoints

* [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md): description updated; parameter `source` updated; response schema updated
* [`GET /files`](api/api-reference/files/list-files.md):
  * new parameter `after`
  * new parameter `after_id`
  * new parameter `before_id`
  * new parameter `order`
  * new parameter `provider`
* [`POST /files`](api/api-reference/files/upload-a-file.md): new parameter `provider`; response schema updated
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): new parameter `provider`
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): new parameter `provider`; response schema updated
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): new parameter `provider`
* [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md): response schema updated
* [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md): response schema updated
* [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md): response schema updated
* [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md): response schema updated
* [`GET /workspaces/{id}/budgets`](api/api-reference/workspaces/list-workspace-budgets.md): response schema updated
* [`PUT /workspaces/{id}/budgets/{interval}`](api/api-reference/workspaces/create-or-update-a-workspace-budget.md): description updated; request schema updated; response schema updated

## New response codes

* [`GET /files`](api/api-reference/files/list-files.md): now returns `403`
* [`GET /files`](api/api-reference/files/list-files.md): now returns `502`
* [`GET /files`](api/api-reference/files/list-files.md): now returns `503`
* [`POST /files`](api/api-reference/files/upload-a-file.md): now returns `502`
* [`POST /files`](api/api-reference/files/upload-a-file.md): now returns `503`
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): now returns `403`
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): now returns `502`
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): now returns `503`
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): now returns `403`
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): now returns `502`
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): now returns `503`
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): now returns `403`
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): now returns `502`
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): now returns `503`

## New schemas

* `UnifiedBenchmarksORItem`
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `AnthropicFile`
  * Used by [`GET /files`](api/api-reference/files/list-files.md), [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md), [`POST /files`](api/api-reference/files/upload-a-file.md)
* `AnthropicFileDeleted`
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `AnthropicFileList`
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileProvider`

  **5 endpoints using this schema**

  * [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
  * [`GET /files`](api/api-reference/files/list-files.md)
  * [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md)
  * [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md)
  * [`POST /files`](api/api-reference/files/upload-a-file.md)
* `FileResponse`
  * Used by [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md), [`POST /files`](api/api-reference/files/upload-a-file.md)
* `OpenAIFile`
  * Used by [`GET /files`](api/api-reference/files/list-files.md), [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md), [`POST /files`](api/api-reference/files/upload-a-file.md)
* `OpenAIFileDeleted`
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `OpenAIFileList`
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `OpenRouterFile`
  * Used by [`GET /files`](api/api-reference/files/list-files.md), [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md), [`POST /files`](api/api-reference/files/upload-a-file.md)
* `OpenRouterFileDeleted`
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `OpenRouterFileList`
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `ModelAliasTarget`

  **4 endpoints using this schema**

  * [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md)
  * [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)
  * [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md)
  * [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md)

## Modified schemas

* `UnifiedBenchmarksMeta`: enum property\_added
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `UnifiedBenchmarksResponse`: example modified; new union variant added
  * Used by [`GET /benchmarks`](api/api-reference/benchmarks/list-benchmarks.md)
* `FileDeleteResponse`:
  * description updated
  * example modified
  * new union variant added
  * type property\_removed
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileListResponse`:
  * description updated
  * example modified
  * new union variant added
  * type property\_removed
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `CreateWorkspaceResponse`: example modified
  * Used by [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `GetWorkspaceResponse`: example modified
  * Used by [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md)
* `ListWorkspaceBudgetsResponse`: example modified; new property `include_byok_in_budgets`
  * Used by [`GET /workspaces/{id}/budgets`](api/api-reference/workspaces/list-workspace-budgets.md)
* `ListWorkspacesResponse`: example modified
  * Used by [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md)
* `Model`: new property `alias_target`

  **4 endpoints using this schema**

  * [`GET /embeddings/models`](api/api-reference/embeddings/list-all-embeddings-models.md)
  * [`GET /model/{author}/{slug}`](api/api-reference/models/get-a-model-by-its-slug.md)
  * [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md)
  * [`GET /models/user`](api/api-reference/models/list-models-filtered-by-user-provider-preferences-privacy-settings-and-guardrails.md)
* `UpdateWorkspaceResponse`: example modified
  * Used by [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
* `UpsertWorkspaceBudgetRequest`: example modified; new property `include_byok_in_budgets`
  * Used by [`PUT /workspaces/{id}/budgets/{interval}`](api/api-reference/workspaces/create-or-update-a-workspace-budget.md)
* `UpsertWorkspaceBudgetResponse`: example modified; new property `include_byok_in_budgets`
  * Used by [`PUT /workspaces/{id}/budgets/{interval}`](api/api-reference/workspaces/create-or-update-a-workspace-budget.md)
* `Workspace`: example modified; new property `include_byok_in_budgets`

  **4 endpoints using this schema**

  * [`GET /workspaces`](api/api-reference/workspaces/list-workspaces.md)
  * [`GET /workspaces/{id}`](api/api-reference/workspaces/get-a-workspace.md)
  * [`PATCH /workspaces/{id}`](api/api-reference/workspaces/update-a-workspace.md)
  * [`POST /workspaces`](api/api-reference/workspaces/create-a-workspace.md)
* `AutoBetaRouterPlugin`: example modified; new property `excluded_models`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AutoRouterPlugin`: example modified; new property `excluded_models`

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `VideoModel`: enum property\_added
  * Used by [`GET /videos/models`](api/api-reference/video-generation/list-all-video-generation-models.md)

**July 28, 2026**

## Breaking changes

* `FusionCallAnalysisInProgressEvent`: required `analyst_model` property addedNo action needed
  * **No action required for existing consumers.** `analyst_model` replaces `judge_model` in this streaming event; `judge_model` is retained as a deprecated alias that always carries the same value.
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* \$.tags: responses object removedNo action needed
  * **No action required.** The `responses` OpenAPI tag was renamed to `Responses` for consistent Title Case across the API Reference. This is a documentation-grouping change only: `POST /api/v1/responses` and its schemas are unchanged, SDK namespaces are unchanged (`client.responses.send()` in TypeScript and Python, `Sdk.Responses.Send()` in Go), and endpoint documentation URLs are unchanged.

## Modified endpoints

* [`GET /files`](api/api-reference/files/list-files.md): parameter `cursor` updated; response schema updated
* [`POST /files`](api/api-reference/files/upload-a-file.md): response schema updated
* [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md): parameter `file_id` updated; response schema updated
* [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md): parameter `file_id` updated; response schema updated
* [`GET /files/{file_id}/content`](api/api-reference/files/download-file-content.md): parameter `file_id` updated

## Modified schemas

* `FusionAnalysisResult`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionCallAnalysisCompletedEvent`: description updated
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionCallAnalysisInProgressEvent`:
  * description updated
  * example modified
  * new property `analyst_model`
  * property `judge_model` deprecated (alias of `analyst_model`, kept for existing consumers)
  * Used by [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionPlugin`: description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionServerToolConfig`: description updated; property `effort` updated; property `max_tokens` updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionServerTool_OpenRouter`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `FusionSource`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `OutputFusionServerToolItem`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ChatWebSearchShorthand`: description updated
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `WebSearchConfig`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `WebSearchDomainFilter`: example modified; new property `blocked_domains`
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `WebSearchServerToolConfig`: description updated
  * Used by [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md), [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AnthropicFileDocumentSource`: example modified
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `FileDeleteResponse`: example modified
  * Used by [`DELETE /files/{file_id}`](api/api-reference/files/delete-a-file.md)
* `FileListResponse`: example modified
  * Used by [`GET /files`](api/api-reference/files/list-files.md)
* `FileMetadata`: example modified
  * Used by [`GET /files`](api/api-reference/files/list-files.md), [`GET /files/{file_id}`](api/api-reference/files/get-file-metadata.md), [`POST /files`](api/api-reference/files/upload-a-file.md)
* `GenerationResponse`: property `data_region` updated
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `CreateGuardrailRequest`: new property `enable_free_model_publication`; new property `enable_free_model_training`; new property `enable_paid_model_training`
  * Used by [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `Guardrail`:

  * example modified
  * new property `enable_free_model_publication`
  * new property `enable_free_model_training`
  * new property `enable_paid_model_training`

  **4 endpoints using this schema**

  * [`GET /guardrails`](api/api-reference/guardrails/list-guardrails.md)
  * [`GET /guardrails/{id}`](api/api-reference/guardrails/get-a-guardrail.md)
  * [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
  * [`POST /guardrails`](api/api-reference/guardrails/create-a-guardrail.md)
* `UpdateGuardrailRequest`: new property `enable_free_model_publication`; new property `enable_free_model_training`; new property `enable_paid_model_training`
  * Used by [`PATCH /guardrails/{id}`](api/api-reference/guardrails/update-a-guardrail.md)
* `AutoBetaRouterPlugin`:

  * example modified
  * new property `cost_tier`
  * deprecated property\_added
  * description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `AutoRouterPlugin`:

  * example modified
  * new property `cost_tier`
  * deprecated property\_added
  * description updated

  **6 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**July 27, 2026**

## Modified endpoints

* [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md): request schema updated

## Modified schemas

* `Quantization`: enum property\_added

  **10 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ReasoningFormat`: enum property\_added

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)

**July 25, 2026**

## Breaking changes

* [`POST /responses`](api/api-reference/responses/create-a-response.md): tags `beta.responses` property removedNo action needed
  * **Migration: no action for HTTP clients.** The Responses API is now GA. `beta.responses` was an OpenAPI grouping tag and SDK namespace, never a URL. `POST /api/v1/responses` and its request and response schemas are unchanged, so raw HTTP callers and OpenAI-compatible clients (including the OpenAI Agents SDK) need no changes. The endpoint now appears under **Responses** instead of **Beta responses** in the API Reference.
  * **Migration for SDK users: optional until sunset.** The canonical namespace is now `responses`, with `client.responses.send()` (TypeScript, Python) and `client.Responses.Send()` (Go). The `beta.responses` namespace, and TypeScript's `betaResponsesSend` standalone function, keep working as deprecated aliases; their removal will be announced here with a sunset date before it ships.
* \$.tags: beta.responses object removedNo action needed
  * Same change as above at the specification level: the `beta.responses` tag definition is gone from `$.tags`.

## Modified endpoints

* [`POST /responses`](api/api-reference/responses/create-a-response.md): tags property\_added
* [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md): parameter `provider` updated

## Modified schemas

* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `claude-on-aws`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `BYOKProviderSlug`: enum property\_added

  **4 endpoints using this schema**

  * [`GET /byok`](api/api-reference/byok/list-byok-provider-credentials.md)
  * [`GET /byok/{id}`](api/api-reference/byok/get-a-byok-provider-credential.md)
  * [`PATCH /byok/{id}`](api/api-reference/byok/update-a-byok-provider-credential.md)
  * [`POST /byok`](api/api-reference/byok/create-a-byok-provider-credential.md)

**July 24, 2026**

## Modified schemas

* `MessagesStartEvent`: property `provider` updated
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `ProviderName`: enum property\_added

  **11 endpoints using this schema**

  * [`GET /endpoints/zdr`](api/api-reference/endpoints/preview-the-impact-of-zdr-on-the-available-endpoints.md)
  * [`GET /models/{author}/{slug}/endpoints`](api/api-reference/endpoints/list-all-endpoints-for-a-model.md)
  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /embeddings`](api/api-reference/embeddings/submit-an-embedding-request.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /rerank`](api/api-reference/rerank/submit-a-rerank-request.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ProviderOptions`: new property `voyageai`

  **4 endpoints using this schema**

  * [`POST /audio/speech`](api/api-reference/tts/create-speech.md)
  * [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
  * [`POST /images`](api/api-reference/images/generate-an-image.md)
  * [`POST /videos`](api/api-reference/video-generation/submit-a-video-generation-request.md)
* `ProviderResponse`: enum property\_added
  * Used by [`GET /generation`](api/api-reference/generations/get-request-&-usage-metadata-for-a-generation.md)
* `AnthropicCompactionBlock`: new property `encrypted_content`
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)
* `MessagesToolAdditionBlock`: new property `cache_control`; new union variant added; type property\_removed
  * `tool` widened from a single `tool_reference` object to a union of `tool_reference`, `mcp_tool_reference` (`name` + `server_name`) and `mcp_toolset_reference` (`server_name`). The `tool_reference` variant is unchanged, so existing `{ "type": "tool_reference", "name": "…" }` payloads stay valid. The `name` and `type` properties moved into that variant rather than being removed.
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `MessagesToolRemovalBlock`: new property `cache_control`; new union variant added; type property\_removed
  * `tool` widened the same way as `MessagesToolAdditionBlock`; existing `tool_reference` payloads stay valid.
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md), [`POST /presets/{slug}/messages`](api/api-reference/presets/create-a-preset-from-a-messages-request-body.md)
* `ORAnthropicStopReason`: enum property\_added
  * Used by [`POST /messages`](api/api-reference/anthropic-messages/create-a-message.md)

**July 8, 2026**

## New schemas

* `ImageGenTextChunkEvent`
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)

## Modified schemas

* `ImageStreamingResponse`: new union variant added
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)

**July 7, 2026**

## Modified endpoints

* [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md): description updated; request body now accepts `multipart/form-data`
* [`GET /datasets/rankings-daily`](api/api-reference/datasets/daily-token-totals-for-top-50-models.md):
  * description updated
  * new parameter `category`
  * new parameter `context_bucket`
  * new parameter `language_type`
  * new parameter `modality`
  * new parameter `period`
* [`GET /models`](api/api-reference/models/list-all-models-and-their-properties.md):
  * new parameter `max_age_days`
  * new parameter `max_agentic_index`
  * new parameter `max_coding_index`
  * new parameter `max_intelligence_index`
  * new parameter `max_output_price`
  * new parameter `max_tool_success_rate`
  * new parameter `min_age_days`
  * new parameter `min_agentic_index`
  * new parameter `min_coding_index`
  * new parameter `min_intelligence_index`
  * new parameter `min_output_price`
  * new parameter `min_tool_success_rate`
  * description updated
  * parameter `sort` updated

## New response codes

* [`POST /images`](api/api-reference/images/generate-an-image.md): now returns `413`

## New schemas

* `STTSegment`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTTimestampGranularity`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTWord`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)

## Modified schemas

* `ChatFunctionTool`: new union variant added
  * Used by [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md), [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
* `FusionServerToolConfig`: description updated

  **4 endpoints using this schema**

  * [`POST /chat/completions`](api/api-reference/chat/create-a-chat-completion.md)
  * [`POST /presets/{slug}/chat/completions`](api/api-reference/presets/create-a-preset-from-a-chat-completions-request-body.md)
  * [`POST /presets/{slug}/responses`](api/api-reference/presets/create-a-preset-from-a-responses-request-body.md)
  * [`POST /responses`](api/api-reference/responses/create-a-response.md)
* `ImageGenCompletedEvent`: description updated; example modified
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `ImageGenerationResponse`: property `media_type` updated
  * Used by [`POST /images`](api/api-reference/images/generate-an-image.md)
* `STTRequest`: new property `response_format`; new property `timestamp_granularities`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)
* `STTResponse`:
  * new property `duration`
  * new property `language`
  * new property `segments`
  * new property `task`
  * new property `words`
  * Used by [`POST /audio/transcriptions`](api/api-reference/stt/create-transcription.md)

**July 3, 2026**

## New endpoints

* [`GET /workspaces/{id}/members`](api/api-reference/workspaces/list-workspace-members.md): List workspace members

## New schemas

* `ListWorkspaceMembersResponse`
  * Used by [`GET /workspaces/{id}/members`](api/api-reference/workspaces/list-workspace-members.md)
