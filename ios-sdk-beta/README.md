# iOS sdk \[Beta]

### Подключение sdk

{% tabs %}
{% tab title="Swift Package Manager" %}
Добавьте модуль через **Swift Package Manager:**

Для этого в Xcode выберите свой проект и перейдите на вкладку Package Dependencies.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Нажмите на "+" для добавления нового пакета и укажите URL репозитория: [`https://github.com/top-100-writer/top100-tracker-ios`](https://github.com/top-100-writer/top100-tracker-ios) в нем находится Package.swift.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-02 at 18.06.56.png" alt=""><figcaption></figcaption></figure>

Выберете версию пакета и настройте правило обновления. Добавьте пакет в свой проект.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-02 at 18.09.39.png" alt=""><figcaption></figcaption></figure>

После добавления, пакет должен появиться в Package Dependencies, а также в левой панели.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-02 at 18.11.09.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="CocoaPods" %}
Добавьте модуль через **CocoaPods:**

Добавьте пакет TrackerTop100SDK в `Podfile` в своем проекте

```
platform :ios, '11.0'

target 'MyApp' do
  use_frameworks!
  pod 'TrackerTop100SDK', '1.0.0'
  ...
end
```

Обновите зависимости c помощью команды `pod install`

После этого, откройте созданный файл проекта `.xcworkspace`, там должен отобразиться подключенный пакет с фреймворком

<figure><img src="../.gitbook/assets/Screenshot 2022-11-03 at 16.14.25.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Carthage" %}
Добавьте модуль через **Carthage:**

Для подключения добавьте зависимость в `Cartfile`

`binary "https://github.com/top-100-writer/top100-tracker-ios/blob/main/TrackerTop100SDK.json" ~> 1.0.0`

Обновите зависимости с помощью команды `carthage update --use-xcframeworks`

Откройте вкладку `General settings` вашего приложения и найдите раздел `Frameworks, Libraries, and Embedded Content`&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2022-11-03 at 16.02.35.png" alt=""><figcaption></figcaption></figure>

Выберете пакет `TrackerTop100SDK.xcframework` из папки `Carthage/Build` на диске или просто перетяните его.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-03 at 16.05.32.png" alt=""><figcaption></figcaption></figure>

После сборки проекта пакет в виде фреймворка должен отобразиться левой панели.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-03 at 16.07.42.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Базовая инициализация в методе Application(Swift)

Инициализируйте библиотеку в методе `application(_:didFinishLaunchingWithOptions:)` вашего `UIApplicationDelegate`:

```
//  AppDelegate.swift
import TrackerTop100SDK

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        let settings = TrackerTop100Settings(projectId: "PROJECT_ID")
        // ... установка параметров sdk
        TrackerTop100.activate(settings: settings)
    }
}
```

**PROJECT\_ID** (обязательный) — id проекта, аналогичный js счетчику
