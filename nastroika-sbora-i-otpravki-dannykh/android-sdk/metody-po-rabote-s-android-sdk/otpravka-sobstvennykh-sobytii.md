# Отправка собственных событий

При необходимости можно отправить любое собственное событие с помощью метода

{% tabs %}
{% tab title="Kotlin" %}
```
Kraken.trackEvent("EVENT_NAME", EVENT_DATA)
```
{% endtab %}

{% tab title="Java" %}
```
Kraken.trackEvent("EVENT_NAME", EVENT_DATA);
```
{% endtab %}
{% endtabs %}

**EVENT\_NAME** - произвольное название события

**EVENT\_DATA** (опциональный) - произвольные данные о событии, не более 30 параметров в формате Map\<String, String>

**Пример:**

{% tabs %}
{% tab title="Kotlin" %}
```
val eventName = "my_event"
val eventData = mapOf(
    "param_1" to "value_1",
    "param_2" to "value_2"
)

Kraken.trackEvent(
    eventName = eventName,
    params = eventData
)
```
{% endtab %}

{% tab title="Java" %}
```
String eventName = "my_event";
Map<String, String> eventData = new HashMap<>();
eventData.put("param_1", "value_1");
eventData.put("param_2", "value_2");

Kraken.trackEvent(eventName, eventData);
```
{% endtab %}
{% endtabs %}
