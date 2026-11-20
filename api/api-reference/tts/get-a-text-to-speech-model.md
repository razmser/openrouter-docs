> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Get a text-to-speech model

> Returns a text-to-speech model with each endpoint's own inputs and speech output parameters.



## OpenAPI

````yaml /openapi/openapi.yaml get /audio/speech/models/{author}/{slug}
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
  /audio/speech/models/{author}/{slug}:
    get:
      tags:
        - TTS
      summary: Get a text-to-speech model
      description: >-
        Returns a text-to-speech model with each endpoint's own inputs and
        speech output parameters.
      operationId: getSpeechModel
      parameters:
        - description: Model author/organization
          in: path
          name: author
          required: true
          schema:
            description: Model author/organization
            example: openai
            type: string
        - description: Model slug
          in: path
          name: slug
          required: true
          schema:
            description: Model slug
            example: gpt-4o-mini-tts
            type: string
      responses:
        '200':
          content:
            application/json:
              example:
                created: 1742428800
                description: Text-to-speech model with steerable delivery.
                endpoints:
                  - input_modalities:
                      - type: text
                    output_modalities:
                      - supported_parameters:
                          instructions:
                            type: unknown
                          response_format:
                            type: enum
                            values:
                              - mp3
                              - pcm
                          speed:
                            max: 4
                            min: 0.25
                            type: range
                          voice:
                            type: enum
                            values:
                              - alloy
                              - coral
                        type: speech
                    provider_name: OpenAI
                    provider_slug: openai
                id: openai/gpt-4o-mini-tts
                input_modalities:
                  - type: text
                name: 'OpenAI: GPT-4o mini TTS'
                output_modalities:
                  - supported_parameters:
                      instructions:
                        type: unknown
                      response_format:
                        type: enum
                        values:
                          - mp3
                          - pcm
                      speed:
                        max: 4
                        min: 0.25
                        type: range
                      voice:
                        type: enum
                        values:
                          - alloy
                          - coral
                    type: speech
              schema:
                $ref: '#/components/schemas/SpeechModelResponse'
          description: A text-to-speech model and its endpoints
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
      security: []
