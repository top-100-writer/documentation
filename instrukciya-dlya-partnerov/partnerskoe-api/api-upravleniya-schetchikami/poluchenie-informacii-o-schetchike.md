# Получение информации о счетчике

Позволяет получить состояние счетчика по его идентификатору.

**URL: ** `GET /api/partner/v2.0/projects/<project_id>`

## Параметры запроса <a href="9" id="9"></a>

| **Поле**   | **Тип** | **Описание**            |
| ---------- | ------- | ----------------------- |
| project_id | Int     | Идентификатор счетчика. |

**Пример запроса**

```
GET /api/partner/v2.0/projects/4600827 HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: key KtdCzvnscS1U6ovSkvkoY6lAv8nu0mntoyapwrAmhFXSHlGAhmxKb0AFrqo4Qd7Y
Connection: keep-alive
Host: statstand11.top100.rambler.tech:8080
User-Agent: HTTPie/0.9.9
```

## Параметры тела ответа <a href="10" id="10"></a>

| **Поле**   | **Тип**    | **Описание**                                                                                   |
| ---------- | ---------- | ---------------------------------------------------------------------------------------------- |
| categories | List\[Int] | Список категорий, к которым привязан счетчик.                                                  |
| id         | Int        | Идентификатор счетчика.                                                                        |
| keywords   | String     | Список ключевых слов, ассоциированных со счетчиком.                                            |
| regions    | List\[Int] | Список регионов, связанных со счетчиком.                                                       |
| status     | String     | Статус счетчика.                                                                               |
| title      | String     | Название счетчика (сайта).                                                                     |
| types      | List\[Int] | Тип сайта (см. [рекомендации по выбору типа](http://help.rambler.ru/top100/top100-faq/1526/)). |
| url        | String     | URL сайта.                                                                                     |

**Пример ответа**

```
HTTP/1.1 200 OK
Content-Length: 308
Content-Type: application/json
{
    "result": {
        "categories": [
            1384,
            1401
        ],
        "id": 4600827,
        "keywords": "test keywords",
        "regions": [
            6,
            8
        ],
        "status": "unincluded",
        "title": "Give me Some Magic",
        "types": [
            8
        ],
        "url": "http://some-magic-url1.test"
    }
}
```
