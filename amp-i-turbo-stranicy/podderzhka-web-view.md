# Android sdk \[Beta]

### Подключение sdk

Добавить в папку libs .aar архив (выдается по запросу)

Добавить в файл build.gradle&#x20;

```
dependencies {
    // ...
    implementation files ('libs/kraken-x.x.x.aar')
}
```

### Базовая инициализация в классе Application

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
                 // установка параметров sdk
                 .build()
        )
        // вызов методов sdk
    }
}
```

**PROJECT\_ID** (обязательный) - id проекта, аналогичный js счетчику

