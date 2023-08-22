# Отправка собственных событий

Метод используется для отправки собственных событий. Для этого необходимо его вызвать и передать название события и данные для события:

```
top100Counter.trackEvent("EVENT_NAME", EVENT_DATA);
```

**EVENT\_NAME** (обязательный) — произвольное название события

**EVENT\_DATA** (опциональный) — произвольные данные о событии, в формате объекта с вложенными параметрами, не более 30 параметров и уровней вложенности не более 5

#### Пример вызова метода:

<pre><code>const eventName = 'my_event';
const eventData = {
<strong>    param1: 'value1',
</strong>    param2: {
        param3: 'value2',
    },
};

<strong>window.top100Counter.trackEvent(eventName, eventData);
</strong></code></pre>
