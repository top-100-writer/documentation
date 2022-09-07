# Методы по работе с sdk

### Отправка событий об активации экрана

Для ручной отправки события о просмотре экрана необходимо в контроллере вызвать следующий код

```
kraken!.trackPageView(className: "SCREEN_CLASS", url: "URL", title: "TITLE");
```

**SCREEN\_CLASS** (обязательный) - название активности, например, "MainActivity"\
**URL** (опциональный) - релевантный url для web страницы, например, "https://rambler.ru"\
**TITLE** (опциональный) - название экрана

**Пример:**

```
class MainViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        kraken!.trackPageView(className: "MainViewController", url: "https://rambler.ru", title: "Главная страница")
    }
}
```

### Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

```
Kraken.trackEvent(eventName: "EVENT_NAME", eventValues: EVENT_DATA);
```

**EVENT\_NAME** - произвольное название события

**EVENT\_DATA** (опциональный) - произвольные данные о событии, не более 30 параметров в формате Dictionary \<String, String>

**Пример:**

```
let eventName: String = "my_event"
let eventData: [String: String] = ["param_1": "value_1", "param_2": "value_2"]

kraken!.trackEvent(eventName: eventName, eventValues: eventData)
```

### Передача данных в web-view

Если есть необходимость связать события отправляемые из sdk и js-счетчика, то необходимо добавить следующий код:

```
// пример
```

