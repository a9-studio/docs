---
title: Инструкция по получению идентификатора каталога в {{ yandex-cloud }}
description: Из статьи вы узнаете, как получить идентификатор каталога в {{ yandex-cloud }}.
---

# Получение идентификатора каталога

{% list tabs group=instructions %}

- Консоль управления {#console}

  1. Перейдите в [консоль управления]({{ link-console-cloud }}) и в списке слева выберите нужный [каталог](../../concepts/resources-hierarchy.md#folder). На открывшейся странице идентификатор каталога указан сверху, рядом с именем каталога.
  
  1. Чтобы скопировать идентификатор, наведите на него указатель и нажмите значок ![image](../../../_assets/console-icons/copy.svg).
  
  Также получить идентификатор можно из URL страницы каталога в консоли управления:
  
  ```text
  {{ link-console-main }}/folders/<идентификатор_каталога>
  ```

- CLI {#cli}

  {% include [cli-install](../../../_includes/cli-install.md) %}

  Если вы знаете имя [каталога](../../concepts/resources-hierarchy.md#folder), получите его идентификатор с помощью команды `get`:

  ```bash
  yc resource-manager folder get my-folder
  ```

  Результат:

  ```text
  id: b1gd129pp9ha********
  ...
  ```

  Если вы не знаете имя каталога, получите список каталогов с идентификаторами для облака по умолчанию:

  ```bash
  yc resource-manager folder list
  ```

  Результат:

  ```text
  +----------------------+--------------------+------------------+--------+
  |          ID          |        NAME        |      LABELS      | STATUS |
  +----------------------+--------------------+------------------+--------+
  | b1gd129pp9ha******** | my-folder          |                  | ACTIVE |
  | b1g66mft1vop******** | default            |                  | ACTIVE |
  +----------------------+--------------------+------------------+--------+
  ```

  Чтобы посмотреть список каталогов в другом облаке, укажите идентификатор каталога в `cloud-id`:

  ```bash
  yc resource-manager folder list --cloud-id b1glku4lgd6g********
  ```

- API {#api}

  Чтобы получить список [каталогов](../../concepts/resources-hierarchy.md#folder) с идентификаторами, воспользуйтесь методом REST API [list](../../api-ref/Folder/list.md) для ресурса [Folder](../../api-ref/Folder/index.md) или вызовом gRPC API [FolderService/List](../../api-ref/grpc/Folder/list.md).

{% endlist %}
