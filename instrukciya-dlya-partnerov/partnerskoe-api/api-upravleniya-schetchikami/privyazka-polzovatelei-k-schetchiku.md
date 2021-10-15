# Привязка пользователей к счетчику

С помощью данного метода можно предоставить доступ к счетчику на чтение заданному множеству пользователей. При этом, если кто-то из пользователей не зарегистрирован в Рамблер/топ-100, ему будет автоматически создан аккаунт на основании переданной почты.

**URL: ** `POST /api/partner/v2.0/projects/<project_id>/users`

## Параметры запроса <a href="16" id="16"></a>

| **Поле**   | **Тип** | **Описание**            |
| ---------- | ------- | ----------------------- |
| project_id | Int     | Идентификатор счетчика. |

## Параметры тела запроса <a href="17" id="17"></a>

| **Поле** | **Тип**       | **Описание**                  |
| -------- | ------------- | ----------------------------- |
| users    | List\[String] | Список емейлов пользователей. |

**Пример запроса**

```
POST /api/partner/v2.0/projects/4600033/users HTTP/1.1
Accept: application/json, */*
Accept-Encoding: gzip, deflate
Authorization: key KtdCzvnscS1U6ovSkvkoY6lAv8nu0mntoyapwrAmhFXSHlGAhmxKb0AFrqo4Qd7Y
Connection: keep-alive
Content-Length: 87
Content-Type: application/json
Host: statstand11.top100.rambler.tech:8080
User-Agent: HTTPie/0.9.9
{
    "users": [
        "d.gening@rambler.ru",
        "new-guy@rambler.test"
    ]
}
```

## Параметры тела ответа <a href="18" id="18"></a>

| **Поле** | **Тип** | **Описание**                                    |
| -------- | ------- | ----------------------------------------------- |
| result   | String  | Отметка об успешность/неуспешности выдачи прав. |

**Пример ответа**

```
HTTP/1.1 200 OK
Content-Length: 21
Content-Type: application/json
{
    "result": "OK"
}
```
