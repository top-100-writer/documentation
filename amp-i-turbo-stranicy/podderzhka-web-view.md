# Android sdk \[Beta]

### Подключение sdk

SDK под Android предоставляется в виде библиотеки в формате AAR. Библиотека доступна в [Maven-репозитории](https://search.maven.org/search?q=top100-sdk).

Добавить в файл build.gradle&#x20;

```
dependencies {
    // ...
    // непосредственно sdk
    implementation 'io.github.top-100-writer:tracker-top100-sdk:0.0.19'
    // зависимости
    implementation 'androidx.datastore:datastore-core:1.0.0'
    implementation 'com.google.protobuf:protobuf-javalite:3.21.2'
    implementation 'com.google.code.gson:gson:2.9.1'
    implementation 'com.squareup.okhttp3:okhttp:5.0.0-alpha.9'
    implementation 'com.squareup.okhttp3:logging-interceptor:5.0.0-alpha.9'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
    implementation 'com.google.android.gms:play-services-appset:16.0.2'
    implementation 'com.google.android.gms:play-services-ads-identifier:18.0.1'
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

