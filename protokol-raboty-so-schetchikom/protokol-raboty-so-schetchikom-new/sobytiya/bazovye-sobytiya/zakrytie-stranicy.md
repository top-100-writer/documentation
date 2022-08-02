# Закрытие страницы

Событие закрытие страницы передается со значением **event\_name=page\_close**. Дополнительную информацию можно пережать в формате JSON в параметре meta. Возможное поля:

| Параметр | Формат          | Описание                         |
| -------- | --------------- | -------------------------------- |
| time     | Number          | Время на странице в секундах     |
| screens  | Array\<Numbers> | Экраны, которые были просмотрены |

**Пример:**

`https://kraken.rambler.ru/cnt/v2/?event_name=page_close&event_class=base&project_id=80674&request_id=1653485500.501-410526461&event_id=9104862342599116&meta=%7B%22time%22%3A62%2C%22screens%22%3A%5B62%2C62%2C62%2C62%2C62%2C62%2C62%2C62%2C62%2C62%5D%7D&url=http%3A%2F%2Frambler.ru%3A4000%2F&session_id=237994821_1653484835442&session_number=40&session_event_number=29&top100_id=t1.7436868.1783481600.1643968662923&adtech_uid=17b92f10-73d4-420c-8d60-a2cb52aa0843&adtech_uid_scope=rambler.ru&fingerprint=pA8AAENKs1dQLsnJAbxfJwA%3D&fingerprint_ip=pA8AAENKs1eK%2FEUzAaosKwA%3D&version=2.2.3&counter_type=web`
