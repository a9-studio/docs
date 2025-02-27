---
editable: false
sourcePath: en/_api-ref-grpc/ai/llm/v1alpha/api-ref/v1alpha/grpc/TextGenerationAsync/instruct.md
---

# YandexGPT API, gRPC: TextGenerationAsyncService.Instruct

RPC method for instructing the model to generate text.

## gRPC request

**rpc Instruct ([InstructRequest](#yandex.cloud.ai.llm.v1alpha.InstructRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## InstructRequest {#yandex.cloud.ai.llm.v1alpha.InstructRequest}

```json
{
  "model": "string",
  "generation_options": {
    "partial_results": "bool",
    "temperature": "google.protobuf.DoubleValue",
    "max_tokens": "google.protobuf.Int64Value"
  },
  // Includes only one of the fields `instruction_text`, `instruction_uri`
  "instruction_text": "string",
  "instruction_uri": "string",
  // end of the list of possible fields
  // Includes only one of the fields `request_text`
  "request_text": "string"
  // end of the list of possible fields
}
```

Request for instructing the model to generate text.

#|
||Field | Description ||
|| model | **string**

The name or identifier of the model to be used for text generation.
Possible value for now: `general`. ||
|| generation_options | **[GenerationOptions](#yandex.cloud.ai.llm.v1alpha.GenerationOptions)**

Configuration options for text generation. ||
|| instruction_text | **string**

The text-based instruction for text generation.

Includes only one of the fields `instruction_text`, `instruction_uri`.

Text precondition or context of the request.
For example, if the instruction is "You are the youngest Nobel laureate",
the request text might be "Tell us about your daily routine". ||
|| instruction_uri | **string**

A URI containing instructions for text generation.

Includes only one of the fields `instruction_text`, `instruction_uri`.

Text precondition or context of the request.
For example, if the instruction is "You are the youngest Nobel laureate",
the request text might be "Tell us about your daily routine". ||
|| request_text | **string**

The text-based request for text generation.

Includes only one of the fields `request_text`.

Request for text generation. ||
|#

## GenerationOptions {#yandex.cloud.ai.llm.v1alpha.GenerationOptions}

Defines the options for text generation.

#|
||Field | Description ||
|| partial_results | **bool**

Enables streaming of partially generated text. ||
|| temperature | **[google.protobuf.DoubleValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/double-value)**

Affects creativity and randomness of responses. Should be a double number between 0 (inclusive) and 1 (inclusive).
Lower values produce more straightforward responses, while higher values lead to increased creativity and randomness. ||
|| max_tokens | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

Sets the maximum limit on the total number of tokens used for both the input prompt and the generated response.
Must be greater than zero and not exceed 7400 tokens. ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "created_at": "google.protobuf.Timestamp",
  "created_by": "string",
  "modified_at": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": "google.protobuf.Any",
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "alternatives": [
      {
        "text": "string",
        "score": "double",
        "num_tokens": "int64"
      }
    ],
    "num_prompt_tokens": "int64"
  }
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| created_by | **string**

ID of the user or service account who initiated the operation. ||
|| modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[InstructResponse](#yandex.cloud.ai.llm.v1alpha.InstructResponse)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## InstructResponse {#yandex.cloud.ai.llm.v1alpha.InstructResponse}

Response containing generated text alternatives and token count.

#|
||Field | Description ||
|| alternatives[] | **[Alternative](#yandex.cloud.ai.llm.v1alpha.Alternative)**

A list of alternative text responses. ||
|| num_prompt_tokens | **int64**

The number of tokens used in the prompt, including both the [instruction_text](#yandex.cloud.ai.llm.v1alpha.InstructRequest) and [request_text](#yandex.cloud.ai.llm.v1alpha.InstructRequest). ||
|#

## Alternative {#yandex.cloud.ai.llm.v1alpha.Alternative}

Represents an alternative generated response, including its score and token count.

#|
||Field | Description ||
|| text | **string**

The generated text response. ||
|| score | **double**

The score or confidence of the generated text. ||
|| num_tokens | **int64**

The number of tokens in the generated response. ||
|#