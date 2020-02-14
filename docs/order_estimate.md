Оценка стоимости заказа
====

Структура запроса соответствует [Протоколу](docs/request.md)

---

## Body json object

Param | Value
----- | ------
tariffId | man | integer64 | Идентификатор тарифа
route | man | array Point / json | массив точек маршрута
time | opt | string | Время заказа в формате YYYY-MM-DDThh:mm:ss.sss ([ISO-8601](https://ru.wikipedia.org/wiki/ISO_8601)) 
optionIds | man | array int | Список идентификаторов опций

### Point / json

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
lat | man | number | Широта
lon | man | number | Долгота

### Пример

```
{
  "method": "Orders.estimate",
  "version": "1.0",
  "params": {
    "tariffId": 22525529,
    "route": [
      {
        "lat": 54.89359040108592,
        "lon": 73.18920135498047
      }, {
        "lat": 55.06165809883029,
        "lon": 73.18920135498047
      }
    ],
    "time": "2019-12-02T12:00:00",
    "optionIds": [1,6,17]
  }
}
```

---

## Ответ

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
result | man | Result | Ответ содержит стоимость и чек

### Result / json

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
cost | man | ResultCostKind / string | Тип стоимости
details | man | array ResultItem / json | Позиции чека

### ResultCostKind / string 

Param | Description
----- | -----------
minimum | Минималка (не удалось рассчитать маршрут)
total | Полная стоимость поездки

### ResultItem / json 

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
title | man | string | Наименование
units | man | int | Количество
cost | man | number | СТоимость

### Пример ответа

```
{
  "result": {
    "client": {
      "cost": 6.8,
      "kind": "total",
      "details": [
        {
          "title": "check.item.per_unit.distance",
          "units": 8,
          "cost": 6.72
        },
        {
          "title": "check.item.round_unit.price",
          "units": 1,
          "cost": 0.08
        }
      ]
    },
    "driver": {
      "cost": 6.8,
      "kind": "total",
      "details": [
        {
          "title": "check.item.per_unit.distance",
          "units": 8,
          "cost": 6.72
        },
        {
          "title": "check.item.round_unit.price",
          "units": 1,
          "cost": 0.08
        }
      ]
    }
  }
}
```
