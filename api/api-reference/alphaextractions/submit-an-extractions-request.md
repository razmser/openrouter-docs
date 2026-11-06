> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Submit an Extractions request

> Extracts, computes, estimates or forecasts typed fields from a state string and image assets using an extraction-style System One model. Alpha: the shape is not stable.



## OpenAPI

````yaml /openapi/openapi.yaml post /api/alpha/extractions
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
  /api/alpha/extractions:
    post:
      tags:
        - alpha.extractions
      summary: Submit an Extractions request
      description: >-
        Extracts, computes, estimates or forecasts typed fields from a state
        string and image assets using an extraction-style System One model.
        Alpha: the shape is not stable.
      operationId: createApiAlphaExtractions
      requestBody:
        content:
          application/json:
            example:
              fields:
                contacts:
                  items: text
                  type: list
                days_to_pay:
                  max: 120
                  min: 0
                  step: 1
                  type: estimate
                due_date:
                  instructions: Issue date plus the net payment days
                  type: date
                invoice_number:
                  type: text
                total:
                  decimals: 2
                  type: number
                  unit: USD
              model: cloudflare/clairic
              reference_date: '2026-10-28'
              state: >-
                Invoice INV-2291 issued 2026-09-02, net 30. Contacts: Dana Ruiz,
                Priya Shah. Total $1080.
            schema:
              $ref: '#/components/schemas/ExtractionsRequest'
        required: true
      responses:
        '200':
          content:
            application/json:
              example:
                answers:
                  contacts:
                    confidence: 0.9999
                    spans:
                      - - 53
                        - 62
                      - - 64
                        - 74
                    type: list
                    value:
                      - Dana Ruiz
                      - Priya Shah
                  days_to_pay:
                    mean: 29.5
                    median: 30
                    p10: 21
                    p90: 38
                    type: estimate
                    value: 30
                  due_date:
                    guess: '2026-10-02'
                    p_null: 1.9e-8
                    type: date
                    value: '2026-10-02'
                  invoice_number:
                    confidence: 1
                    guess: INV-2291
                    p_null: 3.8e-10
                    span:
                      - 8
                      - 16
                    type: text
                    value: INV-2291
                  total:
                    confidence: 0.9999
                    guess: 1080
                    p_null: 2.3e-8
                    type: number
                    value: 1080
                id: gen-dec-1793251006-X5e5eKGQdvR9rblyX250
                model: cloudflare/clairic
                provider: Cloudflare
                truncated: false
                usage:
                  cost: 0.0000655
                  image_tokens: 0
                  input_tokens: 655
                  output_tokens: 0
                  passes: 3
                  schema_tokens: 472
                  state_tokens: 61
              schema:
                $ref: '#/components/schemas/ExtractionsResponse'
          description: Extractions response
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
        '402':
          content:
            application/json:
              example:
                error:
                  code: 402
                  message: >-
                    Insufficient credits. Add more using
                    https://openrouter.ai/credits
              schema:
                $ref: '#/components/schemas/PaymentRequiredResponse'
          description: Payment Required - Insufficient credits or quota to complete request
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
        '413':
          content:
            application/json:
              example:
                error:
                  code: 413
                  message: Request payload too large
              schema:
                $ref: '#/components/schemas/PayloadTooLargeResponse'
          description: Payload Too Large - Request payload exceeds size limits
        '429':
          content:
            application/json:
              example:
                error:
                  code: 429
                  message: Rate limit exceeded
              schema:
                $ref: '#/components/schemas/TooManyRequestsResponse'
          description: Too Many Requests - Rate limit exceeded
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
        '502':
          content:
            application/json:
              example:
                error:
                  code: 502
                  message: Provider returned error
              schema:
                $ref: '#/components/schemas/BadGatewayResponse'
          description: Bad Gateway - Provider/upstream API failure
        '503':
          content:
            application/json:
              example:
                error:
                  code: 503
                  message: Service temporarily unavailable
              schema:
                $ref: '#/components/schemas/ServiceUnavailableResponse'
          description: Service Unavailable - Service temporarily unavailable
        '524':
          content:
            application/json:
              example:
                error:
                  code: 524
                  message: Request timed out. Please try again later.
              schema:
                $ref: '#/components/schemas/EdgeNetworkTimeoutResponse'
          description: Infrastructure Timeout - Provider request timed out at edge network
        '529':
          content:
            application/json:
              example:
                error:
                  code: 529
                  message: Provider returned error
              schema:
                $ref: '#/components/schemas/ProviderOverloadedResponse'
          description: Provider Overloaded - Provider is temporarily overloaded
      servers:
        - url: https://openrouter.ai
