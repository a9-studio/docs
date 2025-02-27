---
title: Уровни производительности vCPU
description: Из статьи вы узнаете об уровнях производительности vCPU и доступных конфигурациях на разных платформах.
---

# Уровни производительности vCPU


При создании каждой виртуальной машины необходимо выбирать уровень производительности vCPU. Этот уровень определяет долю вычислительного времени физических ядер, которую гарантирует vCPU.

* Виртуальные машины с уровнем производительности меньше 100% имеют доступ к вычислительной мощности физических ядер как минимум на протяжении указанного процента от единицы времени.

    > При уровне производительности 20% ВМ будет иметь доступ к физическим ядрам как минимум 20% времени — 200 миллисекунд в течение каждой секунды. Тактовая частота процессора в это время не ограничивается и соответствует выбранной платформе, например, 2 ГГц для платформы Intel Ice Lake (`standard-v3`).

    ВМ с уровнем производительности меньше 100% предназначены для запуска приложений, не требующих высокой производительности и не чувствительных к задержкам. Такие машины обойдутся дешевле.

* Виртуальные машины с уровнем производительности 100% имеют непрерывный доступ (100% времени) к вычислительной мощности физических ядер. Такие ВМ предназначены для запуска приложений, требующих высокой производительности на протяжении всего времени работы.

Реально наблюдаемая производительность может быть выше гарантированного уровня. В зависимости от выбранной [платформы](vm-platforms.md) доступные конфигурации вычислительных ресурсов для разных уровней могут меняться.

Доступный объем диска не зависит от уровня производительности виртуальной машины. Ограничения приведены в разделе [{#T}](limits.md).

## Минимальные и максимальные конфигурации {#minmax-configurations}

{% note info %}

Минимальные конфигурации указаны для уровня производительности 5%, максимальные — для 100%.

{% endnote %}

* Платформа Intel Broadwell (`standard-v1`):

    Конфигурация | vCPU | RAM, ГБ
    --- | --- | --- 
    Мин. | 2 | 1
    Макс. | 32 | 256

* Платформа Intel Cascade Lake (`standard-v2`):

    Конфигурация | vCPU | RAM, ГБ
    --- | --- | --- 
    Мин. | 2 | 0.5
    Макс. | 80 | 1280

* Платформа Intel Ice Lake (`standard-v3`):

    Конфигурация | vCPU | RAM, ГБ
    --- | --- | --- 
    Мин. | 2 | 1
    Макс. | 96 | 640

* Платформа {{ highfreq-ice-lake }} (`highfreq-v3`):

    Конфигурация | vCPU | RAM, ГБ
    --- | --- | --- 
    Мин. | 2 | 2
    Макс. | 56 | 448

## Доступные конфигурации {#available-configurations}

* Платформа Intel Broadwell (`standard-v1`):

    Уровень</br> производительности | vCPU | RAM на 1 ядро, ГБ
    --- | --- | ---
    5% | 2, 4 | 0.5, 1, 1.5, 2
    20% | 2, 4 | 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4
    100% | 2, 4, 6, 8, 10, 12, 14,<br> 16, 20, 24, 28, 32 | 1, 2, 3, 4, 5, 6, 7, 8

* Платформа Intel Cascade Lake (`standard-v2`):

    Уровень<br> производительности | vCPU | RAM на 1 ядро, ГБ
    --- | --- | ---
    5% | 2, 4 | 0.25, 0.5, 1, 1.5, 2
    20% | 2, 4 | 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4
    50% | 2, 4 | 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4
    100% | 2, 4, 6, 8, 10, 12, 14,<br> 16, 20, 24, 28, 32, 36,<br> 40, 44, 48, 52, 56, 60,<br> 64, 68, 72, 76, 80 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12, 13, 14, 15, 16

* Платформа Intel Ice Lake (`standard-v3`):

    Уровень<br> производительности | vCPU | RAM на 1 ядро, ГБ
    --- | --- | ---
    20% | 2, 4 | 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4
    50% | 2, 4 | 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4
    100% | 2, 4, 6, 8, 10, 12, 14, 16, 20 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12, 13, 14, 15, 16
    100% | 24 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13
    100% | 28 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11
    100% | 32 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
    100% | 36, 40 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12, 13, 14, 15, 16 
    100% | 44 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12, 13, 14
    100% | 48 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12, 13
    100% | 52 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12
    100% | 56 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11
    100% | 60, 64 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
    100% | 68 | 1, 2, 3, 4, 5, 6, 7, 8, 9
    100% | 72, 76, 80 | 1, 2, 3, 4, 5, 6, 7, 8
    100% | 84, 88 | 1, 2, 3, 4, 5, 6, 7
    100% | 92, 96 | 1, 2, 3, 4, 5, 6

* Платформа {{ highfreq-ice-lake }} (`highfreq-v3`):

    vCPU | RAM на 1 ядро, ГБ
    --- | --- 
    2, 4, 6, 8, 10, 12, 14,<br> 16, 20, 24, 28, 32, 36,<br> 40, 44, 48, 52, 56 | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10,<br> 11, 12, 13, 14, 15, 16