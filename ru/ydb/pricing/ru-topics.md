---
title: Правила оценки стоимости операций с топиками в {{ ydb-full-name }}
description: Из статьи вы узнаете, как рассчитывается стоимость операций с топиками.
editable: false
---

# Правила оценки стоимости операций с топиками



## Режимы тарификации

Тарификация операций с данными в [топиках {{ ydb-short-name }}]({{ ydb.docs }}/concepts/topic) с использованием Request Units {{ ydb-short-name }} применяется для топиков, использующих _режим тарификации по фактическому использованию (On-demand)_. В этом режиме по умолчанию создаются топики через {{ ydb-short-name }} CLI/SDK, а также при создании [потока CDC]({{ ydb.docs }}/concepts/cdc).

Если топик создается как хранилище для [потока данных](../../data-streams/concepts/glossary.md#stream-concepts) {{ yds-short-name }}, он по умолчанию получает [_режим тарификации по выделенным ресурсам_](../../data-streams/pricing.md#rules). Для находящихся в режиме по выделенным ресурсам топиков начисление Request Units {{ ydb-short-name }} не производится, оплата делается на почасовой основе в рамках сервиса {{ yds-full-name }}.

Смена режима тарификации может быть произведена для любого топика явно вызовом команды {{ ydb-short-name }} CLI [ydb topic alter]({{ ydb.docs }}/reference/ydb-cli/topic-alter) или метода SDK.

## Расчет потребления Request Units {#rules}

Для топика, находящегося в режиме тарификации по фактическому использованию, {{ ydb-short-name }} осуществляет расчет стоимости операций в Request Units по описанным ниже правилам.

### TopicAPI {#topic-api}

TopicAPI используется при работе через {{ ydb-short-name }} SDK и CLI, и предоставляет потоковые методы чтения и записи данных. Стоимость обращения к этим методам в Request Units (RU) вычисляется по следующим правилам:

1. Каждый вызов метода чтения или записи, то есть открытие потока записи или чтения, стоит 1 RU.
1. В рамках каждого открытого потокового метода передачи (сессии) накапливается объем переданных (записанных или считанных) данных. В момент превышения этим объемом границ блоков начисляется дополнительный 1 RU за каждый блок. При этом размеры блоков отличаются для чтения и записи:

    Направление | Размер блока
    --- | ---
    Чтение | 8КБ
    Запись | 4КБ

**Пример расчета**

1. Вызван новый потоковый метод записи. В этот момент начисляется 1 RU.
1. В рамках метода передан пакет данных для записи объемом 1 КБ. Так как граница блока записи 4 КБ не превышена, дополнительных начислений RU не производится.
1. В рамках метода передан пакет данных для записи объемом 8 КБ. Общий объем переданных в рамках метода данных стал равен 9 КБ, что включает 2 блока по 4 КБ. Производится начисление 2 RU, по 1 RU за каждый блок.
1. В рамках метода передан пакет данных для записи объемом 6 КБ. Общий объем переданных в рамках метода данных стал равен 15 КБ, что включает 3 блока данных по 4 КБ, что стоит 3 RU. Так как 2 RU уже ранее передавались, передается разница 3 RU - 2 RU = 1 RU.

Расчет для чтения производится аналогично, но с размером блока в 8 КБ.

### DataStreamsAPI {#data-streams-api}

DataStreamsAPI используется при обращении к топику через интерфейс потоков данных, совместимый с AWS Kinesis. На данном интерфейсе не поддерживаются потоковые методы чтения и записи, и передача каждого блока данных требует вызова отдельного унарного метода (запрос-ответ). Стоимость обращения к этим методам в Request Units (RU) вычисляется по следующим правилам:

1. Каждый вызов метода чтения или записи для передачи или получения очередного блока данных стоит 1 RU.
1. Рассчитывается объем блоков данных, переданных в запросе к методу записи, или полученных в ответе на вызов метода чтения. Размеры блоков отличаются для чтения и записи:

    Направление | Размер блока
    --- | ---
    Чтение | 8КБ
    Запись | 4КБ

1. За каждый полный переданный блок данных начисляется по 1 RU.

**Пример расчета**

1. Вызван метод KinesisAPI `getRecords`.
1. В ответе получен пакет данных размером в 20 KБ. Этот объем содержит два полных блока чтения размером 8 КБ.
1. Стоимость вызова в RU = 1 RU за вызов + 2 RU за два полученных полных блока данных = 3 RU.

### KafkaAPI {#kafka-api}

На интерфейсе KafkaAPI не поддерживаются потоковые методы чтения и записи, а передача каждого блока данных требует вызова отдельного унарного метода (запрос-ответ). Стоимость обращения к этим методам в Request Units (RU) вычисляется по следующим правилам:

1. Каждый вызов метода чтения или записи для передачи или получения очередного блока данных стоит 1 RU (вступает в силу с 01.07.2024).
1. Рассчитывается объем блоков данных, переданных в запросе к методу записи, или полученных в ответе на вызов метода чтения. Размеры блоков для чтения и записи отличаются:

    Направление | Размер блока
    --- | ---
    Чтение | 8КБ
    Запись | 4КБ

1. За каждый полный переданный блок данных начисляется по 1 RU.

**Пример расчета**

1. Вызван метод KafkaAPI `FETCH`.
1. В ответе получен пакет данных размером 20 KБ. Этот объем содержит два полных блока чтения размером 8 КБ.
1. Стоимость вызова в RU = 1 RU за вызов + 2 RU за два полученных полных блока данных = 3 RU.


Расчет для записи производится аналогично, но с размером блока в 4 КБ.