components:
  schemas:
    ExtractionsRequest:
      additionalProperties: false
      properties:
        assets:
          additionalProperties:
            $ref: '#/components/schemas/ExtractionAsset'
          description: >-
            Assets keyed by reference string. Write a reference wherever the
            asset belongs in `state` or a field `instructions`; every asset must
            be referenced at least once. A `state` that is exactly the sole
            asset's key carries no text of its own and is read as file-only. A
            model that reads either text or a document per request, not both
            (ScaleDown Extract with a PDF), needs that form: any other text
            around the key is state text and is rejected with 400.
          type: object
        fields:
          additionalProperties:
            description: >-
              A typed field to extract, compute, estimate or forecast from the
              state. Which types a model answers is model-specific; unsupported
              types are rejected with 400.
            discriminator:
              mapping:
                date: '#/components/schemas/ExtractionDateField'
                datetime: '#/components/schemas/ExtractionDatetimeField'
                duration: '#/components/schemas/ExtractionDurationField'
                estimate: '#/components/schemas/ExtractionEstimateField'
                forecast: '#/components/schemas/ExtractionForecastField'
                list: '#/components/schemas/ExtractionListField'
                number: '#/components/schemas/ExtractionNumberField'
                text: '#/components/schemas/ExtractionTextField'
                time: '#/components/schemas/ExtractionTimeField'
              propertyName: type
            oneOf:
              - $ref: '#/components/schemas/ExtractionTextField'
              - $ref: '#/components/schemas/ExtractionNumberField'
              - $ref: '#/components/schemas/ExtractionDateField'
              - $ref: '#/components/schemas/ExtractionTimeField'
              - $ref: '#/components/schemas/ExtractionDatetimeField'
              - $ref: '#/components/schemas/ExtractionDurationField'
              - $ref: '#/components/schemas/ExtractionListField'
              - $ref: '#/components/schemas/ExtractionEstimateField'
              - $ref: '#/components/schemas/ExtractionForecastField'
          description: Map of field name to typed field spec.
          type: object
        model:
          type: string
        provider:
          allOf:
            - $ref: '#/components/schemas/ProviderPreferences'
            - description: Provider routing preferences for the request.
        reference_date:
          description: ISO date that anchors dates written without a year.
          pattern: ^\d{4}-\d{2}-\d{2}$
          type: string
        session_id:
          description: >-
            A unique identifier for grouping related requests (e.g., a
            conversation or agent workflow). Used for observability grouping in
            Broadcast and private logging; never sent to the provider. If
            provided in both the request body and the x-session-id header, the
            body value takes precedence. Maximum of 256 characters.
          example: session-1234
          maxLength: 256
          type: string
        state:
          description: >-
            The text to read from. May be empty only when the request carries
            image assets.
          type: string
        trace:
          $ref: '#/components/schemas/TraceConfig'
        user:
          maxLength: 256
          type: string
      required:
        - model
        - state
        - fields
      type: object
    ExtractionsResponse:
      properties:
        answers:
          additionalProperties:
            description: >-
              One answer per requested field. `value` is null when the state
              does not determine it.
            discriminator:
              mapping:
                date: '#/components/schemas/ExtractionDateAnswer'
                datetime: '#/components/schemas/ExtractionDatetimeAnswer'
                duration: '#/components/schemas/ExtractionDurationAnswer'
                estimate: '#/components/schemas/ExtractionEstimateAnswer'
                forecast: '#/components/schemas/ExtractionForecastAnswer'
                list: '#/components/schemas/ExtractionListAnswer'
                number: '#/components/schemas/ExtractionNumberAnswer'
                text: '#/components/schemas/ExtractionTextAnswer'
                time: '#/components/schemas/ExtractionTimeAnswer'
              propertyName: type
            oneOf:
              - $ref: '#/components/schemas/ExtractionTextAnswer'
              - $ref: '#/components/schemas/ExtractionNumberAnswer'
              - $ref: '#/components/schemas/ExtractionDateAnswer'
              - $ref: '#/components/schemas/ExtractionTimeAnswer'
              - $ref: '#/components/schemas/ExtractionDatetimeAnswer'
              - $ref: '#/components/schemas/ExtractionDurationAnswer'
              - $ref: '#/components/schemas/ExtractionListAnswer'
              - $ref: '#/components/schemas/ExtractionEstimateAnswer'
              - $ref: '#/components/schemas/ExtractionForecastAnswer'
          type: object
        id:
          type: string
        model:
          type: string
        provider:
          type: string
        state_text:
          description: >-
            The text that spans index into, when requested through provider
            options.
          type:
            - string
            - 'null'
        truncated:
          description: True when the provider read only a prefix of the state.
          type: boolean
        usage:
          $ref: '#/components/schemas/ExtractionsUsage'
      required:
        - model
        - answers
        - usage
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
    PaymentRequiredResponse:
      description: Payment Required - Insufficient credits or quota to complete request
      example:
        error:
          code: 402
          message: Insufficient credits. Add more using https://openrouter.ai/credits
      properties:
        error:
          $ref: '#/components/schemas/PaymentRequiredResponseErrorData'
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
    PayloadTooLargeResponse:
      description: Payload Too Large - Request payload exceeds size limits
      example:
        error:
          code: 413
          message: Request payload too large
      properties:
        error:
          $ref: '#/components/schemas/PayloadTooLargeResponseErrorData'
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
    TooManyRequestsResponse:
      description: Too Many Requests - Rate limit exceeded
      example:
        error:
          code: 429
          message: Rate limit exceeded
      properties:
        error:
          $ref: '#/components/schemas/TooManyRequestsResponseErrorData'
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
    BadGatewayResponse:
      description: Bad Gateway - Provider/upstream API failure
      example:
        error:
          code: 502
          message: Provider returned error
      properties:
        error:
          $ref: '#/components/schemas/BadGatewayResponseErrorData'
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
    ServiceUnavailableResponse:
      description: Service Unavailable - Service temporarily unavailable
      example:
        error:
          code: 503
          message: Service temporarily unavailable
      properties:
        error:
          $ref: '#/components/schemas/ServiceUnavailableResponseErrorData'
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
    EdgeNetworkTimeoutResponse:
      description: Infrastructure Timeout - Provider request timed out at edge network
      example:
        error:
          code: 524
          message: Request timed out. Please try again later.
      properties:
        error:
          $ref: '#/components/schemas/EdgeNetworkTimeoutResponseErrorData'
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
    ProviderOverloadedResponse:
      description: Provider Overloaded - Provider is temporarily overloaded
      example:
        error:
          code: 529
          message: Provider returned error
      properties:
        error:
          $ref: '#/components/schemas/ProviderOverloadedResponseErrorData'
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
    ExtractionAsset:
      additionalProperties: false
      description: >-
        An image or PDF sent once and referenced by its key in the `assets` map.
        `data_base64` is the file in standard base64 with no `data:` prefix. PDF
        is read by document models only.
      properties:
        data_base64:
          minLength: 1
          pattern: ^(?:[A-Za-z0-9+/]{4})*(?:[A-Za-z0-9+/]{2}==|[A-Za-z0-9+/]{3}=)?$
          type: string
        format:
          enum:
            - png
            - jpg
            - jpeg
            - pdf
          type: string
        type:
          enum:
            - image
            - document
          type: string
      required:
        - format
        - data_base64
      type: object
    ExtractionDateField:
      additionalProperties: false
      properties:
        instructions:
          description: What the field should contain.
          type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - date
          type: string
      required:
        - type
      type: object
    ExtractionDatetimeField:
      additionalProperties: false
      properties:
        instructions:
          description: What the field should contain.
          type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - datetime
          type: string
      required:
        - type
      type: object
    ExtractionDurationField:
      additionalProperties: false
      properties:
        decimals:
          description: Decimal places kept in `value`.
          maximum: 6
          minimum: 0
          type: integer
        instructions:
          description: What the field should contain.
          type: string
        integer:
          type: boolean
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - duration
          type: string
        unit:
          description: seconds, minutes, hours, days, weeks, months or years.
          type: string
      required:
        - type
      type: object
    ExtractionEstimateField:
      additionalProperties: false
      properties:
        instructions:
          description: What the field should contain.
          type: string
        max:
          anyOf:
            - format: double
              type: number
            - type: string
        min:
          anyOf:
            - format: double
              type: number
            - type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        scale:
          enum:
            - linear
            - log
          type: string
        step:
          anyOf:
            - exclusiveMinimum: 0
              format: double
              type: number
            - enum:
                - month
              type: string
            - enum:
                - year
              type: string
        type:
          enum:
            - estimate
          type: string
        unit:
          type: string
      required:
        - type
        - min
        - max
      type: object
    ExtractionForecastField:
      additionalProperties: false
      properties:
        horizon:
          description: Number of forecast steps.
          maximum: 64
          minimum: 1
          type: integer
        instructions:
          description: What the field should contain.
          type: string
        interval:
          enum:
            - step
            - minute
            - hour
            - day
            - week
            - month
            - quarter
            - year
          type: string
        max:
          anyOf:
            - format: double
              type: number
            - type: string
        min:
          anyOf:
            - format: double
              type: number
            - type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        scale:
          enum:
            - linear
            - log
          type: string
        step:
          anyOf:
            - exclusiveMinimum: 0
              format: double
              type: number
            - enum:
                - month
              type: string
            - enum:
                - year
              type: string
        type:
          enum:
            - forecast
          type: string
        unit:
          type: string
      required:
        - type
        - min
        - max
        - horizon
        - interval
      type: object
    ExtractionListField:
      additionalProperties: false
      properties:
        decimals:
          description: Decimal places kept in `value`.
          maximum: 6
          minimum: 0
          type: integer
        instructions:
          description: What the field should contain.
          type: string
        items:
          enum:
            - text
            - number
            - date
          type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - list
          type: string
      required:
        - type
        - items
      type: object
    ExtractionNumberField:
      additionalProperties: false
      properties:
        decimals:
          description: Decimal places kept in `value`.
          maximum: 6
          minimum: 0
          type: integer
        instructions:
          description: What the field should contain.
          type: string
        integer:
          type: boolean
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - number
          type: string
        unit:
          type: string
      required:
        - type
      type: object
    ExtractionTextField:
      additionalProperties: false
      properties:
        instructions:
          description: What the field should contain.
          type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - text
          type: string
      required:
        - type
      type: object
    ExtractionTimeField:
      additionalProperties: false
      properties:
        instructions:
          description: What the field should contain.
          type: string
        null_threshold:
          description: Probability of null above which `value` is null. Default 0.5.
          format: double
          maximum: 1
          minimum: 0
          type: number
        type:
          enum:
            - time
          type: string
      required:
        - type
      type: object
    ProviderPreferences:
      additionalProperties: false
      description: >-
        When multiple model providers are available, optionally indicate your
        routing preference.
      example:
        allow_fallbacks: true
      properties:
        allow_fallbacks:
          description: >
            Whether to allow backup providers to serve requests

            - true: (default) when the primary provider (or your custom
            providers in "order") is unavailable, use the next best provider.

            - false: use only the primary/custom provider, and return the
            upstream error if it's unavailable.
          type:
            - boolean
            - 'null'
        data_collection:
          description: >-
            Data collection setting. If no available model provider meets the
            requirement, your request will return an error.

            - allow: (default) allow providers which store user data
            non-transiently and may train on it


            - deny: use only providers which do not collect user data.
          enum:
            - deny
            - allow
            - null
          example: allow
          type:
            - string
            - 'null'
        enforce_distillable_text:
          description: >-
            Whether to restrict routing to only models that allow text
            distillation. When true, only models where the author has allowed
            distillation will be used.
          example: true
          type:
            - boolean
            - 'null'
        ignore:
          description: >-
            List of provider slugs to ignore. If provided, this list is merged
            with your account-wide ignored provider settings for this request.
          example:
            - openai
            - anthropic
          items:
            anyOf:
              - $ref: '#/components/schemas/ProviderName'
              - type: string
          type:
            - array
            - 'null'
        max_price:
          description: >-
            The object specifying the maximum price you want to pay for this
            request. USD price per million tokens, for prompt and completion.
          properties:
            audio:
              description: Maximum price in USD per audio unit
              type: string
            completion:
              description: Maximum price in USD per million completion tokens
              type: string
            image:
              description: Maximum price in USD per image
              type: string
            prompt:
              description: Maximum price in USD per million prompt tokens
              type: string
            request:
              description: Maximum price in USD per request
              type: string
          type: object
        only:
          description: >-
            List of provider slugs to allow. If provided, this list is merged
            with your account-wide allowed provider settings for this request.
          example:
            - openai
            - anthropic
          items:
            anyOf:
              - $ref: '#/components/schemas/ProviderName'
              - type: string
          type:
            - array
            - 'null'
        options:
          $ref: '#/components/schemas/ProviderOptions'
        order:
          description: >-
            An ordered list of provider slugs. The router will attempt to use
            the first provider in the subset of this list that supports your
            requested model, and fall back to the next if it is unavailable. If
            no providers are available, the request will fail with an error
            message.
          example:
            - openai
            - anthropic
          items:
            anyOf:
              - $ref: '#/components/schemas/ProviderName'
              - type: string
          type:
            - array
            - 'null'
        preferred_max_latency:
          $ref: '#/components/schemas/PreferredMaxLatency'
        preferred_min_throughput:
          $ref: '#/components/schemas/PreferredMinThroughput'
        quantizations:
          description: A list of quantization levels to filter the provider by.
          items:
            $ref: '#/components/schemas/Quantization'
          type:
            - array
            - 'null'
        require_parameters:
          description: >-
            Whether to filter providers to only those that support the
            parameters you've provided. If this setting is omitted or set to
            false, then providers will receive only the parameters they support,
            and ignore the rest.
          type:
            - boolean
            - 'null'
        sort:
          anyOf:
            - $ref: '#/components/schemas/ProviderSort'
            - $ref: '#/components/schemas/ProviderSortConfig'
            - type: 'null'
          description: >-
            The sorting strategy to use for this request, if "order" is not
            specified. When set, no load balancing is performed.
          example: price
        zdr:
          description: >-
            Whether to restrict routing to only ZDR (Zero Data Retention)
            endpoints. When true, only endpoints that do not retain prompts will
            be used.
          example: true
          type:
            - boolean
            - 'null'
      type:
        - object
        - 'null'
    TraceConfig:
      additionalProperties: {}
      description: >-
        Metadata for observability and tracing. Known keys (trace_id,
        trace_name, span_name, generation_name, parent_span_id) have special
        handling. Additional keys are passed through as custom metadata to
        configured broadcast destinations.
      example:
        trace_id: trace-abc123
        trace_name: my-app-trace
      properties:
        generation_name:
          type: string
        parent_span_id:
          type: string
        span_name:
          type: string
        trace_id:
          type: string
        trace_name:
          type: string
      type: object
    ExtractionDateAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          type: string
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        span:
          description: >-
            Unicode code point offsets [start, end) into the state text: index
            code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
            accented letter counts once.
          items:
            type: integer
          maxItems: 2
          minItems: 2
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - date
          type: string
        value:
          type:
            - string
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionDatetimeAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          type: string
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        span:
          description: >-
            Unicode code point offsets [start, end) into the state text: index
            code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
            accented letter counts once.
          items:
            type: integer
          maxItems: 2
          minItems: 2
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - datetime
          type: string
        value:
          type:
            - string
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionDurationAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          format: double
          type: number
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        span:
          description: >-
            Unicode code point offsets [start, end) into the state text: index
            code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
            accented letter counts once.
          items:
            type: integer
          maxItems: 2
          minItems: 2
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - duration
          type: string
        unit:
          description: The unit `value` is expressed in.
          type: string
        value:
          format: double
          type:
            - number
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionEstimateAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          anyOf:
            - format: double
              type: number
            - type: string
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
        mean:
          anyOf:
            - format: double
              type: number
            - type: string
        median:
          anyOf:
            - format: double
              type: number
            - type: string
        p_above:
          description: Probability mass above `max`.
          format: double
          type: number
        p_below:
          description: Probability mass below `min`.
          format: double
          type: number
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        p10:
          anyOf:
            - format: double
              type: number
            - type: string
        p90:
          anyOf:
            - format: double
              type: number
            - type: string
        quantiles:
          description: 99 percentiles, present when the provider is asked for quantiles.
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - estimate
          type: string
        value:
          anyOf:
            - format: double
              type: number
            - type: string
            - type: 'null'
      required:
        - type
        - value
      type: object
    ExtractionForecastAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        mean:
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        median:
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        p10:
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        p90:
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        steps:
          items:
            $ref: '#/components/schemas/ExtractionForecastStep'
          type: array
        type:
          enum:
            - forecast
          type: string
        value:
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type:
            - array
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionListAnswer:
      properties:
        confidence:
          format: double
          type: number
        confidences:
          description: One confidence per item of `value`, in the same order.
          items:
            format: double
            type: number
          type: array
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          items:
            anyOf:
              - type: string
              - format: double
                type: number
          type: array
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        spans:
          items:
            description: >-
              Unicode code point offsets [start, end) into the state text: index
              code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
              accented letter counts once.
            items:
              type: integer
            maxItems: 2
            minItems: 2
            type: array
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - list
          type: string
        value:
          items:
            anyOf:
              - type: string
              - format: double
                type: number
          type:
            - array
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionNumberAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          format: double
          type: number
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        span:
          description: >-
            Unicode code point offsets [start, end) into the state text: index
            code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
            accented letter counts once.
          items:
            type: integer
          maxItems: 2
          minItems: 2
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - number
          type: string
        value:
          format: double
          type:
            - number
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionTextAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          type: string
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        span:
          description: >-
            Unicode code point offsets [start, end) into the state text: index
            code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
            accented letter counts once.
          items:
            type: integer
          maxItems: 2
          minItems: 2
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - text
          type: string
        value:
          type:
            - string
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionTimeAnswer:
      properties:
        confidence:
          format: double
          type: number
        guess:
          description: >-
            The most likely value even when `value` is null because `p_null`
            crossed the threshold.
          type: string
        p_null:
          description: Probability that the state contains nothing for this field.
          format: double
          type: number
        source:
          description: >-
            Set to `image` or `document` when the answer was read from an image
            or a PDF rather than the state text.
          enum:
            - state
            - image
            - document
          type: string
        span:
          description: >-
            Unicode code point offsets [start, end) into the state text: index
            code points (not UTF-16 code units or UTF-8 bytes), so an emoji or
            accented letter counts once.
          items:
            type: integer
          maxItems: 2
          minItems: 2
          type: array
        spell_confidence:
          description: Confidence in the spelling of text read from an image.
          format: double
          type: number
        type:
          enum:
            - time
          type: string
        value:
          type:
            - string
            - 'null'
      required:
        - type
        - value
      type: object
    ExtractionsUsage:
      properties:
        cost:
          format: double
          type: number
        image_tokens:
          type: integer
        input_tokens:
          type: integer
        output_tokens:
          type: integer
        passes:
          description: Number of upstream passes when the fields did not fit in one.
          type: integer
        schema_tokens:
          type: integer
        state_tokens:
          type: integer
      required:
        - input_tokens
        - output_tokens
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
    PaymentRequiredResponseErrorData:
      description: Error data for PaymentRequiredResponse
      example:
        code: 402
        message: Insufficient credits. Add more using https://openrouter.ai/credits
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
    PayloadTooLargeResponseErrorData:
      description: Error data for PayloadTooLargeResponse
      example:
        code: 413
        message: Request payload too large
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
    TooManyRequestsResponseErrorData:
      description: Error data for TooManyRequestsResponse
      example:
        code: 429
        message: Rate limit exceeded
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
    BadGatewayResponseErrorData:
      description: Error data for BadGatewayResponse
      example:
        code: 502
        message: Provider returned error
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
    ServiceUnavailableResponseErrorData:
      description: Error data for ServiceUnavailableResponse
      example:
        code: 503
        message: Service temporarily unavailable
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
    EdgeNetworkTimeoutResponseErrorData:
      description: Error data for EdgeNetworkTimeoutResponse
      example:
        code: 524
        message: Request timed out. Please try again later.
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
    ProviderOverloadedResponseErrorData:
      description: Error data for ProviderOverloadedResponse
      example:
        code: 529
        message: Provider returned error
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
    ProviderName:
      enum:
        - Modal
        - AkashML
        - AI21
        - AionLabs
        - Alibaba
        - Ambient
        - Ant Digital
        - Baidu
        - Amazon Bedrock
        - Amazon Nova
        - Anthropic
        - Arcee AI
        - AssemblyAI
        - AtlasCloud
        - Avian
        - Azure
        - BaseTen
        - BytePlus
        - Black Forest Labs
        - Cerebras
        - Chutes
        - Cirrascale
        - Claude Platform on AWS
        - Clarifai
        - Cloudflare
        - Cohere
        - CoreWeave
        - Cosine
        - Crucible
        - Crusoe
        - Darkbloom
        - Databricks
        - Decart
        - Deepgram
        - DeepInfra
        - DeepSeek
        - DekaLLM
        - DigitalOcean
        - ElevenLabs
        - Featherless
        - Fireworks
        - Fish Audio
        - Friendli
        - GMICloud
        - Google
        - Google AI Studio
        - Groq
        - HeyGen
        - Inception
        - Inceptron
        - InferenceNet
        - Ionstream
        - Infermatic
        - Io Net
        - Inferact vLLM
        - Inflection
        - KT
        - Liquid
        - Makora
        - Mara
        - Mancer 2
        - Meta
        - Minimax
        - ModelRun
        - Mistral
        - Modular
        - Moonshot AI
        - Morph
        - VoyageAI by MongoDB
        - TypeSafe
        - Near AI
        - Nebius
        - Nex AGI
        - NextBit
        - Novita
        - Nvidia
        - Ollama
        - OpenAI
        - OpenInference
        - Parallel
        - Parasail
        - ParetoAlpha
        - Particle AI
        - Pearl Research
        - Poolside
        - PrimaLabs
        - PrimeIntellect
        - Perceptron
        - Perplexity
        - Phala
        - Recraft
        - Recursive
        - Reka
        - Relace
        - Respan
        - River
        - Sail Research
        - Sakana AI
        - SambaNova
        - ScaleDown
        - Seed
        - SiliconFlow
        - Sourceful
        - StepFun
        - Stealth
        - StreamLake
        - Switchpoint
        - Tencent
        - Tenstorrent
        - Thinking Machines
        - Together
        - Unbiased
        - Upstage
        - Venice
        - Wafer
        - WandB
        - Quiver
        - Krea
        - Runway
        - Xiaomi
        - xAI
        - Z.AI
        - FakeProvider
      example: OpenAI
      type: string
    ProviderOptions:
      description: >-
        Provider-specific options keyed by provider slug. The provider segment
        is case-insensitive; an endpoint tag after `/` must match the endpoint
        slug exactly. Only options for the matched provider are forwarded; the
        rest are ignored. Unrecognized keys are silently dropped.
      example:
        openai:
          max_tokens: 1000
      properties:
        01ai:
          additionalProperties: {}
          type: object
        ai21:
          additionalProperties: {}
          type: object
        aion-labs:
          additionalProperties: {}
          type: object
        akashml:
          additionalProperties: {}
          type: object
        alibaba:
          additionalProperties: {}
          type: object
        amazon-bedrock:
          additionalProperties: {}
          type: object
        amazon-bedrock/claude-on-aws:
          additionalProperties: {}
          type: object
        amazon-nova:
          additionalProperties: {}
          type: object
        ambient:
          additionalProperties: {}
          type: object
        antdigital:
          additionalProperties: {}
          type: object
        anthropic:
          additionalProperties: {}
          type: object
        anthropic/2:
          additionalProperties: {}
          type: object
        anyscale:
          additionalProperties: {}
          type: object
        arcee-ai:
          additionalProperties: {}
          type: object
        assemblyai:
          additionalProperties: {}
          type: object
        atlas-cloud:
          additionalProperties: {}
          type: object
        atoma:
          additionalProperties: {}
          type: object
        avian:
          additionalProperties: {}
          type: object
        azure:
          additionalProperties: {}
          type: object
        baidu:
          additionalProperties: {}
          type: object
        baseten:
          additionalProperties: {}
          type: object
        black-forest-labs:
          additionalProperties: {}
          type: object
        byteplus:
          additionalProperties: {}
          type: object
        centml:
          additionalProperties: {}
          type: object
        cerebras:
          additionalProperties: {}
          type: object
        chutes:
          additionalProperties: {}
          type: object
        cirrascale:
          additionalProperties: {}
          type: object
        clarifai:
          additionalProperties: {}
          type: object
        claude-on-aws:
          additionalProperties: {}
          type: object
        cloudflare:
          additionalProperties: {}
          type: object
        cohere:
          additionalProperties: {}
          type: object
        coreweave:
          additionalProperties: {}
          type: object
        cosine:
          additionalProperties: {}
          type: object
        crofai:
          additionalProperties: {}
          type: object
        crucible:
          additionalProperties: {}
          type: object
        crusoe:
          additionalProperties: {}
          type: object
        darkbloom:
          additionalProperties: {}
          type: object
        databricks:
          additionalProperties: {}
          type: object
        decart:
          additionalProperties: {}
          type: object
        deepgram:
          additionalProperties: {}
          type: object
        deepinfra:
          additionalProperties: {}
          type: object
        deepseek:
          additionalProperties: {}
          type: object
        dekallm:
          additionalProperties: {}
          type: object
        digitalocean:
          additionalProperties: {}
          type: object
        elevenlabs:
          additionalProperties: {}
          type: object
        enfer:
          additionalProperties: {}
          type: object
        fake-provider:
          additionalProperties: {}
          type: object
        featherless:
          additionalProperties: {}
          type: object
        fireworks:
          additionalProperties: {}
          type: object
        fish-audio:
          additionalProperties: {}
          type: object
        friendli:
          additionalProperties: {}
          type: object
        gmicloud:
          additionalProperties: {}
          type: object
        google-ai-studio:
          additionalProperties: {}
          type: object
        google-vertex:
          additionalProperties: {}
          type: object
        gopomelo:
          additionalProperties: {}
          type: object
        groq:
          additionalProperties: {}
          type: object
        heygen:
          additionalProperties: {}
          type: object
        huggingface:
          additionalProperties: {}
          type: object
        hyperbolic:
          additionalProperties: {}
          type: object
        hyperbolic-quantized:
          additionalProperties: {}
          type: object
        inception:
          additionalProperties: {}
          type: object
        inceptron:
          additionalProperties: {}
          type: object
        inferact-vllm:
          additionalProperties: {}
          type: object
        inference-net:
          additionalProperties: {}
          type: object
        infermatic:
          additionalProperties: {}
          type: object
        inflection:
          additionalProperties: {}
          type: object
        inocloud:
          additionalProperties: {}
          type: object
        io-net:
          additionalProperties: {}
          type: object
        ionstream:
          additionalProperties: {}
          type: object
        klusterai:
          additionalProperties: {}
          type: object
        krea:
          additionalProperties: {}
          type: object
        kt:
          additionalProperties: {}
          type: object
        lambda:
          additionalProperties: {}
          type: object
        lepton:
          additionalProperties: {}
          type: object
        liquid:
          additionalProperties: {}
          type: object
        lynn:
          additionalProperties: {}
          type: object
        lynn-private:
          additionalProperties: {}
          type: object
        makora:
          additionalProperties: {}
          type: object
        mancer:
          additionalProperties: {}
          type: object
        mancer-old:
          additionalProperties: {}
          type: object
        mara:
          additionalProperties: {}
          type: object
        meta:
          additionalProperties: {}
          type: object
        minimax:
          additionalProperties: {}
          type: object
        mistral:
          additionalProperties: {}
          type: object
        modal:
          additionalProperties: {}
          type: object
        modelrun:
          additionalProperties: {}
          type: object
        modular:
          additionalProperties: {}
          type: object
        moonshotai:
          additionalProperties: {}
          type: object
        morph:
          additionalProperties: {}
          type: object
        ncompass:
          additionalProperties: {}
          type: object
        near-ai:
          additionalProperties: {}
          type: object
        nebius:
          additionalProperties: {}
          type: object
        nex-agi:
          additionalProperties: {}
          type: object
        nextbit:
          additionalProperties: {}
          type: object
        nineteen:
          additionalProperties: {}
          type: object
        novita:
          additionalProperties: {}
          type: object
        nvidia:
          additionalProperties: {}
          type: object
        octoai:
          additionalProperties: {}
          type: object
        ollama:
          additionalProperties: {}
          type: object
        open-inference:
          additionalProperties: {}
          type: object
        openai:
          additionalProperties: {}
          type: object
        parallel:
          additionalProperties: {}
          type: object
        parasail:
          additionalProperties: {}
          type: object
        pareto-alpha:
          additionalProperties: {}
          type: object
        particle-ai:
          additionalProperties: {}
          type: object
        pearl-research:
          additionalProperties: {}
          type: object
        perceptron:
          additionalProperties: {}
          type: object
        perplexity:
          additionalProperties: {}
          type: object
        phala:
          additionalProperties: {}
          type: object
        poolside:
          additionalProperties: {}
          type: object
        primalabs:
          additionalProperties: {}
          type: object
        primeintellect:
          additionalProperties: {}
          type: object
        quiver:
          additionalProperties: {}
          type: object
        recraft:
          additionalProperties: {}
          type: object
        recursal:
          additionalProperties: {}
          type: object
        recursive:
          additionalProperties: {}
          type: object
        reflection:
          additionalProperties: {}
          type: object
        reka:
          additionalProperties: {}
          type: object
        relace:
          additionalProperties: {}
          type: object
        replicate:
          additionalProperties: {}
          type: object
        respan:
          additionalProperties: {}
          type: object
        river:
          additionalProperties: {}
          type: object
        runway:
          additionalProperties: {}
          type: object
        sail-research:
          additionalProperties: {}
          type: object
        sakana:
          additionalProperties: {}
          type: object
        sakana-ai:
          additionalProperties: {}
          type: object
        sambanova:
          additionalProperties: {}
          type: object
        sambanova-cloaked:
          additionalProperties: {}
          type: object
        scaledown:
          additionalProperties: {}
          type: object
        seed:
          additionalProperties: {}
          type: object
        sf-compute:
          additionalProperties: {}
          type: object
        siliconflow:
          additionalProperties: {}
          type: object
        sourceful:
          additionalProperties: {}
          type: object
        stealth:
          additionalProperties: {}
          type: object
        stepfun:
          additionalProperties: {}
          type: object
        streamlake:
          additionalProperties: {}
          type: object
        switchpoint:
          additionalProperties: {}
          type: object
        targon:
          additionalProperties: {}
          type: object
        tencent:
          additionalProperties: {}
          type: object
        tenstorrent:
          additionalProperties: {}
          type: object
        thinkingmachines:
          additionalProperties: {}
          type: object
        together:
          additionalProperties: {}
          type: object
        together-lite:
          additionalProperties: {}
          type: object
        typesafe:
          additionalProperties: {}
          type: object
        ubicloud:
          additionalProperties: {}
          type: object
        unbiased:
          additionalProperties: {}
          type: object
        upstage:
          additionalProperties: {}
          type: object
        venice:
          additionalProperties: {}
          type: object
        voyageai:
          additionalProperties: {}
          type: object
        wafer:
          additionalProperties: {}
          type: object
        wandb:
          additionalProperties: {}
          type: object
        wandb-legacy:
          additionalProperties: {}
          type: object
        xai:
          additionalProperties: {}
          type: object
        xiaomi:
          additionalProperties: {}
          type: object
        z-ai:
          additionalProperties: {}
          type: object
      type: object
    PreferredMaxLatency:
      anyOf:
        - format: double
          type: number
        - $ref: '#/components/schemas/PercentileLatencyCutoffs'
        - type: 'null'
      description: >-
        Preferred maximum latency (in seconds). Can be a number (applies to p50)
        or an object with percentile-specific cutoffs. Endpoints above the
        threshold(s) may still be used, but are deprioritized in routing. When
        using fallback models, this may cause a fallback model to be used
        instead of the primary model if it meets the threshold.
      example: 5
    PreferredMinThroughput:
      anyOf:
        - format: double
          type: number
        - $ref: '#/components/schemas/PercentileThroughputCutoffs'
        - type: 'null'
      description: >-
        Preferred minimum throughput (in tokens per second). Can be a number
        (applies to p50) or an object with percentile-specific cutoffs.
        Endpoints below the threshold(s) may still be used, but are
        deprioritized in routing. When using fallback models, this may cause a
        fallback model to be used instead of the primary model if it meets the
        threshold.
      example: 100
    Quantization:
      enum:
        - int4
        - int8
        - fp4
        - mxfp4
        - nvfp4
        - fp6
        - fp8
        - mxfp8
        - fp16
        - bf16
        - fp32
        - unknown
      example: fp16
      type: string
    ProviderSort:
      description: The provider sorting strategy (price, throughput, latency)
      enum:
        - price
        - throughput
        - latency
        - exacto
      example: price
      type: string
    ProviderSortConfig:
      description: The provider sorting strategy (price, throughput, latency)
      example:
        by: price
        partition: model
      properties:
        by:
          description: The provider sorting strategy (price, throughput, latency)
          enum:
            - price
            - throughput
            - latency
            - exacto
            - null
          example: price
          type:
            - string
            - 'null'
        partition:
          description: >-
            Partitioning strategy for sorting: "model" (default) groups
            endpoints by model before sorting (fallback models remain
            fallbacks), "none" sorts all endpoints together regardless of model.
          enum:
            - model
            - none
            - null
          example: model
          type:
            - string
            - 'null'
      type: object
    ExtractionForecastStep:
      properties:
        mean:
          anyOf:
            - format: double
              type: number
            - type: string
        median:
          anyOf:
            - format: double
              type: number
            - type: string
        p_above:
          description: Probability mass above `max`.
          format: double
          type: number
        p_below:
          description: Probability mass below `min`.
          format: double
          type: number
        p10:
          anyOf:
            - format: double
              type: number
            - type: string
        p90:
          anyOf:
            - format: double
              type: number
            - type: string
        quantiles:
          description: 99 percentiles, present when the provider is asked for quantiles.
          items:
            anyOf:
              - format: double
                type: number
              - type: string
          type: array
        value:
          anyOf:
            - format: double
              type: number
            - type: string
            - type: 'null'
      required:
        - value
      type: object
    PercentileLatencyCutoffs:
      description: >-
        Percentile-based latency cutoffs. All specified cutoffs must be met for
        an endpoint to be preferred.
      example:
        p50: 5
        p90: 10
      properties:
        p50:
          description: Maximum p50 latency (seconds)
          format: double
          type:
            - number
            - 'null'
        p75:
          description: Maximum p75 latency (seconds)
          format: double
          type:
            - number
            - 'null'
        p90:
          description: Maximum p90 latency (seconds)
          format: double
          type:
            - number
            - 'null'
        p99:
          description: Maximum p99 latency (seconds)
          format: double
          type:
            - number
            - 'null'
      type: object
    PercentileThroughputCutoffs:
      description: >-
        Percentile-based throughput cutoffs. All specified cutoffs must be met
        for an endpoint to be preferred.
      example:
        p50: 100
        p90: 50
      properties:
        p50:
          description: Minimum p50 throughput (tokens/sec)
          format: double
          type:
            - number
            - 'null'
        p75:
          description: Minimum p75 throughput (tokens/sec)
          format: double
          type:
            - number
            - 'null'
        p90:
          description: Minimum p90 throughput (tokens/sec)
          format: double
          type:
            - number
            - 'null'
        p99:
          description: Minimum p99 throughput (tokens/sec)
          format: double
          type:
            - number
            - 'null'
      type: object
  securitySchemes:
    apiKey:
      description: API key as bearer token in Authorization header
      scheme: bearer
      type: http

````
