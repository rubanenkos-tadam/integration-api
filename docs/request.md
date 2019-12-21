## POST Request

```
https://dev.opentadam.com/api/integration/rpc
```

### Headers

Param | Sample | Man/Opt | Type | Description
----- | ------ | ------- | ---- | -----------
Authorization | HJAsdhjashj328238asd | man | string | API-key
Accept-Language | en-US | opt | string | Локаль, согласно стандарта [RFC 2616](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.4)<br> Используется для локализации сообщений.


### Body json object

Param | Sample | Man/Opt | Type | Description
----- | ------ | ------- | ---- | -----------
method | "Orders.getList" | man | string | Название команды
version | "1.0" | man | string | Версия
params | { "dispatchingServiceId": 101001010233 } | opt | json | Параметры команды
id | 123 | opt | integer | ИД запроса. Сервер вернет этот же ИД в ответе


## HTTP-Response

http-code | Description
--------- | -----------
200 | Ok
401 | Auth error

### Output json object

Param | Sample | Man/Opt | Type | Description
----- | ------ | ------- | ---- | -----------
result |  | opt | json | Результат команды
error | {} | opt | json, JsonRpcError | Ошибка
id | 123 | opt | integer | ИД запроса


#### Object JsonRpcError

Param | Sample | Man/Opt | Type | Description
----- | ------ | ------- | ---- | -----------
code | 65001 | man | Код ошибки
message | "Неверный параметр" | man | Текст ошибки 

