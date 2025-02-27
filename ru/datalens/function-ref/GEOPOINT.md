---
editable: false
sourcePath: ru/_api-ref/datalens/function-ref/GEOPOINT.md
---

# GEOPOINT



#### Синтаксис {#syntax}


```
GEOPOINT( value_1 [ , value_2 ] )
```

#### Описание {#description}
Формирует значение типа геоточка. Принимает на вход строку, либо значение типа "геоточка", либо координаты — широту `value_1` и долготу `value_2`. Если на вход подается одна строка, в ней должен содержаться список из двух чисел, координат (широты и долготы) в JSON-синтаксисе.

**Типы аргументов:**
- `value_1` — `Дробное число | Геоточка | Целое число | Строка`
- `value_2` — `Дробное число | Целое число | Строка`


**Возвращаемый тип**: `Геоточка`

#### Примеры {#examples}

```
GEOPOINT("[55.75222,37.61556]") = "[55.75222,37.61556]"
```

```
GEOPOINT(55.75222, 37.61556) = "[55.75222,37.61556]"
```


#### Поддержка источников данных {#data-source-support}

`ClickHouse 21.8`, `Файлы`, `Google Sheets`, `Microsoft SQL Server 2017 (14.0)`, `MySQL 5.7`, `Oracle Database 12c (12.1)`, `PostgreSQL 9.3`, `Яндекс Документы`, `YDB`.
