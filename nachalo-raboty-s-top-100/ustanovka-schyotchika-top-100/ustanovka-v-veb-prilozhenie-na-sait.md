# Установка в веб-приложение (на сайт)

Выполнив все необходимые настройки в Топ-100, можно добавить соответствующий счетчик в веб-приложение. Для этого в HTML-код сайта следует вставить сгенерированный код.

Для корректного подсчёта статистики необходимо установить код на все страницы сайта.

{% hint style="warning" %}
**ВНИМАНИЕ!** Для корректного подсчета событий для single-page application следует использовать метод [`trackPageview`](broken-reference).&#x20;
{% endhint %}

Код можно встроить в любое место HTML-кода. Рекомендуется вставлять его в начало страницы, чтобы счётчик успел загрузиться при коротком визите.

**Пример кода счётчика для асинхронной загрузки:**

```
<!-- Top100 (Kraken) Counter -->
<script>
(function (w, d, c) {
    (w[c] = w[c] || []).push(function() {
        var options = {
            project: 'PROJECT_ID'
        };
        try {
            w.top100Counter = new top100(options);
        } catch(e) { }
    });
    var n = d.getElementsByTagName("script")[0],
    s = d.createElement("script"),
    f = function () { n.parentNode.insertBefore(s, n); };
    s.type = "text/javascript";
    s.async = true;
    s.src =
        (d.location.protocol == "https:" ? "https:" : "http:") +
        "//st.top100.ru/top100/top100.js”;
    if (w.opera == "[object Opera]") {
        d.addEventListener("DOMContentLoaded", f, false);
    } else { f(); }
})(window, document, "_top100q");
</script>
<noscript><img src="//counter.rambler.ru/top100.cnt?pid=PROJECT_ID"></noscript>
<!-- END Top100 (Kraken) Counter -->
```

**PROJECT\_ID** (обязательный) - id проекта, полученный при регистрации счётчика

> _**Примечание:** Можно добавить на страницу сайта код счетчика для синхронной загрузки. Но следует иметь в виду, что при синхронной загрузке, пока счётчик не инициализируется полностью, все остальные скрипты не будут загружены._

**Пример кода счетчика для синхронной загрузки:**

```
<script src="//st.top100.ru/top100/top100.js"></script>
<script>
    var options = {
        project: 'PROJECT_ID'`
    };
    try {
        window.top100Counter = new top100(options);
    } catch(e) { }
</script>
<noscript><img src="//counter.rambler.ru/top100.cnt?pid=PROJECT_ID"></noscript>
<!-- END Top100 (Kraken) Counter -->
```

{% hint style="warning" %}
**ВНИМАНИЕ!** Статистика перестанет собираться, если на вашем сайте не будет ни одного посещения в течение девяти календарных дней. При этом в случае участия в рейтинге сайт оттуда пропадёт, и соответствующая настройка счетчика будет сброшена. Если в дальнейшем будет зафиксировано посещение, то сбор статистики возобновится. Участие в рейтинге автоматически восстановится, и сайт будет возвращен в рейтинг.&#x20;
{% endhint %}
