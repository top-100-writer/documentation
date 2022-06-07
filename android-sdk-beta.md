# Android Sdk \[BETA]

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
import ru.sberads.kraken.Kraken;
import ru.sberads.kraken.KrakenSettings;

public class MyApplication extends Application {
    @Override
    public final void onCreate() {
        KrakenSettings krakenSettings = new KrakenSettings.Builder(getApplicationContext(), "PROJECT_ID")
            // ...
            .build();
        Kraken.activate(getApplicationContext(), krakenSettings);
        Kraken.activateAutoTracking(this);
    }
}
```

**PROJECT\_ID** (обязательный) - id проекта, аналогичный js счетчику

### Отправка событий об активации экрана

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
