# Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

{% tabs %}
{% tab title="Swift" %}
```swift
TrackerTop100.trackEvent(eventName: "EVENT_NAME", customVars: EVENT_DATA);
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
[TrackerTop100 trackEventWithEventName: @"EVENT_NAME" eventValues: EVENT_DATA];
```
{% endtab %}
{% endtabs %}

**EVENT\_NAME** (обязательный) — произвольное название события

**EVENT\_DATA** (опциональный) — произвольные данные о событии, не более 30 параметров в формате `Dictionary<String, String>`

**Пример:**

{% tabs %}
{% tab title="Swift" %}
<pre class="language-swift"><code class="lang-swift">import TrackerTop100SDK
<strong>// ...
</strong>let eventName: String = "my_event"
let eventData: [String: String] = ["param_1": "value_1", "param_2": "value_2"]

TrackerTop100.trackEvent(eventName: eventName, eventValues: eventData)
</code></pre>
{% endtab %}

{% tab title="Objective-C" %}
<pre class="language-objectivec"><code class="lang-objectivec"><strong>NSString *eventName = @"my_event";
</strong><strong>NSDictionary *eventValues = @{
</strong>    @"param_1" : @"value_1",
    @"param_2" : @"value_2"
};
[TrackerTop100 trackEventWithEventName: eventName eventValues: eventValues];
</code></pre>
{% endtab %}
{% endtabs %}
