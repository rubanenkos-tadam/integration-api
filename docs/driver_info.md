# Информация по назначенному на заказ водителю

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Orders.getAssignee
version | 1.0
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
orderId | man | int64 | Идентификатор заказа

### Пример

```
{
  "method": "Orders.getAssignee",
  "version": "1.0",
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
      "phone": "+375291234567"
    }
  }
}
```
