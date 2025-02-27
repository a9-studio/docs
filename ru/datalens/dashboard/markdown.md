# Markdown

{{ datalens-short-name }} позволяет использовать язык разметки Markdown в виджете [{#T}](./widget.md#text) на дашборде.
Вы можете разместить поясняющий текст, ссылки, таблицу, изображение или выделить значимые моменты с помощью форматирования.

В текстовых виджетах вы можете использовать следующие элементы:

* [Заголовки](#headings)
* [Полужирный шрифт и курсив](#emphasizing)
* [Цвет текста](#text-color)
* [Списки](#lists)
  * [Простой неупорядоченный список](#unordered-list)
  * [Вложенный неупорядоченный список](#unordered-sublist)
  * [Простой упорядоченный список](#ordered-list)
  * [Вложенный упорядоченный список](#ordered-sublist)
* [Таблицы](#tables)
* [Ссылки](#links)
* [Оформление кода](#code)
  * [Фрагмент кода как часть предложения](#inline-code)
  * [Фрагмент кода отдельным блоком](#codeblock)
* [Изображение](#image)

## Заголовки {#headings}

Вы можете использовать четыре уровня заголовков в виджете.
Для обозначения заголовка используется символ `#`.

Пример синтаксиса:

```markdown
# Заголовок 1 уровня
## Заголовок 2 уровня
### Заголовок 3 уровня
#### Заголовок 4 уровня
```

## Выделение текста {#emphasizing}

Вы можете выделить важное в тексте с помощью форматирования:

* Чтобы выделить текст **полужирным шрифтом**, используйте удвоенный символ `*`:

  ```markdown
  Этот текст выделен **полужирным шрифтом**.
  ```

* Чтобы выделить текст _курсивом_, используйте символ `_`:

  ```markdown
  Этот текст выделен _курсивом_.
  ```

* Чтобы выделить текст _**полужирным шрифтом и курсивом**_, используйте одновременно удвоенный символ `*` и символ `_`:

  ```markdown
  Этот текст выделен _**полужирным шрифтом и курсивом**_.
  Этот текст выделен **_полужирным шрифтом и курсивом_**.
  ```

## Цвет текста {#text-color}

Вы можете задать цвет текста с помощью форматирования: `{цвет}(текст)`. Поддерживаются следующие значения цвета:

* gray — серый;
* yellow — желтый;
* orange — оранжевый;
* red — красный;
* green — зеленый;
* blue — синий;
* violet — фиолетовый.

Например, следующая разметка:

```markdown
Этот текст {green}(зеленого) цвета.
```

будет отображаться так:

Этот текст <font color=green>зеленого</font> цвета.

## Списки {#lists}

Вы можете использовать несколько вариантов списков для структурирования информации на дашборде.

### Простой неупорядоченный список {#unordered-list}

Чтобы оформить неупорядоченный маркированный список, используйте символы `*`, `-` или `+`.

Например, следующая разметка:

```markdown
* Элемент 1
* Элемент 2
* Элемент 3
```

будет отображаться так:

* Элемент 1
* Элемент 2
* Элемент 3

### Вложенный неупорядоченный список {#unordered-sublist}

Чтобы оформить вложенный неупорядоченный список, добавьте отступ в начале строк с элементами вложенного списка. Допустимый размер отступа — от двух до пяти пробелов.

Например, следующая разметка:

```markdown
- Элемент 1
   - Элемент A
   - Элемент B
- Элемент 2
```

будет отображаться так:

* Элемент 1
   * Элемент A
   * Элемент B
* Элемент 2

### Простой упорядоченный список {#ordered-list}

Чтобы оформить упорядоченный список, используйте цифры с символом `.` или `)`.

Например, следующая разметка:

```markdown
1. Первый пункт
1. Второй пункт
1. Третий пункт
```

будет отображаться так:

1. Первый пункт
1. Второй пункт
1. Третий пункт

### Вложенный упорядоченный список {#ordered-sublist}

Чтобы оформить вложенный упорядоченный список, добавьте отступ в начале строк с элементами вложенного списка. Допустимый размер отступа — от трех до шести пробелов.

Например, следующая разметка:

```markdown
1. Первый пункт
   1. Вложенный пункт
   1. Вложенный пункт
1. Второй пункт
```

будет отображаться так:

1. Первый пункт

   1.1. Вложенный пункт<br>
   1.2. Вложенный пункт
1. Второй пункт

## Таблицы {#tables}

Таблица состоит из одной строки с заголовками, разделительной строки и строк с данными.

Каждая строка таблицы состоит из ячеек, отделенных друг от друга символами `|`.

В ячейках разделительной строки используются только символ `-` и символ `:`. Символ `:` ставится в начале, в конце или с обеих сторон содержимого ячейки разделительной строки, чтобы обозначить выравнивания текста в соответствующем столбце по левой стороне, по правой стороне или по центру соответственно.

Таблицу нужно отделять от предшествующего и последующего текста пустыми строками.

Например, следующая разметка:

```markdown
По левому краю | По правому краю | По центру
:--- | ---: | :---:
Текст | Текст | Текст
```

будет отображаться так:

По левому краю | По правому краю | По центру
:--- | ---: | :---:
Текст | Текст | Текст

Если необходимо добавить в ячейку таблицы перенос строки или более сложный элемент (например, список или блок кода), воспользуйтесь альтернативной разметкой:

```
#|
|| **Заголовок1** | **Заголовок2** ||
|| Текст | Текст ||
|#
```

Пример разметки с переносами и списком:

```
#|
||Текст
на двух строчках
|
- Пункт 1
- Пункт 2
- Пункт 3
- Пункт 4||
|#
```

См. подробнее в [документации YFM](https://ydocs.tech/ru/syntax/tables/multiline).

## Ссылки {#links}

С помощью ссылок вы можете указать информацию, которые имеет отношение к дашборду или чартам.
Например, добавить ссылки на другие дашборды, указать источники данных.

Ссылка состоит из двух частей:

* `[текст]` — текст ссылки.
* `(ссылка)` — URL или путь до файла, на который делается ссылка.

Например, следующая разметка:


```markdown
[ссылка на yandex.ru](https://yandex.ru).
```


будет отображаться так:


[ссылка на yandex.ru](https://yandex.ru).



## Оформление кода {#code}

Фрагмент кода можно оформить как часть предложения или как отдельный блок.

### Фрагмент кода как часть предложения {#inline-code}

Чтобы оформить фрагмент кода как часть предложения, используйте символ <code>`</code>.

Например, следующая разметка:

```markdown
Предложение с `фрагментом кода`.
```

будет отображаться так:

Предложение с `фрагментом кода`.

### Фрагмент кода отдельным блоком {#codeblock}

Чтобы оформить фрагмент кода как отдельный блок, используйте утроенный символ <code>`</code> и имя соответствующего языка программирования.

Например, следующая разметка:

```markdown
    ```kotlin
    val a: Int = 1
    ```
```

будет отображаться как фрагмент кода на языке Kotlin с подсветкой:

```kotlin
val a: Int = 1
```

## Изображение {#image}



В виджет можно добавлять изображения, размещенные в хранилище [{{ objstorage-full-name }}](../../storage/quickstart.md). С тарифами сервиса можно ознакомиться в разделе [{#T}](../../storage/pricing.md). Изображения из внешних источников не поддерживаются.




Поддерживается добавление изображений любого формата по [ссылкам на объекты](../../storage/concepts/object.md#object-url) вида `https://{{ s3-storage-host }}/<bucket>/<key>`.


Для загрузки изображения из **{{ objstorage-short-name }}** в виджет:

1. Откройте [консоль управления]({{ link-console-main }}).
1. В левом верхнем углу нажмите значок ![image](../../_assets/console-icons/dots-9.svg) и выберите сервис **{{ objstorage-short-name }}**.
1. [Создайте бакет](../../storage/operations/buckets/create.md).
1. [Загрузите изображение](../../storage/operations/objects/upload.md) в бакет.
1. Перейдите в полученный объект и нажмите кнопку **Получить ссылку**.
1. Укажите время жизни для ссылки и скопируйте ее.

   {% note warning %}

   По истечении указанного времени жизни изображение станет недоступным (максимально — 30 дней).

   {% endnote %}

1. Откройте дашборд в сервисе {{ datalens-name }} и [создайте](../operations/dashboard/add-text.md) виджет **Текст**.
1. Вставьте в виджет следующий код:

   ```markdown
   ![alt text](https://ссылка_на_изображение "Текст для подсказки при наведении" =100x200)
   ```

{% cut "Как создать постоянную ссылку" %}

Чтобы загруженное изображение оставалось доступным всегда, откройте к нему доступ с помощью [ACL](../../storage/concepts/acl.md) объекта.

{% note warning %}

Публичный доступ к файлу предоставляется неограниченному кругу анонимных пользователей. Подробнее о способах управления доступом в {{ objstorage-name }} читайте в [документации сервиса](../../storage/security/overview.md).

{% endnote %}

1. Откройте [консоль управления]({{ link-console-main }}).
1. В левом верхнем углу нажмите значок ![image](../../_assets/console-icons/dots-9.svg) и выберите сервис **{{ objstorage-short-name }}**.
1. [Создайте бакет](../../storage/operations/buckets/create.md). При выборе имени бакета придерживайтесь [рекомендаций](../../storage/concepts/bucket.md#naming).
1. [Загрузите изображение](../../storage/operations/objects/upload.md) в бакет.
1. Настройте ACL созданного объекта:

   1. Нажмите значок ![image](../../_assets/console-icons/ellipsis.svg) справа от имени объекта и выберите **{{ ui-key.yacloud.storage.bucket.button_action-permissions }}**.
   1. Для группы `allUsers` выдайте разрешение `READ`.

1. Составьте ссылку на объект в бакете вида `https://{{ s3-storage-host }}/<бакет>/<ключ>`, где:

   * `<бакет>` — имя бакета.
   * `<ключ>` — [ключ](../../storage/concepts/object.md#key) объекта (путь к файлу).

1. Откройте дашборд в сервисе {{ datalens-name }} и [создайте](../operations/dashboard/add-text.md) виджет **Текст**.
1. Вставьте в виджет следующий код:

   ```markdown
   ![alt text](https://ссылка_на_изображение "Текст для подсказки при наведении" =100x200)
   ```

{% endcut %}




