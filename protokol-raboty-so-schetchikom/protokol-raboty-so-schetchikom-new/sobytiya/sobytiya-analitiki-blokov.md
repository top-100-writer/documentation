# События аналитики блоков

События показа блока передается со значением **event\_name=show** и событие клика по блоку **event\_name=click**, при этом **event\_type=ub**. Список блоков можно передать в параметре meta в формате массива строк.

| Параметр | Формат    | Описание                                                                                                 |
| -------- | --------- | -------------------------------------------------------------------------------------------------------- |
| meta     | \[String] | Список блоков, который были показаны или по которым был совершен клик. Например, \["attribute::link\_1"] |

**Пример:**

`https://kraken.rambler.ru/cnt/v2/?event_name=click&event_class=ub&project_id=80674&request_id=1653485500.501-410526461&event_id=2955855019949337&meta=%5B%22blocks%3A%3Aplay%22%5D&url=http%3A%2F%rambler.ru%3A4000%2F&session_id=237994821_1653484835442&session_number=40&session_event_number=20&top100_id=t1.7436868.1783481600.1643968662923&adtech_uid=17b92f10-73d4-420c-8d60-a2cb52aa0843&adtech_uid_scope=rambler.ru&fingerprint=pA8AAENKs1dQLsnJAbxfJwA%3D&fingerprint_ip=pA8AAENKs1eK%2FEUzAaosKwA%3D&version=2.2.3&counter_type`
