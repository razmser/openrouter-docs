> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Get a moderation policy

> Get a moderation policy with its member and API key assignments. [Management key](../../../guides/overview/auth/management-api-keys.md) required.



## OpenAPI

````yaml /openapi/openapi.yaml get /guardrails/policies/moderation/{id}
openapi: 3.1.0
info:
  contact:
    email: support@openrouter.ai
    name: OpenRouter Support
    url: https://openrouter.ai/docs
  description: OpenAI-compatible API with additional OpenRouter features
  license:
    name: MIT
    url: https://opensource.org/licenses/MIT
  title: OpenRouter API
  version: 1.0.0
servers:
  - description: Production server
    url: https://openrouter.ai/api/v1
    x-speakeasy-server-id: production
security:
  - apiKey: []
tags:
  - description: API key management endpoints
    name: API Keys
  - description: Analytics and usage endpoints
    name: Analytics
  - description: Anthropic Messages endpoints
    name: Anthropic Messages
  - description: BYOK endpoints
    name: BYOK
  - description: >-
      Submit, list, poll, and delete asynchronous batches of inference requests.
      See https://openrouter.ai/docs/batch-quickstart.
    name: Batch
  - description: Benchmarks endpoints
    name: Benchmarks
  - description: Chat completion endpoints
    name: Chat
  - description: Task classification market-share endpoints
    name: Classifications
  - description: Containers endpoints
    name: Containers
  - description: Credit management endpoints
    name: Credits
  - description: >-
      Public OpenRouter usage datasets. Data returned by these endpoints is
      licensed under CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/):
      reuse and republish it, including commercially, with attribution to
      OpenRouter.
    name: Datasets
  - description: Text embedding endpoints
    name: Embeddings
  - description: Endpoint information
    name: Endpoints
  - description: External Users endpoints
    name: External Users
  - description: Files endpoints
    name: Files
  - description: Generation history endpoints
    name: Generations
  - description: Guardrail Policies endpoints
    name: Guardrail Policies
  - description: Guardrails endpoints
    name: Guardrails
  - description: Images endpoints
    name: Images
  - description: Model information endpoints
    name: Models
  - description: OAuth authentication endpoints
    name: OAuth
  - description: Observability endpoints
    name: Observability
  - description: Organization endpoints
    name: Organization
  - description: Presets endpoints
    name: Presets
  - description: Private Endpoints endpoints
    name: Private Endpoints
  - description: Private Providers endpoints
    name: Private Providers
  - description: Provider information endpoints
    name: Providers
  - description: Rerank endpoints
    name: Rerank
  - description: OpenAI-compatible Responses API endpoints
    name: Responses
  - description: >-
      Management endpoints for SCIM group-to-workspace mappings, authenticated
      with a management key. These are not the SCIM 2.0 connector endpoints for
      your identity provider. In your identity provider, enter the SCIM endpoint
      URL shown when you enable provisioning under Settings > Members > SCIM
      Mappings. See
      https://openrouter.ai/docs/guides/features/scim-mappings#set-up-provisioning.
    name: SCIM
  - description: Speech-to-text endpoints
    name: STT
    x-displayName: Transcriptions
  - description: >-
      System One endpoints for models such as Jev, compatible with the TypeSafe
      SDKs. See https://openrouter.ai/docs/guides/community/typesafe-sdk.
    name: SystemOne
    x-displayName: System One
  - description: Text-to-speech endpoints
    name: TTS
    x-displayName: Speech
  - description: >-
      The catalog of server tools OpenRouter runs on behalf of a model: accepted
      `tools[].type` spellings per API format, engines and pricing, and which
      endpoints run each tool natively. See
      https://openrouter.ai/docs/guides/features/server-tools.
    name: Tools
  - description: >-
      Store host-bound secrets for a workspace or for one intern. Scope is
      selected by the API key. Responses return metadata only, never secret
      values. See https://openrouter.ai/docs/guides/ori/vault.
    name: Vault
  - description: Video Generation endpoints
    name: Video Generation
  - description: Workspaces endpoints
    name: Workspaces
  - description: Alpha feature endpoints for Decisions requests
    name: alpha.decisions
  - description: Alpha feature endpoints for Extractions requests
    name: alpha.extractions
externalDocs:
  description: OpenRouter Documentation
  url: https://openrouter.ai/docs
