# Пользовательская активность

Событие пользовательской активности передается со значением **event\_name=ping**. Дополнительную информацию можно передать в формате JSON в параметре meta. Возможные поля:

| Параметр | Формат | Описание                                                                |
| -------- | ------ | ----------------------------------------------------------------------- |
| activity | JSON   | Активность пользователя (клики мышки, клавиатура, ресайз страницы и пр) |
| scroll   | JSON   | Минимальная, максимальная и текущая позиция скролла во время пинга      |
| num      | Number | Порядковый номер пинга                                                  |
| duration | Number | Длительность пинга в секундах                                           |
| url      | String | Url страницы с активностью                                              |
| id       | String | Id страницы                                                             |

**Пример:**

{% code overflow="wrap" %}
```
https://kraken.rambler.ru/cnt/v2/?event_name=ping&event_class=base&project_id=80674&request_id=1653485500.501-410526461&event_id=3244855958766310&rn=585406943&meta=%7B%22activity%22%3A%7B%22mousemove%22%3A9%7D%2C%22scroll%22%3A%7B%22max%22%3A551%2C%22min%22%3A0%2C%22current%22%3A0%7D%2C%22num%22%3A4%2C%22duration%22%3A40%7D&url=http%3A%2F%2Frambler.ru%3A4000%2F&session_id=237994821_1653484835442&session_number=40&session_event_number=25&top100_id=t1.7436868.1783481600.1643968662923&adtech_uid=17b92f10-73d4-420c-8d60-a2cb52aa0843&adtech_uid_scope=rambler.ru&fingerprint=pA8AAENKs1dQLsnJAbxfJwA%3D&fingerprint_ip=pA8AAENKs1eK%2FEUzAaosKwA%3D&version=2.2.3&counter_type=web
```
{% endcode %}
