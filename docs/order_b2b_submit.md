# Создание заказа

Структура запроса соответствует [Протоколу](docs/request.md)

### Body json object

Param | Value
----- | ------
method | Orders.b2b.submit
version | 10
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
contractorFareId | man | int64 | Идентификатор B2B тарифа
phone | man | string | Телефон сотрудника контрагента
route | man | (ClientAddress)(docs/objects/ClientAddress.md) / array json | Список адресов (маршрут поездки)
time | opt | [OffsetDateTime](docs/objects/OffsetDateTime.md) / string | Время заказа (отсутствует, если текущий)
fixCost | opt | numeric | Стоимость заказа. В течении поездки стоимость пожет измениться только на время простоя, если водитель нажмет кнопку **Простой** или клиент выйдет с опозданием.
options | opt | array of int64 | Массив идентификаторов опций, поддерживаемых тарифом

### Пример

```
{
  "method": "Orders.b2b.submit",
  "version": "10",
  "params": {
    "fixCost": 12.56,
    "options":[
        1123,
        3344
    ],
    "contractorFareId": 1534,
    "phone": "+375290123456",
    "route": [{
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
      }],
    "time": "2019-11-14T13:00:00+03:00"
  }
}
```

## Ответ

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
result | man | int64 | ИД заказа

```
{
  "result": 46400003832333
}
```
