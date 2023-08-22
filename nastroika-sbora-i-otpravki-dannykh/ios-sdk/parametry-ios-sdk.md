# Параметры iOS SDK

<table><thead><tr><th width="398">Параметр</th><th>Описание</th></tr></thead><tbody><tr><td><pre data-overflow="wrap"><code>.setPublisherId(publisherId: "PUBLISHER_ID")
</code></pre></td><td>Передача идентификатора пользователя от площадки</td></tr><tr><td><pre data-overflow="wrap"><code>.setPublisherScope(publisherScope: "PUBLISHER_SCOPE")
</code></pre></td><td>Передача области видимости идентификатора площадки</td></tr><tr><td><pre data-overflow="wrap"><code>.setAuthUserId(authUserId: "AUTH_USER_ID")
</code></pre></td><td>Передача авторизованного идентификатора пользователя</td></tr><tr><td><pre data-overflow="wrap"><code>.setPhone(phone: "79109101090")
</code></pre></td><td>Передача телефона пользователя.  Данные будут захэшированы алгоритмом sha256</td></tr><tr><td><pre data-overflow="wrap"><code>.setEmail(email: "email@rambler.ru")
</code></pre></td><td>Передача email пользователя. Данные будут захэшированы алгоритмом sha256</td></tr><tr><td><pre data-overflow="wrap"><code>.setAutoTrackView(value: true)
</code></pre></td><td>Установка флага, отвечающего за включение автоматического трекинга просмотра экранов</td></tr></tbody></table>

**Пример передачи настроек:**

{% tabs %}
{% tab title="Swift" %}
```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    let settings = TrackerTop100Settings(projectId: "PROJECT_ID")!
        .setAuthUserId(authUserId: "USER_ID")
        .setPublisherId(publisherId: "PUBLISHER_ID")
        .setPublisherScope(publisherScope: "PUBLISHER_SCOPE")
        .setEmail(email: "user@domain.ru") // хеши посчитаются автоматически
        .setPhone(phone: "79109109010") // хеши посчитаются автоматически
        .setAutoTrackView(value: true)
        .build()

    TrackerTop100.activate(settings: settings)
}
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@implementation AppDelegate
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    TrackerTop100Settings *settings = [[TrackerTop100Settings alloc] initWithProjectId: @"PROJECT_ID"];
    settings = [settings setAuthUserIdWithAuthUserId: @"USER_ID"];
    settings = [settings setPublisherIdWithPublisherId: @"PUBLISHER_ID"];
    settings = [settings setPublisherScopeWithPublisherScope: @"PUBLISHER_SCOPE"];
    settings = [settings setEmailWithEmail: @"user@domain.ru"]; // хеши посчитаются автоматически
    settings = [settings setPhoneWithPhone: @"79109109010"]; // хеши посчитаются автоматически
    settings = [settings setAutoTrackViewWithValue: true];
    
    [TrackerTop100 activateWithSettings: [settings build]];
}
```
{% endtab %}
{% endtabs %}

