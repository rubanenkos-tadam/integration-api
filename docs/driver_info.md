# Информация по назначенному на заказ водителю

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Orders.getAssignee
version | 1.1
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
orderId | man | int64 | Идентификатор заказа

### Пример

```
{
  "method": "Orders.getAssignee",
  "version": "1.1",
  "params": {
    "orderId": 3424253235
  }
}
```

----

## Ответ json object

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
result | man | ResultAssignee / json | Объект

### ResultAssignee / json

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
firstName | nam | string | Имя
middleName | opt | string | Отчество
lastName | man | string | Фамилия
callSign | opt | string | Позывной
phone | man | string | Телефон
carBrand | man | string | Бренд автомобиля
carAlias | man | string | Алиас для Brand + Model.
carModel | man | string | Марка автомобиля
carRegnum | man | string | Регистрационный номер автомобиля
carColor | man | string | Цвет автомобиля
position | opt | GpsPosition / json | Координаты, назначенного автомобиля

#### GpsPosition / json
Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
lat | man | number | Широта
lon | man | number | Долгота

---

### Пример

```
{
  "result": {
    "assignee": {
      "firstName": "Иван",
      "middleName": "Петрович",
      "lastName": "Жуков",
      "callSign": "1122",
      "phone": "+375291234567",
      "carBrand": "Audi",
      "carAlias": "Audi",
      "carModel": "A4 Avant (8E)",
      "carRegnum": "7475IH1",
      "carColor": "Blue",
      "position": {
           "lat": 52.33234,
           "lon": 24.56786
      }
    }
  }
}
```
