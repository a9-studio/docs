---
editable: false
sourcePath: en/_api-ref/datalens/function-ref/AT_DATE.md
---

# AT_DATE



#### Syntax {#syntax}

{% list tabs %}

- Standard

  ```
  AT_DATE( measure, date_dimension, date_expr )
  ```

- Extended

  ```
  AT_DATE( measure, date_dimension, date_expr
           [ BEFORE FILTER BY ... ]
           [ IGNORE DIMENSIONS ... ]
         )
  ```

  More info:
  - [BEFORE FILTER BY](time-series-functions.md#syntax-before-filter-by)
  - [IGNORE DIMENSIONS](time-series-functions.md#syntax-ignore-dimensions)

{% endlist %}

#### Description {#description}
Re-evaluate `measure` for a date/time specified by `date_expr`. It allows to get the measure at the beginning and at the end of a period, or for the specified date.
The `date_dimension` argument is the dimension along which the offset is made.

You can use the following as the `date_expr` argument:

* Certain date.
* Function [TODAY](TODAY.md) to obtain the current date.
* Functions to calculate date and time.

See also [AGO](AGO.md), [LAG](LAG.md).

**Argument types:**
- `measure` — `Any`
- `date_dimension` — `Date | Datetime`
- `date_expr` — `Date | Datetime`


**Return type**: Same type as (`measure`)

{% note info %}

The first argument must be a measure (aggregated expression), otherwise an error will be raised.

{% endnote %}


#### Examples {#examples}

```
AT_DATE(SUM([Sales]), [Order Date], #2019-01-01#)
```

```
AT_DATE(SUM([Sales]), [Order Date], TODAY())
```

```
AT_DATE(SUM([Sales]), [Order Date], DATETRUNC([Order Date], "month"))
```


#### Data source support {#data-source-support}

`ClickHouse 21.8`, `Files`, `Google Sheets`, `Yandex Metrica`, `Microsoft SQL Server 2017 (14.0)`, `MySQL 5.7`, `Oracle Database 12c (12.1)`, `PostgreSQL 9.3`, `Yandex Documents`, `YDB`.
