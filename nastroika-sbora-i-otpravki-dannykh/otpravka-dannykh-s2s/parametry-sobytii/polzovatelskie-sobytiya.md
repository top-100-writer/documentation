# Пользовательские события

При передаче данных событий должен быть передан параметр **event\_type=cv.**

Уникальное название события необходимо передать в параметре **event\_name=EVENT\_NAME.** Например, `event_name=button_click`.

Дополнительные параметры события можно передать в параметре **meta**, не более 30 пар ключ=значение, в формате JSON.&#x20;

Например, `meta={color: black, image: true}`

**Пример:**

{% code overflow="wrap" %}
```
https://kraken.rambler.ru/cnt/v2/?event_type=cv&event_name=rec&project_id=127846&session_id=1808149018_1670228367626&session_number=8&session_event_number=60&version=3.12.12&counter_type=web&experiment=%5B%5B%22exp_bot%22%2C%22split_b%22%5D%2C%5B%22exp_ping%22%2C%22no%22%5D%2C%5B%22exp_ping_heartbeat%22%2C%22ping_heartbeat_on%22%5D%5D&top100_id=t1.-1.1938537918.1643966398357&adtech_uid=6a0ff610-8f49-4896-9c25-ed9643715b94&adtech_uid_scope=rambler.ru&fingerprint=pA8AAENKs1fTzF29Ab8DNQA%3D&fingerprint_ip=pA8AAENKs1fnZVqRATvpYAA%3D&url=https%3A%2F%2Fnews.rambler.ru%2Fincidents%2F49813016-smi-chechenskiy-bloger-tumso-abdurahmanov-ubit-v-shvetsii%2F&request_id=1670228980.882-1439163155&event_id=148989814595420&split=%5B%22desktop%22%2C%22%22%2C%22%22%5D&meta=%7B%22rec%3A%3Anull%3A%3Anull%3A%3Anull%3A%3Apageview%3A%3Anull%3A%3Anull%3A%3AAAAAADYkfWJTHUO8AeKFAQB%3D%3A%3Anull%3A%3ARCM-122C%3A%3ARCM-122C%3A%3A25237d955df271d543070d28d4dd1c01e36dc3599d16f92c883b1f8ddca7%3A%3Ahttps%3A%2F%2Fnews.rambler.ru%2Fincidents%2F49813016-smi-chechenskiy-bloger-tumso-abdurahmanov-ubit-v-shvetsii%2F%3A%3Anull%3A%3Ahttps%3A%2F%2Fnews.rambler.ru%2Fincidents%2F49813016-smi-chechenskiy-bloger-tumso-abdurahmanov-ubit-v-shvetsii%2F%3A%3Anull%3A%3Anull%3A%3A18bKJu__2sSDg9SbfWVwU%3A%3A1670228981.075-1094185879%3A%3Anull%3A%3Anull%3A%3Anull%3A%3Afalse%3A%3A1.9.4842%2Bg315a3f6ef%3A%3Anull%22%3A%2249813016%22%7D&rn=452652996
```
{% endcode %}
