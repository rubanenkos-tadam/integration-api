# Отмена заказа

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Orders.cancel
version | 1.0
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
orderId | man | integer64 | Идентификатор заказа
cancellationCause | man | CancellationCause / json | Причина отмены

### CancellationCause / json

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
kind | man | CancellationCauseKind / integer | Тип причины
comment | opt | string | Комментарий

### CancellationCauseKind / integer

Value | Description
----- | -----------
1 | По желанию клиента
2 | По вине диспетчерской
3 | По вине водителя
4 | Технические проблемы
5 | Неадекватный клиент
6 | Клиент уже уехал
7 | Клиент не берет трубку
8 | Автоматическая отмена
9 | Отправлен в биржу

### Пример

```
{
  "method": "Orders.cancel",
  "version": "1.0",
  "params": {
    "orderId": 34554633,
    "cancellationCause": {
      "kind": 3,
      "comment": "не знает дороги"
    }
  }
}
```

---

## Ответ

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
result | opt | nothing | Пустой

### Пример

```
{}
```
