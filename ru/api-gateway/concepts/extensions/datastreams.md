---
title: Расширение x-yc-apigateway-integration:cloud_datastreams
description: Из статьи вы узнаете, для чего нужно расширение x-yc-apigateway-integration:cloud_datastreams, какие оно поддерживает параметры, как выглядит его спецификация.
---

# Расширение x-yc-apigateway-integration:cloud_datastreams

 Расширение `x-yc-apigateway-integration:cloud_datastreams` позволяет обращаться к {{ yds-full-name }} для выполнения операции с [потоком](../../../data-streams/concepts/glossary.md#stream-concepts). На данный момент поддерживается только операция [PutRecord](../../../data-streams/kinesisapi/methods/putrecord.md). 

{% include [add-extentions-console](../../../_includes/api-gateway/add-extentions-console.md) %}

## Поддерживаемые параметры {#parameters}

{% include [param-table](../../../_includes/api-gateway/parameters-table.md) %}

Параметр | Тип | Описание
----|----|----
`action` | `string` | Выполняемая операция. Возможные значения: `PutRecord`.
`stream_name` | `string` | Имя потока {{ yds-name }}.
`partition_key` | `string` | Необязательный параметр. [Ключ сегмента](../../../data-streams/concepts/glossary#partition-key). Если не указан, запись будет выполнена в случайный сегмент. В `partition_key` осуществляется подстановка параметров.
`payload_format_type` | `string` | Необязательный параметр. Тип содержимого записи. Если значение — `body`, в поток записывается только тело запроса, если `request` — весь [запрос](./cloud-functions.md#request_v1) в формате JSON. Значение по умолчанию — `body`.
`service_account_id` | `string` | Идентификатор сервисного аккаунта. Используется для авторизации при выполнении операции с потоком {{ yds-name }}. Если параметр не указан, используется значение [верхнеуровневого параметра](./index.md#top-level) `service_account_id`.

## Спецификация расширения {#spec}

Пример спецификации:

```yaml
  /pets-stream/{petId}:
    post:
      x-yc-apigateway-integration:
        type: cloud_datastreams
        action: PutRecord
        stream_name: /{{ region-id }}/b1v1emj927uv********/ett01h3uz7qm********/pets-stream
        partition_key: '{petId}'
        service_account_id: ajeqvh23fi2********
      parameters:
      - description: petId
        explode: false
        in: path
        name: petId
        required: true
        schema:
          type: string
        style: simple
```
