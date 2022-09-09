# iOS sdk \[Beta]

### Подключение sdk

Добавить модуль можно через **Swift Package Manager**

В Xcode выберите свой проект и перейдите на вкладку Package Dependencies

<figure><img src="../.gitbook/assets/Снимок экрана 2022-09-07 в 14.20.15.png" alt=""><figcaption><p>Xcode</p></figcaption></figure>

Добавьте новый пакет через указание URL репозитория. Ссылка на модуль выдается по запросу

<figure><img src="../.gitbook/assets/Снимок экрана 2022-09-07 в 14.27.08.png" alt=""><figcaption><p> Xcode</p></figcaption></figure>

Выбираем зависимость по тегам и добавляем в проект

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

**PROJECT\_ID** (обязательный) - id проекта, аналогичный js счетчику
