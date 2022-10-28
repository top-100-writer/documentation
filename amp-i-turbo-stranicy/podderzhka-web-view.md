# Android sdk \[Beta]

### Подключение sdk

SDK под Android предоставляется в виде библиотеки в формате AAR. Библиотека доступна в [Maven-репозитории](https://search.maven.org/search?q=top100-sdk).

Добавить в файл build.gradle&#x20;

```
dependencies {
    // ...
    implementation 'io.github.top-100-writer:tracker-top100-sdk:0.0.21'
}
```

### Базовая инициализация в классе Application

Инициализируйте библиотеку в приложении и настройте отслеживание активности пользователей. Для этого объявите производный класс от базового класса `Application` и переопределите метод `onCreate()`

```
import ru.top100.tracker.kraken.data.model.KrakenSettings
import ru.top100.tracker.kraken.di.Kraken

public class MyApplication extends Application {
    @Override
    public final void onCreate() {
        Kraken.activate(
             application = this,
             krakenSettings = KrakenSettings
                 .Builder(projectId = "PROJECT_ID")
                 // автоматическое отслеживание загрузки активностей
                 .setActivityAutoTracking(enabled = true)
                 // установка параметров sdk
                 .build()
        )
        // вызов методов sdk
    }
}
```

**PROJECT\_ID** (обязательный) - id проекта, аналогичный js счетчику

