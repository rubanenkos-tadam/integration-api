# Создание заказа

Структура запроса соответствует [Протоколу](docs/request.md)

### Body json object

Param | Value
----- | ------
method | Orders.submit
version | 1.1
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
fareId | man | integer | Идентификатор клиентского тарифа (выдается администрацией HiveTaxi)
phone | man | string | Телефон клиента
route | man | (ClientAddress)(docs/objects/ClientAddress.md) / array json | Список адресов (маршрут поездки)
time | opt | [OffsetDateTime](docs/objects/OffsetDateTime.md) / string | Время заказа (отсутствует, если текущий)
fixCost | opt | numeric | Стоимость заказа. В течении поездки стоимость пожет измениться только на время простоя, если водитель нажмет кнопку **Простой** или клиент выйдет с опозданием.

### Пример

```
{
  "method": "Orders.submit",
  "version": "1.0",
  "params": {
    "fixCost": 12.56,
    "fareId": 1534,
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
result | man | integer64 | ИД заказа

```
{
  "result": 46400003832333
}
```
