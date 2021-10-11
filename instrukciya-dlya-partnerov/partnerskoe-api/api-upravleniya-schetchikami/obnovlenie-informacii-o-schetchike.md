# Обновление информации о счетчике

Метод позволяет обновить темы/типы/регионы/состояние в рейтинге для конкретного счетчика.

**URL:** `PUT /api/partner/v2.0/projects/<project_id>`

## Параметры запроса <a href="11" id="11"></a>

| **Поле**   | **Тип** | **Описание**            |
| ---------- | ------- | ----------------------- |
| project_id | Int     | Идентификатор счетчика. |

## Параметры тела запроса <a href="12" id="12"></a>

| **Поле** | **Тип** | **Описание**                                         |
| -------- | ------- | ---------------------------------------------------- |
| rated    | Boolean | Признак участия счетчика (сайта) в рейтинге Топ-100. |
| title    | String  | Название счетчика (сайта).                           |

**Пример запроса**

```
PUT /api/partner/v2.0/projects/4600827 HTTP/1.1
Accept: application/json, */*
Accept-Encoding: gzip, deflate
Authorization: key KtdCzvnscS1U6ovSkvkoY6lAv8nu0mntoyapwrAmhFXSHlGAhmxKb0AFrqo4Qd7Y
Connection: keep-alive
Content-Length: 62
Content-Type: application/json
Host: statstand11.top100.rambler.tech:8080
User-Agent: HTTPie/0.9.9
{
    "rated": false,
    "title": "Give me Some New Magic"
}
```

## Параметры тела ответа <a href="13" id="13"></a>

| **Поле** | **Тип** | **Описание**                                            |
| -------- | ------- | ------------------------------------------------------- |
| result   | String  | Отметка об успешности/неуспешности обновления счетчика. |

**Пример ответа**

```
HTTP/1.1 200 OK
Content-Length: 21
Content-Type: application/json
{
    "result": "OK"
}
```
