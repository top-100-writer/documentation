# Параметры sdk

| Параметр                                                                      | Описание                                                                     |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| <pre><code>.setPublisherId(publisherId: "PUBLISHER_ID")</code></pre>          | Передача идентификатора пользователя от площадки                             |
| <pre><code>.setPublisherScope(publisherScope: "PUBLISHER_SCOPE")</code></pre> | Передача области видимости идентификатора площадки                           |
| <pre><code>.setAuthUserId(authUserId: "AUTH_USER_ID")</code></pre>            | Передача авторизованного идентификатора пользователя                         |
| <pre><code>.setPhone("8-910-910-10-90")</code></pre>                          | Передача телефона пользователя.  Данные будут захэшируются алгоритмом sha256 |
| <pre><code>.setEmail("email@rambler.ru")</code></pre>                         | Передача email пользователя. Данные будут захэшируются алгоритмом sha256     |

**Пример передачи настроек:**

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    let settings = TrackerTop100Settings(projectId: "PROJECT_ID")
    settings.setAuthUserId("USER_ID")
    settings.setPublisherId("PUBLISHER_ID")
    settings.setPublisherScope("PUBLISHER_SCOPE")
    settings.setEmail(email: "user@domain.ru") // хеши посчитаются автоматом
    settings.setPhone(phone: "8-910-910-90-10") // хеши посчитаются автоматом

    kraken = TrackerTop100(settings: settings)
    return true
}
```
