# Статус заказа

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Orders.getStatus
version | 1.0
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
orderId | man | int64 | Идентификатор заказа

### Пример

```
{
  "method": "Orders.getStatus",
  "version": "1.0",
  "params": {
    "orderId": 12233401
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
status | man | OrderStatus / integer | Статус заказа
cancellationCause | opt | CancellationCause / json | Причина отмены (если status=6)

### OrderStatus / integer

Value | Description
----- | -----------
1 | Не распределен
2 | Назначен водитель
3 | Водитель по адресу (ожидает клиента)
4 | Заказ выполняется
5 | Успешно завершен
6 | Отменен
7 | Зарезервирован водителем (только если заказ предварительный)

### CancellationCause / json

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
kind | man |CancellationCauseKind / integer | Тип причины
comment | opt | string | Комментарий

#### CancellationCauseKind / integer

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

---

### Пример

```
{
  "result": {
    "status": 6,
    "cancellationCause": {
      "kind": 5,
      "comment": "клиент отменил заказ"
    }
  }
}
```
