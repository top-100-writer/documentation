# Методы по работе с sdk

### Отправка событий об активации экрана

Для ручной отправки события о просмотре экрана необходимо в контроллере вызвать следующий код

```
TrackerTop100.trackPageView(className: "SCREEN_CLASS", url: "URL", title: "TITLE");
```

**SCREEN\_CLASS** (обязательный) - название активности, например, "MainActivity"\
**URL** (опциональный) - релевантный url для web страницы, например, "https://rambler.ru"\
**TITLE** (опциональный) - название экрана

**Пример:**

<pre><code>import TrackerTop100SDK

<strong>class MainViewController: UIViewController {
</strong>    override func viewDidLoad() {
        super.viewDidLoad()
        TrackerTop100.trackPageView(className: "MainViewController", url: "https://rambler.ru", title: "Главная страница")
    }
}</code></pre>

### Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

```
TrackerTop100.trackEvent(eventName: "EVENT_NAME", eventValues: EVENT_DATA);
```

**EVENT\_NAME** - произвольное название события

**EVENT\_DATA** (опциональный) - произвольные данные о событии, не более 30 параметров в формате Dictionary \<String, String>

**Пример:**

```
let eventName: String = "my_event"
let eventData: [String: String] = ["param_1": "value_1", "param_2": "value_2"]

TrackerTop100.trackEvent(eventName: eventName, eventValues: eventData)
```

### Передача данных в web-view

Если есть необходимость связать события отправляемые из sdk и js-счетчика, то необходимо добавить следующий код:

```
import WebKit
import TrackerTop100SDK

class WebViewController: UIViewController {
    let webView = WKWebView()
    // ...
    override func viewDidAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        
        let jsString = "window.Kraken.getData = function() { return \"\(TrackerTop100.getData())\" }"
        webView.evaluateJavaScript(jsString)
    }
    // ...
}

```