paths:
  /guardrails/policies/moderation/{id}:
    get:
      tags:
        - Guardrail Policies
      summary: Get a moderation policy
      description: >-
        Get a moderation policy with its member and API key assignments.
        [Management key](/docs/guides/overview/auth/management-api-keys)
        required.
      operationId: getModerationPolicy
      parameters:
        - description: Policy ID
          in: path
          name: id
          required: true
          schema:
            description: Policy ID
            example: 550e8400-e29b-41d4-a716-446655440000
            format: uuid
            type: string
        - description: Workspace the policy belongs to
          in: query
          name: workspace_id
          required: true
          schema:
            description: Workspace the policy belongs to
            example: 0df9e665-d932-5740-b2c7-b52af166bc11
            format: uuid
            type: string
      responses:
        '200':
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ModerationGuardrailPolicyDetailResponse'
          description: moderation policy details
        '400':
          content:
            application/json:
              example:
                error:
                  code: 400
                  message: Invalid request parameters
              schema:
                $ref: '#/components/schemas/BadRequestResponse'
          description: Bad Request - Invalid request parameters or malformed input
        '401':
          content:
            application/json:
              example:
                error:
                  code: 401
                  message: Missing Authentication header
              schema:
                $ref: '#/components/schemas/UnauthorizedResponse'
          description: Unauthorized - Authentication required or invalid credentials
        '403':
          content:
            application/json:
              example:
                error:
                  code: 403
                  message: Only management keys can perform this operation
              schema:
                $ref: '#/components/schemas/ForbiddenResponse'
          description: Forbidden - Authentication successful but insufficient permissions
        '404':
          content:
            application/json:
              example:
                error:
                  code: 404
                  message: Resource not found
              schema:
                $ref: '#/components/schemas/NotFoundResponse'
          description: Not Found - Resource does not exist
        '500':
          content:
            application/json:
              example:
                error:
                  code: 500
                  message: Internal Server Error
              schema:
                $ref: '#/components/schemas/InternalServerResponse'
          description: Internal Server Error - Unexpected server error
