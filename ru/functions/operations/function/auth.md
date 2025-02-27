---
title: Как аутентифицироваться при вызове приватной функции через HTTPS в {{ sf-full-name }}
description: Следуя данной инструкции, вы сможете аутентифицироваться при вызове приватной функции через HTTPS.
---

# Аутентифицироваться при вызове приватной функции через HTTPS

Чтобы вызвать приватную функцию через HTTPS, необходимо аутентифицироваться. Для этого получите:

* [IAM-токен](../../../iam/concepts/authorization/iam-token.md):
    * [Инструкция](../../../iam/operations/iam-token/create.md) для аккаунта на Яндексе.
    * [Инструкция](../../../iam/operations/iam-token/create-for-sa.md) для сервисного аккаунта.
    * [Инструкция](../../../iam/operations/iam-token/create-for-federation.md) для федеративного аккаунта.

    Полученный IAM-токен передайте в заголовке `Authorization` в следующем формате:
    ```
    Authorization: Bearer <IAM-токен>
    ```
    IAM-токен действует не больше 12 часов.

* [API-ключ](../../../iam/operations/api-key/create) для сервисного аккаунта.

    Полученный API-ключ передайте в заголовке `Authorization` в следующем формате:
    ```
    Authorization: Api-Key <API-ключ>
    ```

    {% include [api-keys-disclaimer](../../../_includes/iam/api-keys-disclaimer.md) %}

