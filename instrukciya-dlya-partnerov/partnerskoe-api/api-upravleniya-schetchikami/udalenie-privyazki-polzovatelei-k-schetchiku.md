# Удаление привязки пользователей к счетчику

Позволяет удалить у существующего пользователя права на доступ к счетчику.

**URL:** `DELETE /api/partner/v2.0/projects/<project_id>/users/<user_id>`

## Параметры запроса <a href="#19" id="19"></a>

| **Поле**    | **Тип** | **Описание**                |
| ----------- | ------- | --------------------------- |
| project\_id | Int     | Идентификатор счетчика.     |
| user\_id    | Int     | Идентификатор пользователя. |

**Пример запроса**

```
DELETE /api/partner/v2.0/projects/4600033/users/1194244 HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: key KtdCzvnscS1U6ovSkvkoY6lAv8nu0mntoyapwrAmhFXSHlGAhmxKb0AFrqo4Qd7Y
Connection: keep-alive
Content-Length: 0
Host: statstand11.top100.rambler.tech:8080
User-Agent: HTTPie/0.9.9
```

## Параметры тела ответа <a href="#20" id="20"></a>

| **Поле** | **Тип** | **Описание**                                      |
| -------- | ------- | ------------------------------------------------- |
| result   | String  | Отметка об успешность/неуспешности удаления прав. |

**Пример ответа**

```
HTTP/1.1 200 OK
Content-Length: 21
Content-Type: application/json
{
    "result": "OK"
}
```
