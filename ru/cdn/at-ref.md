---
title: Справочник аудитных логов {{ cdn-full-name }} в {{ at-full-name }}
description: На этой странице приведен справочник событий сервиса {{ cdn-name }}, отслеживаемых в {{ at-name }}.
---

# Справочник аудитных логов {{ at-full-name }}

В {{ at-name }} поддерживается отслеживание событий уровня конфигурации (Control Plane) для {{ cdn-full-name }}. Подробнее см. [{#T}](../audit-trails/concepts/format.md).

Общий вид значения поля `event_type` (_тип события_):

```text
{{ at-event-prefix }}.audit.cdn.<имя_события>
```

{% include [cdn-events](../_includes/audit-trails/events/cdn-events.md) %}