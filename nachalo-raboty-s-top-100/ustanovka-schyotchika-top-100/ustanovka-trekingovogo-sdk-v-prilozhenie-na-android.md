# Установка трекингового SDK в приложение на Android

SDK под Android предоставляется в виде библиотеки в формате AAR. Библиотека доступна в [Maven-репозитории](https://search.maven.org/search?q=top100-sdk).

Добавить в файл build.gradle:

{% tabs %}
{% tab title="Kotlin" %}
```
dependencies {
    // ...
    implementation ("io.github.top-100-writer:tracker-top100-sdk:1.2.0")
}
```
{% endtab %}

{% tab title="Java" %}
```
dependencies {
    // ...
    implementation 'io.github.top-100-writer:tracker-top100-sdk:1.2.0'
}
```
{% endtab %}
{% endtabs %}

### Базовая инициализация в классе Application

Инициализируйте библиотеку в приложении и настройте отслеживание активности пользователей. Для этого объявите производный класс от базового класса `Application` и переопределите метод `onCreate()`

{% tabs %}
{% tab title="Kotlin" %}
```
import ru.top100.tracker.kraken.data.model.KrakenSettings
import ru.top100.tracker.kraken.di.Kraken

class MyApplication : MultiDexApplication() {
    override fun onCreate() {
        super.onCreate()
        Kraken.activate(
           application = this,
           krakenSettings = listOf(KrakenSettings
               .Builder(projectId = "PROJECT_ID")
               // установка параметров sdk
               .build()
            )
        )
    }
}
```
{% endtab %}

{% tab title="Java" %}
```
import ru.top100.tracker.kraken.data.model.KrakenSettings;
import ru.top100.tracker.kraken.di.Kraken;

public class MyApplication extends Application {
    @Override
    public final void onCreate() {
        super.onCreate();
        KrakenSettings config = new KrakenSettings.Builder("PROJECT_ID")
            // установка параметров sdk
            .build();
        List<KrakenSettings> krakenSettingsList = new ArrayList();
        krakenSettingsList.add(config);
        Kraken.activate((Application) getApplicationContext(), krakenSettingsList);
    }
}
```
{% endtab %}
{% endtabs %}

**PROJECT\_ID** (обязательный) - id проекта, полученный при регистрации счётчика