components:
  schemas:
    SpeechModelResponse:
      description: >-
        A text-to-speech model. Its members are the envelope of its endpoints':
        enums are unioned and ranges widened, so a value inside a range may be
        accepted by no single endpoint. Each record in `endpoints` lists exactly
        what that endpoint accepts.
      example:
        created: 1742428800
        description: Text-to-speech model with steerable delivery.
        endpoints:
          - input_modalities:
              - type: text
            output_modalities:
              - supported_parameters:
                  instructions:
                    type: unknown
                  response_format:
                    type: enum
                    values:
                      - mp3
                      - pcm
                  speed:
                    max: 4
                    min: 0.25
                    type: range
                  voice:
                    type: enum
                    values:
                      - alloy
                      - coral
                type: speech
            provider_name: OpenAI
            provider_slug: openai
        id: openai/gpt-4o-mini-tts
        input_modalities:
          - type: text
        name: 'OpenAI: GPT-4o mini TTS'
        output_modalities:
          - supported_parameters:
              instructions:
                type: unknown
              response_format:
                type: enum
                values:
                  - mp3
                  - pcm
              speed:
                max: 4
                min: 0.25
                type: range
              voice:
                type: enum
                values:
                  - alloy
                  - coral
            type: speech
      properties:
        created:
          description: Unix timestamp (seconds) of when the model was created
          type: integer
        description:
          type: string
        endpoints:
          description: >-
            Each endpoint serving the model, with exactly the inputs and
            parameters it accepts. Some endpoints route only after the caller
            accepts a provider requirement such as a self-attestation; until
            then, a request to them is rejected with a 403 that names the
            requirement.
          items:
            $ref: '#/components/schemas/SpeechModelEndpoint'
          type: array
        id:
          description: Model slug
          example: openai/gpt-4o-mini-tts
          type: string
        input_modalities:
          items:
            $ref: '#/components/schemas/SpeechInputModality'
          type: array
        name:
          example: 'OpenAI: GPT-4o mini TTS'
          type: string
        output_modalities:
          items:
            $ref: '#/components/schemas/SpeechOutputModality'
          type: array
      required:
        - id
        - name
        - description
        - created
        - input_modalities
        - output_modalities
        - endpoints
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
    SpeechModelEndpoint:
      description: >-
        One endpoint serving a speech model, with the inputs and parameters it
        accepts.
      example:
        input_modalities:
          - type: text
        output_modalities:
          - supported_parameters:
              instructions:
                type: unknown
              response_format:
                type: enum
                values:
                  - mp3
                  - pcm
              speed:
                max: 4
                min: 0.25
                type: range
              voice:
                type: enum
                values:
                  - alloy
                  - coral
            type: speech
        provider_name: OpenAI
        provider_slug: openai
      properties:
        input_modalities:
          items:
            $ref: '#/components/schemas/SpeechInputModality'
          type: array
        output_modalities:
          items:
            $ref: '#/components/schemas/SpeechOutputModality'
          type: array
        provider_name:
          description: Provider display name
          example: OpenAI
          type: string
        provider_slug:
          description: Provider slug
          example: openai
          type: string
      required:
        - provider_name
        - provider_slug
        - input_modalities
        - output_modalities
      type: object
    SpeechInputModality:
      description: >-
        An input the model accepts. `audio` and `image` are `input_references`
        for voice cloning and voice design.
      example:
        type: text
      oneOf:
        - description: The `input` text.
          properties:
            turns:
              description: >-
                `optional`: `input` may also be a multi-speaker turn array,
                which cannot be combined with `input_references`. `required`:
                `input` must be a turn array with at least two distinct voices.
                Absent: `input` is a string.
              enum:
                - required
                - optional
              type: string
            type:
              enum:
                - text
              type: string
          required:
            - type
          type: object
        - properties:
            supported_inputs:
              description: >-
                `references` is how many audio clips a request may send. With
                more than one, some providers require the text to address every
                clip with an `@AudioN` placeholder.
              properties:
                references:
                  $ref: '#/components/schemas/SpeechReferenceCount'
              required:
                - references
              type: object
            type:
              enum:
                - audio
              type: string
          required:
            - type
            - supported_inputs
          type: object
        - properties:
            supported_inputs:
              properties:
                audio:
                  description: >-
                    `required`: an image reference is accepted only together
                    with an audio reference. `excluded`: only without one.
                    Absent: either.
                  enum:
                    - required
                    - excluded
                  type: string
                references:
                  $ref: '#/components/schemas/SpeechReferenceCount'
              required:
                - references
              type: object
            type:
              enum:
                - image
              type: string
          required:
            - type
            - supported_inputs
          type: object
    SpeechOutputModality:
      example:
        supported_parameters:
          voice:
            type: enum
            values:
              - alloy
              - coral
        type: speech
      properties:
        supported_parameters:
          $ref: '#/components/schemas/SpeechSupportedParameters'
        type:
          enum:
            - speech
          type: string
      required:
        - type
        - supported_parameters
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
    SpeechReferenceCount:
      example:
        max: 1
        min: 1
        type: integer
      properties:
        max:
          type: integer
        min:
          type: integer
        type:
          enum:
            - integer
          type: string
      required:
        - type
        - min
      type: object
    SpeechSupportedParameters:
      example:
        instructions:
          type: unknown
        response_format:
          type: enum
          values:
            - mp3
            - pcm
        speed:
          max: 4
          min: 0.25
          type: range
        voice:
          type: enum
          values:
            - alloy
            - coral
      properties:
        instructions:
          $ref: '#/components/schemas/SpeechUnknownParameter'
        response_format:
          $ref: '#/components/schemas/SpeechEnumParameter'
        speed:
          $ref: '#/components/schemas/SpeechRangeParameter'
        voice:
          $ref: '#/components/schemas/SpeechVoiceParameter'
      type: object
    SpeechUnknownParameter:
      example:
        type: unknown
      properties:
        type:
          enum:
            - unknown
          type: string
      required:
        - type
      type: object
    SpeechEnumParameter:
      example:
        type: enum
        values:
          - alloy
          - coral
      properties:
        type:
          enum:
            - enum
          type: string
        values:
          items:
            type: string
          type: array
      required:
        - type
        - values
      type: object
    SpeechRangeParameter:
      description: >-
        The accepted `speed` range. Absent: the provider documents no range;
        some providers still forward `speed`.
      example:
        max: 4
        min: 0.25
        type: range
      properties:
        max:
          format: double
          type: number
        min:
          format: double
          type: number
        type:
          enum:
            - range
          type: string
      required:
        - type
        - min
        - max
      type: object
    SpeechVoiceParameter:
      description: >-
        `enum` lists the documented voices in `values`; some providers also
        accept voice IDs not listed there (custom or cloned voices). `unknown`
        means the field is accepted but no voices are listed.
      example:
        type: enum
        values:
          - alloy
          - coral
      properties:
        references:
          description: >-
            `excluded`: `voice` is rejected when the request also sends a
            nonempty `input_references`. Absent: they can be combined.
          enum:
            - excluded
          type: string
        type:
          enum:
            - enum
            - unknown
          type: string
        values:
          items:
            type: string
          type: array
      required:
        - type
      type: object
  securitySchemes:
    apiKey:
      description: API key as bearer token in Authorization header
      scheme: bearer
      type: http

````
