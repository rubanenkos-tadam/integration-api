# Список идентификаторов заказов (не завершенные)

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Orders.getIdentifiers
version | 1.0
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
dispatchingServiceId | man | integer64 | Идентификатор диспетчерской

### Пример

```
{
  "method": "Orders.getIdentifiers",
  "version": "1.0",
  "params": {
    "dispatchingServiceId": 135464637
  }
}
```

---

## Ответ json object

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
result | man | array | Массив идентификаторов заказов

```
{
  "result": [2342433,32445456,43535353]
}
```
