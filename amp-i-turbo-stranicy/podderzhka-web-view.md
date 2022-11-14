# Android sdk \[Beta]

### Подключение sdk

SDK под Android предоставляется в виде библиотеки в формате AAR. Библиотека доступна в [Maven-репозитории](https://search.maven.org/search?q=top100-sdk).

Добавить в файл build.gradle&#x20;

{% tabs %}
{% tab title="Java" %}
```
dependencies {
    // ...
    implementation 'io.github.top-100-writer:tracker-top100-sdk:0.1.0'
}
```
{% endtab %}

{% tab title="Kotlin" %}
```
dependencies {
    // ...
    implementation ("io.github.top-100-writer:tracker-top100-sdk:0.1.0")
}
```
{% endtab %}
{% endtabs %}

### Базовая инициализация в классе Application

Инициализируйте библиотеку в приложении и настройте отслеживание активности пользователей. Для этого объявите производный класс от базового класса `Application` и переопределите метод `onCreate()`

{% tabs %}
{% tab title="Java" %}
```
import ru.top100.tracker.kraken.data.model.KrakenSettings;
import ru.top100.tracker.kraken.di.Kraken;

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
{% endtab %}

{% tab title="Kotlin" %}
```
import ru.top100.tracker.kraken.data.model.KrakenSettings
import ru.top100.tracker.kraken.di.Kraken

class MyApplication : MultiDexApplication() {
    override fun onCreate() {
        super.onCreate()
        Kraken
            .activate(
                application = this,
                krakenSettings = KrakenSettings
                    .Builder(projectId = "PROJECT_ID")
                    // автоматическое отслеживание загрузки активностей
                    .setActivityAutoTracking(enabled = true)
                    // установка параметров sdk
                    .build()
            )
    }
}
```
{% endtab %}
{% endtabs %}

**PROJECT\_ID** (обязательный) - id проекта, аналогичный js счетчику

