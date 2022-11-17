# Параметры sdk

| Параметр                                                         | Описание                                                                        |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| <pre><code>.publisherId("PUBLISHER_ID")</code></pre>             | Передача идентификатора пользователя от площадки                                |
| <pre><code>.publisherScope("PUBLISHER_SCOPE")</code></pre>       | Передача области видимости идентификатора площадки                              |
| <pre><code>.userId("AUTH_USER_ID")</code></pre>                  | Передача авторизованного идентификатора пользователя                            |
| <pre><code>.phone("8-910-910-10-90")</code></pre>                | Передача телефона пользователя.  Данные будут захэшируются алгоритмом sha256    |
| <pre><code>.email("email@rambler.ru")</code></pre>               | Передача email пользователя. Данные будут захэшируются алгоритмом sha256        |
| <pre><code>.setActivityAutoTracking(enabled = true)</code></pre> | Включение автоматической отправки события page\_view при переходе на активность |

**Пример передачи настроек:**

{% tabs %}
{% tab title="Java" %}
```
public final void onCreate() {
    KrakenSettings config = new KrakenSettings.Builder("PROJECT_ID")
        .userId("USER_ID")
        .publisherId("PUBLISHER_ID")
        .publisherScope("PUBLISHER_SCOPE")
        .phone("8-910-910-90-10") // хеши посчитаются автоматом
        .email("user@domain.ru") // хеши посчитаются автоматом
        .setActivityAutoTracking(true)
        .build();
    Kraken.activate((Application) getApplicationContext(), config);
}
```
{% endtab %}

{% tab title="Kotlin" %}
```
override fun onCreate() {
    super.onCreate()
    Kraken.activate(
        application = this,
        krakenSettings = KrakenSettings
            .Builder(projectId = "PROJECT_ID")
            .userId(userIdValue = "USER_ID")
            .publisherId(publisherIdValue = "PUBLISHER_ID")
            .publisherScope(publisherScopeValue = "PUBLISHER_SCOPE")
            .phone(phone = "8-910-910-90-10") // хеши посчитаются автоматом
            .email(email = "user@domain.ru") // хеши посчитаются автоматом
            .setActivityAutoTracking(enabled = true) // по-умолчанию false
            .build()
        )
        .disableActivityAutoTracking() // можно задать/переопределить

    // Можно переопределить в любом месте приложения
    Kraken.disableActivityAutoTracking()
}
```
{% endtab %}
{% endtabs %}
