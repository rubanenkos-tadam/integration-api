# Список заказов

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Orders.getList
version | 1.0
params | json

## Params

Param | Sample | Man/Opt | Type | Description
----- | ------ | ------- | ---- | -----------
dispatchingServiceId | 123 | man | integer | Идентификатор диспетчерской

### Пример

```
{
  "method": "Orders.getList",
  "version": "1.0",
  "params": {
    "dispatchingServiceId": 101
  }
}
```

----

## Ответ json object

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
result | man | json | Объект

### json object

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
id | nam | integer | Идентификатор заказа
status | man | OrderStatus / integer | Статус заказа
phone | man | integer | Телефон клиента
route | man | [ClientAddress](docs/objects/ClientAddress.md) / array json | Маршрут
time | opt | [OffsetDateTime](docs/objects/OffsetDateTime.md) / string | Время заказа (отсутствует, если текущий)
created | man | [OffsetDateTime](docs/objects/OffsetDateTime.md) / string | Время создания заказа
source | man | OrderSource / integer | Источник заказа

### OrderStatus / integer

Value | Description
----- | -----------
1 | Не распределен
2 | Назначен водитель
3 | Водитель по адресу (ожидает клиента)
4 | Заказ выполняется
7 | Зарезервирован водителем (только если предварительный)

### OrderSource / integer

Value | Description
----- | -----------
1 | Диспетчерская
2 | Клиентский виджет
3 | Клиентское приложение
6 | Водитель
7 | Integration API

---

### Пример

```
{
  "result": [
    {
      "id": 333001,
      "status": 1,
      "phone": "+375290123456",
      "route": {
        "address": {
          "name": "Республика Беларусь, обл Бресткая, г Брест, б-р Космонавтов, 60 (Школа № 3)",
          "components": [
            {
              "level": 0,
              "name": " Республика Беларусь"
            }, {
              "level": 1,
              "name": "обл Бресткая"
            }, {
              "level": 4,
              "name": "г Брест"
            }, {
              "level": 7,
              "name": "б-р Космонавтов"
            }, {
              "level": 8,
              "name": "60"
            }, {
              "level": 9,
              "name": "Школа № 3"
            }
          ],
          "types": {
            "pointType": 63,
            "aliasType": 3
          },
          "position": {
            "lat": 52.096807,
            "lon": 23.697629
          }
        },
        "comment": "парковка перед школой"
      },
      "time": "2019-11-20T17:00:00+03:00",
      "created": "2019-11-26T15:00:00+03:00",
      "source": 1
    }
  ]
}
```
