# Переход по внешней ссылке

Событие переход по внешней ссылке передается со значением **event\_name=click**. Дополнительную информацию можно пережать в формате JSON в параметре meta. Возможные поля:

| Параметр | Формат | Описание                                      |
| -------- | ------ | --------------------------------------------- |
| URL      | String | URL страницы, на который совершается переход. |



**Пример:**

{% code overflow="wrap" %}
```
https://kraken.rambler.ru/cnt/v2/?event_name=click&event_class=base&project_id=80674&request_id=1653486325.197-1923296212&event_id=4848863278197387&meta=https%3A%2F%2Fgoogle.ru%2F&url=http%3A%2F%2Frambler.ru%3A4000%2F&session_id=237994821_1653484835442&session_number=40&session_event_number=39&top100_id=t1.7436868.1783481600.1643968662923&adtech_uid=17b92f10-73d4-420c-8d60-a2cb52aa0843&adtech_uid_scope=rambler.ru&fingerprint=pA8AAENKs1dQLsnJAbxfJwA%3D&fingerprint_ip=pA8AAENKs1eK%2FEUzAaosKwA%3D&version=2.2.3&counter_type=web
```
{% endcode %}

