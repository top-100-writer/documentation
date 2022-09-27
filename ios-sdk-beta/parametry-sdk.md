# Параметры sdk

| Параметр                                                                      | Описание                                                                     |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| <pre><code>.setPublisherId(publisherId: "PUBLISHER_ID")</code></pre>          | Передача идентификатора пользователя от площадки                             |
| <pre><code>.setPublisherScope(publisherScope: "PUBLISHER_SCOPE")</code></pre> | Передача области видимости идентификатора площадки                           |
| <pre><code>.setAuthUserId(authUserId: "AUTH_USER_ID")</code></pre>            | Передача авторизованного идентификатора пользователя                         |
| <pre><code>.setPhone(phone: "8-910-910-10-90")</code></pre>                   | Передача телефона пользователя.  Данные будут захэшированы алгоритмом sha256 |
| <pre><code>.setEmail(email: "email@rambler.ru")</code></pre>                  | Передача email пользователя. Данные будут захэшированы алгоритмом sha256     |

**Пример передачи настроек:**

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    let settings = TrackerTop100Settings(projectId: "PROJECT_ID")
        .setAuthUserId(authUserId: "USER_ID")
        .setPublisherId(publisherId: "PUBLISHER_ID")
        .setPublisherScope(publisherScope: "PUBLISHER_SCOPE")
        .setEmail(email: "user@domain.ru") // хеши посчитаются автоматом
        .setPhone(phone: "8-910-910-90-10") // хеши посчитаются автоматом
        .build()

    TrackerTop100.activate(settings: settings)
}
```
