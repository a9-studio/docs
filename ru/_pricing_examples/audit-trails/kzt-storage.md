> ((25&nbsp;000 - 1&nbsp;000) / 100&nbsp;000) × {{ sku|KZT|audit-trails.events.data_plane.v1|string }} = 0,24 × {{ sku|KZT|audit-trails.events.data_plane.v1|string }} = {% calc [currency=KZT] 0,24 × {{ sku|KZT|audit-trails.events.data_plane.v1|number }} %}
>
> Итого: {% calc [currency=KZT] 0,24 × {{ sku|KZT|audit-trails.events.data_plane.v1|number }} %}

Где:

* 25&nbsp;000 — общее количество доставленных событий {{ objstorage-name }}.
* 1&nbsp;000 — количество доставленных событий уровня конфигурации, которые не тарифицируются.
* {{ sku|KZT|audit-trails.events.data_plane.v1|string }} — цена за доставку 100&nbsp;000 событий.
* 100&nbsp;000 — делим, чтобы привести количество событий к единице тарификации.