components:
  schemas:
    ModerationGuardrailPolicyDetailResponse:
      properties:
        data:
          $ref: '#/components/schemas/ModerationGuardrailPolicyDetail'
      required:
        - data
      type: object
    BadRequestResponse:
      description: Bad Request - Invalid request parameters or malformed input
      example:
        error:
          code: 400
          message: Invalid request parameters
      properties:
        error:
          $ref: '#/components/schemas/BadRequestResponseErrorData'
        openrouter_metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
        user_id:
          type:
            - string
            - 'null'
      required:
        - error
      type: object
    UnauthorizedResponse:
      description: Unauthorized - Authentication required or invalid credentials
      example:
        error:
          code: 401
          message: Missing Authentication header
      properties:
        error:
          $ref: '#/components/schemas/UnauthorizedResponseErrorData'
        openrouter_metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
        user_id:
          type:
            - string
            - 'null'
      required:
        - error
      type: object
    ForbiddenResponse:
      description: Forbidden - Authentication successful but insufficient permissions
      example:
        error:
          code: 403
          message: Only management keys can perform this operation
      properties:
        error:
          $ref: '#/components/schemas/ForbiddenResponseErrorData'
        openrouter_metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
        user_id:
          type:
            - string
            - 'null'
      required:
        - error
      type: object
    NotFoundResponse:
      description: Not Found - Resource does not exist
      example:
        error:
          code: 404
          message: Resource not found
      properties:
        error:
          $ref: '#/components/schemas/NotFoundResponseErrorData'
        openrouter_metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
        user_id:
          type:
            - string
            - 'null'
      required:
        - error
      type: object
    InternalServerResponse:
      description: Internal Server Error - Unexpected server error
      example:
        error:
          code: 500
          message: Internal Server Error
      properties:
        error:
          $ref: '#/components/schemas/InternalServerResponseErrorData'
        openrouter_metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
        user_id:
          type:
            - string
            - 'null'
      required:
        - error
      type: object
    ModerationGuardrailPolicyDetail:
      properties:
        api_key_hashes:
          description: API key hashes
          example:
            - c56454edb818d6b14bc0d61c46025f1450b0f4012d12304ab40aacb519fcbc93
          items:
            maxLength: 255
            minLength: 1
            type: string
          type: array
        config:
          $ref: '#/components/schemas/GuardrailModerationPolicyConfig'
        id:
          description: Policy ID
          example: 550e8400-e29b-41d4-a716-446655440000
          format: uuid
          type: string
        is_account_policy:
          description: >-
            Whether this is an account-owned policy rather than a workspace
            policy
          type: boolean
        is_workspace_default:
          type: boolean
        member_ids:
          description: Organization member user IDs
          example:
            - user_2abcDEFghiJKLmnoPQRstu
          items:
            maxLength: 255
            minLength: 1
            type: string
          type: array
        name:
          description: Policy name
          example: Engineering monthly budget
          maxLength: 255
          minLength: 1
          type: string
        opted_out_api_key_hashes:
          description: API key hashes
          example:
            - c56454edb818d6b14bc0d61c46025f1450b0f4012d12304ab40aacb519fcbc93
          items:
            maxLength: 255
            minLength: 1
            type: string
          type: array
        opted_out_member_ids:
          description: Organization member user IDs
          example:
            - user_2abcDEFghiJKLmnoPQRstu
          items:
            maxLength: 255
            minLength: 1
            type: string
          type: array
        overridden_api_key_hashes:
          description: API keys that have a different policy of this type assigned directly
          example:
            - c56454edb818d6b14bc0d61c46025f1450b0f4012d12304ab40aacb519fcbc93
          items:
            maxLength: 255
            minLength: 1
            type: string
          type: array
        overridden_member_ids:
          description: Members that have a different policy of this type assigned directly
          example:
            - user_2abcDEFghiJKLmnoPQRstu
          items:
            maxLength: 255
            minLength: 1
            type: string
          type: array
        policy_type:
          enum:
            - moderation
          type: string
        reference:
          default: null
          description: >-
            `legacy_mapping` when the policy is synced from a v1 guardrail,
            `account_default` when it is an account-wide default, otherwise
            `null`
          enum:
            - legacy_mapping
            - account_default
            - null
          type:
            - string
            - 'null'
        replaces_legacy_default:
          description: >-
            Whether this workspace copy replaced a v1 workspace default
            guardrail that still exists; it cannot be deleted
          type: boolean
        updated_at:
          type:
            - string
            - 'null'
      required:
        - id
        - name
        - policy_type
        - config
        - updated_at
        - member_ids
        - api_key_hashes
        - opted_out_api_key_hashes
        - overridden_api_key_hashes
      type: object
    BadRequestResponseErrorData:
      description: Error data for BadRequestResponse
      example:
        code: 400
        message: Invalid request parameters
      properties:
        code:
          type: integer
        message:
          type: string
        metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
      required:
        - code
        - message
      type: object
    UnauthorizedResponseErrorData:
      description: Error data for UnauthorizedResponse
      example:
        code: 401
        message: Missing Authentication header
      properties:
        code:
          type: integer
        message:
          type: string
        metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
      required:
        - code
        - message
      type: object
    ForbiddenResponseErrorData:
      description: Error data for ForbiddenResponse
      example:
        code: 403
        message: Only management keys can perform this operation
      properties:
        code:
          type: integer
        message:
          type: string
        metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
      required:
        - code
        - message
      type: object
    NotFoundResponseErrorData:
      description: Error data for NotFoundResponse
      example:
        code: 404
        message: Resource not found
      properties:
        code:
          type: integer
        message:
          type: string
        metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
      required:
        - code
        - message
      type: object
    InternalServerResponseErrorData:
      description: Error data for InternalServerResponse
      example:
        code: 500
        message: Internal Server Error
      properties:
        code:
          type: integer
        message:
          type: string
        metadata:
          additionalProperties: {}
          type:
            - object
            - 'null'
      required:
        - code
        - message
      type: object
    GuardrailModerationPolicyConfig:
      additionalProperties: false
      example:
        content_filter_builtins:
          - action: block
            slug: secrets
      properties:
        armor:
          additionalProperties: false
          properties:
            classifier_context:
              $ref: '#/components/schemas/ArmorContext'
            mode:
              description: >-
                `enforce` withholds blocked calls; `audit` evaluates and reports
                the same verdicts without withholding any calls, regardless of
                `on_error`. Default `enforce`.
              enum:
                - enforce
                - audit
              type: string
            on_error:
              description: >-
                When the classifier cannot answer (timeout, upstream error,
                context too long) the call is reported `unavailable`; `block`
                rejects it and `log` releases it. Default `block`.
              enum:
                - log
                - block
              type: string
            use_cc_style_default_rules:
              description: >-
                Prepend Claude Code's built-in auto-mode rule set (1 hard-deny,
                72 soft-deny, 17 allow, 21 environment slots) ahead of every
                configured rule. Defaults to true on the Anthropic Messages API
                and false elsewhere.
              type: boolean
          type:
            - object
            - 'null'
        broadcast_model_armor_flagged_requests:
          type:
            - boolean
            - 'null'
        content_filter_blocks_requests:
          type: boolean
        content_filter_builtins:
          items:
            additionalProperties: false
            properties:
              action:
                enum:
                  - redact
                  - block
                  - flag
                type: string
              label:
                maxLength: 100
                type: string
              scan_scope:
                enum:
                  - user_only
                  - all_messages
                type: string
              slug:
                enum:
                  - email
                  - phone
                  - ssn
                  - credit-card
                  - ip-address
                  - secrets
                  - person-name
                  - address
                  - regex-prompt-injection
                type: string
            required:
              - slug
              - action
            type: object
          type:
            - array
            - 'null'
        content_filter_patterns:
          items:
            type: string
          type:
            - array
            - 'null'
        content_filters:
          items:
            additionalProperties: false
            properties:
              action:
                enum:
                  - redact
                  - block
                  - flag
                type: string
              label:
                maxLength: 100
                type:
                  - string
                  - 'null'
              pattern:
                maxLength: 100000
                minLength: 1
                type: string
            required:
              - pattern
              - action
            type: object
          type:
            - array
            - 'null'
        enable_model_armor_injection_protection:
          type:
            - boolean
            - 'null'
        lakera_injection_protection_mode:
          enum:
            - block
            - flag
            - null
          type:
            - string
            - 'null'
        model_armor_injection_confidence_level:
          enum:
            - low
            - medium
            - high
          type: string
        model_armor_injection_protection_mode:
          enum:
            - block
            - flag
            - null
          type:
            - string
            - 'null'
        pii_filters:
          items:
            additionalProperties: false
            properties:
              action:
                enum:
                  - redact
                  - block
                  - flag
                type: string
              entity_type:
                type: string
              score_threshold:
                maximum: 1
                minimum: 0
                type: number
            required:
              - entity_type
              - action
            type: object
          type:
            - array
            - 'null'
        platform_image_moderated_providers:
          items:
            type: string
          type:
            - array
            - 'null'
        platform_moderated_providers:
          items:
            type: string
          type:
            - array
            - 'null'
      type: object
    ArmorContext:
      additionalProperties:
        description: Carried unchanged; any JSON value.
      description: >-
        The Armor context: Claude Code's `classifier_context` (v1), with
        `auto_mode.{hard_deny,soft_deny,allow}` rules as strings or `{ id,
        instructions, threshold? }` objects and `auto_mode.environment` entries
        as `"Name: value"` strings or `{ name, value }` objects. `threshold`
        applies when Armor evaluates; when the provider evaluates natively
        (Anthropic dangerous-tool-use beta) rules are judged at the provider's
        own boundary.
      example:
        auto_mode:
          allow: []
          environment:
            - 'Trusted repo: github.com/acme/app'
          hard_deny: []
          soft_deny:
            - id: secrets-in-vcs
              instructions: >-
                Staging, committing or pushing a file that holds secrets,
                including indirectly through git add -A when the tree shows one.
        v: 1
      properties:
        auto_mode:
          $ref: '#/components/schemas/ArmorAutoMode'
        v:
          enum:
            - 1
          type: number
      required:
        - v
      type: object
    ArmorAutoMode:
      properties:
        allow:
          items:
            anyOf:
              - maxLength: 8122
                minLength: 1
                type: string
              - $ref: '#/components/schemas/ArmorRule'
          type: array
        environment:
          items:
            anyOf:
              - maxLength: 4122
                minLength: 1
                type: string
              - $ref: '#/components/schemas/ArmorEnvironmentEntry'
          type: array
        hard_deny:
          items:
            anyOf:
              - maxLength: 8122
                minLength: 1
                type: string
              - $ref: '#/components/schemas/ArmorRule'
          type: array
        soft_deny:
          items:
            anyOf:
              - maxLength: 8122
                minLength: 1
                type: string
              - $ref: '#/components/schemas/ArmorRule'
          type: array
      type: object
    ArmorRule:
      properties:
        id:
          description: >-
            Stable id, unique within its source; reported as the deciding rule
            when it fires.
          maxLength: 64
          minLength: 1
          pattern: ^[a-z0-9][a-z0-9_-]*$
          type: string
        instructions:
          description: What the rule matches, written for the classifier.
          maxLength: 8000
          minLength: 1
          type: string
        name:
          description: Display name shown in verdict explanations; defaults to the id.
          maxLength: 120
          minLength: 1
          type: string
        threshold:
          description: >-
            Probability at or above which the rule counts as matched. Defaults
            to 0.6 for hard-deny and soft-deny rules and 0.7 for allow rules (an
            exception needs stronger evidence to clear a matched soft deny).
          format: double
          type: number
      required:
        - id
        - instructions
      type: object
    ArmorEnvironmentEntry:
      properties:
        name:
          maxLength: 120
          minLength: 1
          type: string
        value:
          maxLength: 4000
          type: string
      required:
        - name
        - value
      type: object
  securitySchemes:
    apiKey:
      description: API key as bearer token in Authorization header
      scheme: bearer
      type: http

````
