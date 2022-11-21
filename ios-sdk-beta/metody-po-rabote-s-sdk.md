# Методы по работе с sdk

### Отправка событий об активации экрана

Для ручной отправки события о просмотре экрана необходимо в контроллере вызвать следующий код

{% tabs %}
{% tab title="Swift" %}
```
TrackerTop100.trackPageView(className: "SCREEN_CLASS", url: "URL", title: "TITLE");
```
{% endtab %}

{% tab title="Objective-C" %}
```
[TrackerTop100 trackPageViewWithClassName: @"SCREEN_CLASS" url: @"URL" title: @"TITLE"];
```
{% endtab %}
{% endtabs %}

**SCREEN\_CLASS** (обязательный) — название активности, например, "MainActivity"\
**URL** (опциональный) — релевантный url для web страницы, например, "https://rambler.ru"\
**TITLE** (опциональный) — название экрана

**Пример:**

{% tabs %}
{% tab title="Swift" %}
```
import TrackerTop100SDK

class MainViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        TrackerTop100.trackPageView(className: "MainViewController", url: "https://rambler.ru", title: "Главная страница")
    }
}
```
{% endtab %}

{% tab title="Objective-C" %}
```
@import TrackerTop100SDK;

@interface MainViewController ()

@end

@implementation MainViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    [TrackerTop100 trackPageViewWithClassName: @"MainViewController" url: @"https://rambler.ru" title: @"Главная страница"];
}

@end

```
{% endtab %}
{% endtabs %}

### Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

{% tabs %}
{% tab title="Swift" %}
```
TrackerTop100.trackEvent(eventName: "EVENT_NAME", eventValues: EVENT_DATA);
```
{% endtab %}

{% tab title="Objective-C" %}
```
[TrackerTop100 trackEventWithEventName: @"EVENT_NAME" eventValues: EVENT_DATA];
```
{% endtab %}
{% endtabs %}

**EVENT\_NAME** (обязательный) — произвольное название события

**EVENT\_DATA** (опциональный) — произвольные данные о событии, не более 30 параметров в формате Dictionary \<String, String>

**Пример:**

{% tabs %}
{% tab title="Swift" %}
```
let eventName: String = "my_event"
let eventData: [String: String] = ["param_1": "value_1", "param_2": "value_2"]

TrackerTop100.trackEvent(eventName: eventName, eventValues: eventData)
```
{% endtab %}

{% tab title="Objective-C" %}
<pre><code><strong>NSString *eventName = @"my_event";
</strong><strong>NSDictionary *eventValues = @{
</strong>    @"param_1" : @"value_1",
    @"param_2" : @"value_2"
};
[TrackerTop100 trackEventWithEventName: eventName eventValues: eventValues];</code></pre>
{% endtab %}
{% endtabs %}

### Передача данных в web-view

Если есть необходимость связать события отправляемые из sdk и js-счетчика, то необходимо добавить следующий код:

{% tabs %}
{% tab title="Swift" %}
```
import WebKit
import TrackerTop100SDK

class WebViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        
        // Добавляем script после того как html загрузится
        let userScript = WKUserScript(source: TrackerTop100.getDataToWebView(), injectionTime: .atDocumentEnd, forMainFrameOnly: true)
        
        // Устанавлваем скрипт в конфигурацию загрузки webview
        let userContentController = WKUserContentController()
        userContentController.addUserScript(userScript)
        let configuration = WKWebViewConfiguration()
        configuration.userContentController = userContentController
        
        let webView = WKWebView(frame: self.view.bounds, configuration: configuration)
        
        //...
    }
}
```
{% endtab %}

{% tab title="Objective-C" %}
```
#import "WebViewController.h"
@import TrackerTop100SDK;

@interface WebViewController ()

@end

@implementation WebViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    // Добавляем script после того как html загрузится
    WKUserScript *userScript = [[WKUserScript alloc] initWithSource: [TrackerTop100 getDataToWebView] injectionTime:WKUserScriptInjectionTimeAtDocumentEnd forMainFrameOnly:YES];
    
    // Устанавлваем скрипт в конфигурацию загрузки webview
    WKUserContentController *userContentController = [[WKUserContentController alloc] init];
    [userContentController addUserScript: userScript];
    WKWebViewConfiguration *configuration = [[WKWebViewConfiguration alloc] init];
    configuration.userContentController = userContentController;
    
    WKWebView *webView = [[WKWebView alloc] initWithFrame: self.view.bounds configuration: configuration];
    
    //...
}

@end
```
{% endtab %}
{% endtabs %}
