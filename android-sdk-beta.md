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

### Инициализация в классе Application

```
import ru.rambler.android.kraken.data.model.KrakenSettings
import ru.rambler.android.kraken.di.Kraken.activateAutoTracking

public class MyApplication extends Application {
    @Override
    public final void onCreate() {
        KrakenSettings krakenSettings = new KrakenSettings.Builder("PROJECT_ID")
            // установка параметров
            .build();
        Kraken.activate(getApplicationContext(), krakenSettings);
        Kraken.activateAutoTracking(this);
    }
}
```

**PROJECT\_ID** (обязательный) - id проекта, аналогичный js счетчику

### Параметры возможные для передачи при инициализации

Передача идентификатора пользователя от площадки

```
.publisherId("PUBLISHER_ID")
```

Передача области видимости идентификатора

```
.publisherScope("PUBLISHER_SCOPE")
```

Передача авторизованного идентификатора пользователя

```
.userId("AUTH_USER_ID")
```

Передача телефона пользователя.  Данные хэшируются алгоритмом sha256

```
.phoneHash("9-910-910-10-90")
```

Передача email пользователя.  Данные хэшируются алгоритмом sha256

```
.emailHash(email@rambler.ru)
```

### Отправка событий об активации экрана

Если передается настройка Kraken.activateAutoTracking(this), то запуск активностей в первый раз фиксируется автоматически. Если необходимо самостоятельно фиксировать просмотр экрана, то можно воспользоваться отдельным методом.

Для ручной отправки события о просмотре экрана необходимо при активации Activity при ее создании выполнить следующий код

```
Kraken.trackPageView("SCREEN_CLASS", "URL");
```

**SCREEN\_CLASS** (обязательный) - название активности, например, "MainActivity"\
**URL** (опциональный) - релевантный url для web страницы, например, "http://rambler.ru"

### Передача данных в web-view

Если есть необходимость связать события отправляемые из sdk и js-счетчика, то необходимо добавить следующий код в Activity:

```
@Override
protected void onCreate(Bundle savedInstanceState) {
    webView = findViewById(R.id.webView);
    webView.getSettings().setJavaScriptEnabled(true);
    webView.loadUrl("https://someurl");
    webView.setWebViewClient(new MyWebViewClient());
    webView.addJavascriptInterface(new MyJavaInterface(), "kraken");
}

 private class MyJavaInterface {
    @android.webkit.JavascriptInterface
    public String getData() {
        return Kraken.getData();
    }
 }
```

### Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

```
Kraken.trackEvent("EVENT_NAME", EVENT_DATA);
```

EVENT\_NAME - произвольное название события

EVENT\_DATA - произвольные данные о событии, не более 30 параметров в формате Map\<String, String>

Пример:

```
String eventName = "my_event";
Map<String, String> eventData = new HashMap<>();
eventData.put("param", "value");

Kraken.trackEvent(eventName, eventData);
```
