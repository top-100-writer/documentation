# Показ страницы / экрана

Событие показа страницы передается со значением **event\_name=page\_view**. Дополнительную информацию можно пережать в формате JSON в параметре meta. Возможные поля:

<table><thead><tr><th width="150">Параметр</th><th width="150">Формат</th><th width="367.2">Описание</th></tr></thead><tbody><tr><td>title</td><td>String</td><td>Заголовок страницы. Ограничение: не более 250 символов<br><strong>Пример:</strong> <code>Lenta.ru - Новости России и мира сегодня</code></td></tr><tr><td>referer</td><td>URL</td><td>Аналог referer в web. <br><strong>Пример:</strong> <code>https://google.ru</code></td></tr><tr><td>browser_size</td><td>NumberхNumber</td><td>Размеры страницы. <br><strong>Пример:</strong> <code>123x123</code></td></tr><tr><td>screen_size</td><td>NumberхNumber</td><td>Разрешение экрана.<br><strong>Пример:</strong> <code>123х123</code></td></tr><tr><td>color_depth</td><td>Number</td><td>Глубина цвета<br><strong>Пример:</strong> <code>24</code></td></tr><tr><td>pixel_ration</td><td>Float</td><td>Отношение разрешения дисплея в физических пикселях к разрешению в логических пикселях <strong>Пример:</strong> <code>2.5</code></td></tr><tr><td>language</td><td>String</td><td>Язык браузера<br><strong>Пример:</strong> <code>ru-RU</code></td></tr><tr><td>timezone</td><td>Number</td><td>Таймзона (число минут)<br><strong>Пример:</strong> <code>-180</code></td></tr><tr><td>app_name</td><td>String</td><td>Название приложения</td></tr><tr><td>app_verison</td><td>String</td><td>Версия приложения</td></tr><tr><td>manufacturer</td><td>String</td><td>Производитель устройства</td></tr></tbody></table>

**Пример:**

{% code overflow="wrap" %}
```
https://kraken.rambler.ru/cnt/v2/?event_name=page_view&event_class=base&project_id=80674&request_id=1653485500.501-410526461&event_id=2393855005041690&rn=312220732&meta=%7B%22browser_size%22%3A%222027x551%22%2C%22title%22%3A%22Cerber.Counters%22%2C%22screen_size%22%3A%222560x1440%22%2C%22color_depth%22%3A%2224-bit%22%2C%22language%22%3A%22ru-RU%22%2C%22browser%22%3A%22Netscape%22%2C%22platform%22%3A%22MacIntel%22%2C%22timezone%22%3A-180%2C%22referer%22%3A%22%22%7D&url=http%3A%2F%2Frambler.ru%3A4000%2F&session_id=237994821_1653484835442&session_number=40&session_event_number=19&top100_id=t1.7436868.1783481600.1643968662923&adtech_uid=17b92f10-73d4-420c-8d60-a2cb52aa0843&adtech_uid_scope=rambler.ru&fingerprint=pA8AAENKs1dQLsnJAbxfJwA%3D&fingerprint_ip=pA8AAENKs1eK%2FEUzAaosKwA%3D&version=2.2.3&counter_type=web
```
{% endcode %}

