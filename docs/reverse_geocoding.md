# Поиск ближайшего адреса по координате

Структура запроса соответствует [Протоколу](docs/request.md)

---

### Body json object

Param | Value
----- | ------
method | Address.ReverseGeocoding
version | 1
params | json

## Params

Param | Man/Opt | Type | Description
----- | ------- | ---- | -----------
pos | opt | GpsPosition / json | Координаты для сортировки результатов


### Пример

```
{
  "method": "Address.ReverseGeocoding",
  "version": "1",
  "params": {
    "pos": {
      "lat": 52.093580,
      "lon": 23.697391
    }
  }
}
```

----

## Ответ json object

Param  | Man/Opt | Type | Description
-----  | ------- | ---- | -----------
result | man | json | Объект

Объект [addresses](docs/objects/ClientAddress.md#json-object-address)

---

### Пример

```
{
  "result": {
    "addresses": [
      {
        "name": "Республика Беларусь, обл Брестская, г Брест, ул Гоголя, 82",
        "components": [
          {
            "level": 0,
            "name": "Республика Беларусь"
          },
          {
            "level": 1,
            "name": "обл Брестская"
          },
          {
            "level": 4,
            "name": "г Брест"
          },
          {
            "level": 7,
            "name": "ул Гоголя"
          },
          {
            "level": 8,
            "name": "82"
          }
        ],
        "types": {
          "pointType": 22
        },
        "position": {
          "lat": 52.094579,
          "lon": 23.699920
        }
      },
      {
        "name": "Республика Беларусь, обл Брестская, г Брест, ул Гоголя, 821"
        "components": [
          {
            "level": 0,
            "name": "Республика Беларусь"
          },
          {
            "level": 1,
            "name": "обл Брестская"
          },
          {
            "level": 4,
            "name": "г Брест"
          },
          {
            "level": 7,
            "name": "ул Гоголя"
          },
          {
            "level": 8,
            "name": "821"
          }
        ],
        "position": {
          "lat": 52.095781, 
          "lon": 23.705027
        }
      }
    ]
  }
}
```
