# Отправка событий о показе экрана

Для ручной отправки события о просмотре экрана необходимо в контроллере вызвать следующий код

{% tabs %}
{% tab title="Swift" %}
```swift
TrackerTop100.trackPageView(className: "SCREEN_CLASS", url: "URL", title: "TITLE");
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
[TrackerTop100 trackPageViewWithClassName: @"SCREEN_CLASS" url: @"URL" title: @"TITLE"];
```
{% endtab %}
{% endtabs %}

**SCREEN\_CLASS** (обязательный) — название активности, например, "MainActivity"\
**URL** (опциональный) — релевантный url для веб-страницы, например, "https://www.rambler.ru"\
**TITLE** (опциональный) — название экрана

**Пример:**

{% tabs %}
{% tab title="Swift" %}
```swift
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
```objectivec
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
