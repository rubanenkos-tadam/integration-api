# JSON object ClientAddress

Param |  Man/Opt | Type | Description
----- |  ------- | ---- | -----------
address | man | Address / json | Адрес
entrance | opt | string | Подъезд
flat | opt | string	| Квартира
comment | opt | string | Комментарий

### JSON object Address

Param |  Man/Opt | Type | Description
----- |  ------- | ---- | -----------
name | man | string	| Форматированное наименование
components | opt | AddressComponent / array json | Компоненты
types | opt |	AddressTypes / json | Типы точки, быстрого адреса
position | opt | GpsPosition / json | Координаты

### JSON object AddressComponent

Param |  Man/Opt | Type | Description
----- |  ------- | ---- | -----------
level |	man | AddressLevel / integer | обязательный	Уровень
name | man | string	| Наименование

### JSON object AddressTypes

Param |  Man/Opt | Type | Description
----- |  ------- | ---- | -----------
pointType | man | integer |	Тип точки
aliasType | man | integer | Тип быстрого адреса

### JSON object GpsPosition

Param |  Man/Opt | Type | Description
----- |  ------- | ---- | -----------
lat | man | double | Широта
lon | man | double | Долгота

### AddressLevel / integer

Value | Description
----- | -----------
0 | Страна
1 | Административный уровень 1
2 | Административный уровень 2
3 | Административный уровень 3
4 | Административный уровень 4
5 | Административный уровень 5
6 | Административный уровень 6
7 | Улица
8 | Дом
9 | POI

## Пример

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
