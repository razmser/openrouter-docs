> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Get a model availability policy

> Get a model availability policy with its member and API key assignments. [Management key](../../../guides/overview/auth/management-api-keys.md) required.



## OpenAPI

````yaml /openapi/openapi.yaml get /guardrails/policies/model-availability/{id}
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
  /guardrails/policies/model-availability/{id}:
    get:
      tags:
        - Guardrail Policies
      summary: Get a model availability policy
      description: >-
        Get a model availability policy with its member and API key assignments.
        [Management key](/docs/guides/overview/auth/management-api-keys)
        required.
      operationId: getModelAvailabilityPolicy
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
        - description: >-
            Workspace the policy belongs to. Required for an organization
            management key; a workspace-scoped key defaults to its own workspace
            and gets 403 for any other.
          in: query
          name: workspace_id
          required: false
          schema:
            description: >-
              Workspace the policy belongs to. Required for an organization
              management key; a workspace-scoped key defaults to its own
              workspace and gets 403 for any other.
            example: 0df9e665-d932-5740-b2c7-b52af166bc11
            format: uuid
            type: string
      responses:
        '200':
          content:
            application/json:
              schema:
                $ref: >-
                  #/components/schemas/ModelAvailabilityGuardrailPolicyDetailResponse
          description: model availability policy details
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
    ModelAvailabilityGuardrailPolicyDetailResponse:
      properties:
        data:
          $ref: '#/components/schemas/ModelAvailabilityGuardrailPolicyDetail'
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
    ModelAvailabilityGuardrailPolicyDetail:
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
          $ref: '#/components/schemas/GuardrailModelAvailabilityPolicyConfig'
        id:
          description: Policy ID
          example: 550e8400-e29b-41d4-a716-446655440000
          format: uuid
          type: string
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
            - model_availability
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
    GuardrailModelAvailabilityPolicyConfig:
      additionalProperties: false
      example:
        allowed_models:
          - openai/gpt-4o
          - anthropic/claude-sonnet-4
        allowed_providers:
          - openai
          - anthropic
        enforce_zdr_anthropic: true
        enforce_zdr_openai: true
      properties:
        allow_safety_retention_google:
          type:
            - boolean
            - 'null'
        allow_safety_retention_other:
          type:
            - boolean
            - 'null'
        allowed_data_regions:
          items:
            type: string
          type:
            - array
            - 'null'
        allowed_models:
          items:
            type: string
          type:
            - array
            - 'null'
        allowed_providers:
          items:
            type: string
          type:
            - array
            - 'null'
        enable_free_model_publication:
          type:
            - boolean
            - 'null'
        enable_free_model_training:
          type:
            - boolean
            - 'null'
        enable_paid_model_training:
          type:
            - boolean
            - 'null'
        enforce_first_party_harness_models:
          type:
            - boolean
            - 'null'
        enforce_zdr:
          type:
            - boolean
            - 'null'
        enforce_zdr_anthropic:
          type:
            - boolean
            - 'null'
        enforce_zdr_google:
          type:
            - boolean
            - 'null'
        enforce_zdr_openai:
          type:
            - boolean
            - 'null'
        enforce_zdr_other:
          type:
            - boolean
            - 'null'
        enforce_zdr_xai:
          type:
            - boolean
            - 'null'
        ignored_models:
          items:
            type: string
          type:
            - array
            - 'null'
        ignored_providers:
          items:
            type: string
          type:
            - array
            - 'null'
        platform_banned_authors:
          items:
            type: string
          type:
            - array
            - 'null'
        platform_banned_models:
          items:
            type: string
          type:
            - array
            - 'null'
        platform_banned_providers:
          items:
            type: string
          type:
            - array
            - 'null'
        require_eu_data_region:
          type:
            - boolean
            - 'null'
      type: object
  securitySchemes:
    apiKey:
      description: API key as bearer token in Authorization header
      scheme: bearer
      type: http

````
