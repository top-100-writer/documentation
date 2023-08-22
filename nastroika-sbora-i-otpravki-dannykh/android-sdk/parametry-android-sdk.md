# Параметры Android SDK

| Параметр                                                                               | Описание                                                                        |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| <pre data-overflow="wrap"><code>.publisherId("PUBLISHER_ID")
</code></pre>             | Передача идентификатора пользователя от площадки                                |
| <pre data-overflow="wrap"><code>.publisherScope("PUBLISHER_SCOPE")
</code></pre>       | Передача области видимости идентификатора площадки                              |
| <pre data-overflow="wrap"><code>.userId("AUTH_USER_ID")
</code></pre>                  | Передача авторизованного идентификатора пользователя                            |
| <pre data-overflow="wrap"><code>.phone("79109101090")
</code></pre>                    | Передача телефона пользователя.  Данные будут захэшируются алгоритмом sha256    |
| <pre data-overflow="wrap"><code>.email("email@rambler.ru")
</code></pre>               | Передача email пользователя. Данные будут захэшируются алгоритмом sha256        |
| <pre data-overflow="wrap"><code>.setActivityAutoTracking(enabled = true)
</code></pre> | Включение автоматической отправки события page\_view при переходе на активность |

**Пример передачи настроек:**

{% tabs %}
{% tab title="Kotlin" %}
```
override fun onCreate() {
    super.onCreate()
    Kraken.activate(
        application = this,
        krakenSettings = listOf(KrakenSettings
            .Builder(projectId = "PROJECT_ID")
            .userId(userIdValue = "USER_ID")
            .publisherId(publisherIdValue = "PUBLISHER_ID")
            .publisherScope(publisherScopeValue = "PUBLISHER_SCOPE")
            .phone(phone = "79109109010") // хеши посчитаются автоматом
            .email(email = "user@domain.ru") // хеши посчитаются автоматом
            .setActivityAutoTracking(enabled = true) // по-умолчанию false
            .build()
        ))
        .disableActivityAutoTracking() // можно задать/переопределить

    // Можно переопределить в любом месте приложения
    Kraken.disableActivityAutoTracking()
}
```
{% endtab %}

{% tab title="Java" %}
```
public final void onCreate() {
    KrakenSettings config = new KrakenSettings.Builder("PROJECT_ID")
        .userId("USER_ID")
        .publisherId("PUBLISHER_ID")
        .publisherScope("PUBLISHER_SCOPE")
        .phone("79109109010") // хеши посчитаются автоматом
        .email("user@domain.ru") // хеши посчитаются автоматом
        .setActivityAutoTracking(true)
        .build();
    List<KrakenSettings> krakenSettingsList = new ArrayList();
    krakenSettingsList.add(config);
    Kraken.activate((Application) getApplicationContext(), krakenSettingsList);
}
```
{% endtab %}
{% endtabs %}

