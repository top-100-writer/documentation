# Методы по работе с sdk

### Включение/отключение автоматической отправки события о переходе на активность

Включение автоматической отправки данных

```
Kraken.enableActivityAutoTracking()
```

Отключение автоматической отправки данных

```
Kraken.disableActivityAutoTracking()
```

Данные методы можно вызывать в любых классах и активностях приложения

### Отправка событий об активации экрана

Если передается настройка Kraken.activateAutoTracking(this), то запуск активностей в первый раз фиксируется автоматически. Если необходимо самостоятельно фиксировать просмотр экрана, то можно воспользоваться отдельным методом.

Для ручной отправки события о просмотре экрана необходимо при активации Activity при ее создании выполнить следующий код

```
Kraken.trackPageView("SCREEN_CLASS", "URL", "TITLE");
```

**SCREEN\_CLASS** (обязательный) - название активности, например, "MainActivity"\
**URL** (опциональный) - релевантный url для web страницы, например, "https://rambler.ru"\
**TITLE** (опциональный) - название экрана

### Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

```
Kraken.trackEvent("EVENT_NAME", EVENT_DATA);
```

**EVENT\_NAME** - произвольное название события

**EVENT\_DATA** (опциональный) - произвольные данные о событии, не более 30 параметров в формате Map\<String, String>

Пример:

```
String eventName = "my_event";
Map<String, String> eventData = new HashMap<>();
eventData.put("param_1", "value_1");
eventData.put("param_2", "value_2");

Kraken.trackEvent(eventName, eventData);
```

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

