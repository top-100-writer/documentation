# Получение списка пользователей, привязанных к счетчику

Позволяет получить список пользователей, связанных со счетчиком.

**URL: ** `GET /api/partner/v2.0/projects/<project_id>/users`

## Параметры запроса <a href="14" id="14"></a>

| **Поле**   | **Тип** | **Описание**            |
| ---------- | ------- | ----------------------- |
| project_id | Int     | Идентификатор счетчика. |

**Пример запроса**

```
GET /api/partner/v2.0/projects/4600033/users HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: key KtdCzvnscS1U6ovSkvkoY6lAv8nu0mntoyapwrAmhFXSHlGAhmxKb0AFrqo4Qd7Y
Connection: keep-alive
Host: statstand11.top100.rambler.tech:8080
User-Agent: HTTPie/0.9.9
```

## Параметры тела ответа <a href="15" id="15"></a>

| **Поле** | **Тип** | **Описание**                                                                                                                       |
| -------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| result   | List    | Содержит набор данных, характеризующих пользователей с доступом к счетчику. Для каждого пользователя выводятся нижеописанные поля. |
| email    | String  | Емейл пользователя.                                                                                                                |
| id       | Int     | Идентификатор пользователя.                                                                                                        |
| readonly | Boolean | Отметка о наличии у пользователя прав к счетчику.                                                                                  |

**Пример ответа**

```
HTTP/1.1 200 OK
Content-Length: 417
Content-Type: application/json
{
    "result": [
        {
            "email": "v.testtest@rambler.ru",
            "id": 1194243,
            "readonly": true
        },
        {
            "email": "r.krav@rambler.ru",
            "id": 1194244,
            "readonly": true
        },
        {
            "email": "new-guy@rambler.test",
            "id": 1194245,
            "readonly": true
        },
        {
            "email": "d.gening@rambler.ru",
            "id": 1194246,
            "readonly": true
        }
    ]
}
```
