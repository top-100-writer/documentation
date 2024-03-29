# Установка трекингового SDK в приложение на iOS

{% tabs %}
{% tab title="Swift Package Manager" %}
Добавьте модуль через **Swift Package Manager:**

Для этого в Xcode выберите свой проект и перейдите на вкладку Package Dependencies.

<figure><img src="../../.gitbook/assets/1.webp" alt=""><figcaption></figcaption></figure>

Нажмите на "+" для добавления нового пакета и укажите URL репозитория: `https://github.com/top-100-writer/top100-tracker-ios` в нем находится Package.swift.

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Выберете версию пакета и настройте правило обновления. Добавьте пакет в свой проект.

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

После добавления, пакет должен появиться в Package Dependencies, а также в левой панели.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>


{% endtab %}

{% tab title="CocoaPods" %}
Добавьте модуль через **CocoaPods:**

Добавьте пакет TrackerTop100SDK в `Podfile` в своем проекте

```
platform :ios, '11.0'

target 'MyApp' do
  use_frameworks!
  pod 'TrackerTop100SDK', '1.5.1'
  ...
end
```

Обновите зависимости c помощью команды `pod install`

После этого, откройте созданный файл проекта `.xcworkspace`, там должен отобразиться подключенный пакет с фреймворком

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Carthage" %}
Добавьте модуль через **Carthage:**

Для подключения добавьте зависимость в `Cartfile`

```
binary "https://raw.githubusercontent.com/top-100-writer/top100-tracker-ios/main/TrackerTop100SDK.json" ~> 1.5.1
```

Обновите зависимости с помощью команды `carthage update --use-xcframeworks`

Откройте вкладку `General settings` вашего приложения и найдите раздел `Frameworks, Libraries, and Embedded Content`&#x20;

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Выберете пакет `TrackerTop100SDK.xcframework` из папки `Carthage/Build` на диске или просто перетяните его.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

После сборки проекта пакет в виде фреймворка должен отобразиться левой панели.

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Прямое подключение" %}
Если вы не используете системы управления зависимостями, то можете подключить фреймворк с пакетом напрямую в свое приложение.

Для подключения напрямую:

[Загрузите архив с пакетом](https://github.com/top-100-writer/top100-tracker-ios/releases/download/1.5.1/TrackerTop100SDK.xcframework.zip)

Откройте вкладку `General settings` вашего приложения и найдите раздел `Frameworks, Libraries, and Embedded Content`&#x20;

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Выберете пакет `TrackerTop100SDK.xcframework` из папки `Carthage/Build` на диске или просто перетяните его

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

После сборки проекта пакет в виде фреймворка должен отобразиться левой панели.
{% endtab %}
{% endtabs %}

## Базовая инициализация

{% tabs %}
{% tab title="Swift" %}
Инициализируйте библиотеку в методе `application(_:didFinishLaunchingWithOptions:)` вашего `AppDelegate`:

```swift
//  AppDelegate.swift
import TrackerTop100SDK

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        let settings = TrackerTop100Settings(projectId: "PROJECT_ID")!
            // ... установка параметров sdk
            .build()
        TrackerTop100.activate(settings: settings)
    }
}
```
{% endtab %}

{% tab title="Objective-C" %}
Инициализируйте библиотеку в методе `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions` вашего `AppDelegate` :

```objectivec
// AppDelegate.m
@import TrackerTop100SDK;

@implementation AppDelegate
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    TrackerTop100Settings *settings = [[TrackerTop100Settings alloc] initWithProjectId: @"PROJECT_ID"];
    // ... установка параметров sdk
    [TrackerTop100 activateWithSettings: [settings build]];
}
```
{% endtab %}
{% endtabs %}

**PROJECT\_ID** (обязательный) — идентификатор проекта (строка с цифрами), аналогичный JS-счётчику. В случае некорректного значения, `TrackerTop100Settings` не будет создан.

