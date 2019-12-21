<div align="center">*Структура запроса соответствует [[Протоколу|Протокол]].*</div>

----


### Headers



method | Orders.getList
------------ | -------------
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
route | man | array [[object ClientAddress | Структура-адреса#object-clientaddress]] | Маршрут
time | opt | [[string OffsetDateTime| Форматы-даты-и-времени#string-offsetdatetime]] | Время заказа (отсутствует, если текущий)
created | man | [[string OffsetDateTime| Форматы-даты-и-времени#string-offsetdatetime]] | Время создания заказа
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

### Пример

```
{
  "result": [
    {
      "id": 20333,
      "status": 1,
      "phone": "+79123456789",
      "route": {
        "address": {
          "name": "Россия, обл Омская, г Омск, б-р Архитекторов, 35 (Мега Омск, семейный торговый центр)",
          "components": [
            {
              "level": 0,
              "name": " Россия"
            }, {
              "level": 1,
              "name": "обл Омская"
            }, {
              "level": 4,
              "name": "г Омск"
            }, {
              "level": 7,
              "name": "б-р Архитекторов"
            }, {
              "level": 8,
              "name": "35"
            }, {
              "level": 9,
              "name": "Мега Омск, семейный торговый центр"
            }
          ],
          "types": {
            "pointType": 63,
            "aliasType": 3
          },
          "position": {
            "lat": 54.972549,
            "lon": 73.28389
          }
        },
        "comment": "вход IKEA, подземная парковка"
      },
      "time": "2017-10-16T17:00:00+06:00",
      "created": "2017-10-16T15:00:00+06:00",
      "source": 1
    }
  ]
}
```
