# Регистрация счетчика

Метод позволяет массово завести счетчики и соотнести их с соответствующими категориями каталога сайтов.

В результате выполнения данного метода Топ-100 сохранит счетчик и присвоит ему уникальный идентификатор, который и вернет в ответе.

**URL:** `POST /api/partner/v2.0/projects`

**ВНИМАНИЕ!** Новый сайт будет добавлен в рейтинг Топ-100 только после прохождения модерации.

## Параметры тела запроса <a href="6" id="6"></a>

| **Поле**   | **Тип**    | **Описание**                                                                                                                                                                                                                                                                                                                                             |
| ---------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url        | String     | URL вашего сайта.                                                                                                                                                                                                                                                                                                                                        |
| title      | String     | Название счетчика (сайта).                                                                                                                                                                                                                                                                                                                               |
| keywords   | String     | Список ключевых слов. Можно указать одно слово или несколько.                                                                                                                                                                                                                                                                                            |
| categories | List\[Int] | Список категорий, к которым необходимо привязать счетчик. Можно указать одну категорию или несколько (см. [рекомендации по выбору темы](http://help.rambler.ru/top100/top100-faq/1525/)). ВНИМАНИЕ! Счетчик можно отнести только к категории из числа доступных вам (настраивается менеджером в Рамблер при генерации токена и выдаче вам прав доступа). |
| regions    | List\[Int] | Список регионов, к которым привязывается счетчик. Опциональный параметр (см. [рекомендации по привязке к региону](http://help.rambler.ru/top100/top100-faq/1346/)).                                                                                                                                                                                      |
| types      | List\[Int] | Список типов, к которым привязывается счетчик. Опциональный параметр (см. [рекомендации по выбору типа](http://help.rambler.ru/top100/top100-faq/1526/)).                                                                                                                                                                                                |
| rated      | Boolean    | Признак участия счетчика (сайта) в рейтинге Топ-100.                                                                                                                                                                                                                                                                                                     |

**Пример запроса**

```
POST /api/partner/v2.0/projects HTTP/1.1
Accept: application/json, */*
Accept-Encoding: gzip, deflate
Authorization: key somekey
Connection: keep-alive
Content-Length: 209
Content-Type: application/json
Host: statstand11.top100.rambler.tech:8080
User-Agent: HTTPie/0.9.9
[
    {
        "categories": [
            1384,
            1401
        ],
        "rated": false,
        "regions": [
            8,
            6
        ],
        "title": "Give me Some Magic",
        "types": [
            8
        ],
        "url": "http://some-magic-url1.test"
    }
]
```

## Параметры тела ответа <a href="7" id="7"></a>

| **Поле** | **Тип** | **Описание**                               |
| -------- | ------- | ------------------------------------------ |
| result   | Int     | Идентификатор зарегистрированного счетчика |

**Пример ответа**

```
HTTP/1.1 200 OK
Content-Length: 34
Content-Type: application/json
{
    "result": [
        4600827
    ]
}
```

## Возможные ошибки <a href="8" id="8"></a>

**Указана категория к которой нету прав доступа**

```
HTTP/1.0 400 BAD REQUEST
Content-Length: 108
Content-Type: application/json
Date: Thu, 07 Sep 2017 11:55:44 GMT
Server: Werkzeug/0.12.2 Python/3.6.1
{
    "errors": {
        "1": {
            "categories": {
                "0": [
                    "Missing permission for theme"
                ]
            }
        },
        "message": "Request validation errors"
    }
}
```

**URL уже зарегистрирован в каталоге**

```
HTTP/1.0 400 BAD REQUEST
Content-Length: 89
Content-Type: application/json
Date: Thu, 07 Sep 2017 12:07:05 GMT
Server: Werkzeug/0.12.2 Python/3.6.1
{
    "errors": {
        "0": {
            "url": [
                "URL already registered"
            ]
        },
        "message": "Request validation errors"
    }
}
```

**Слишком короткий Title**

```
HTTP/1.0 400 BAD REQUEST
Content-Length: 99
Content-Type: application/json
Date: Thu, 07 Sep 2017 12:48:06 GMT
Server: Werkzeug/0.12.2 Python/3.6.1
{
    "errors": {
        "0": {
            "title": [
                "Shorter than minimum length 5."
            ]
        },
        "message": "Request validation errors"
    }
}
```
