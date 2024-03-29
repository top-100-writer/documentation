# Передача E-commerce данных

С помощью Топ-100 можно выполнять сбор и анализ данных, относящихся к области электронной коммерции (eCommerce). Реализовать это можно, используя счетчик Топ-100, в коде которого в качестве одного из параметров указывается контейнер eCommerce-данных (по умолчанию – `dataLayer`).

**Пример кода счетчика с прописанным параметром ecommerce:**

```
<!-- Top100 (Kraken) Counter -->
<script>
(function (w, d, c) {
    (w[c] = w[c] || []).push(function() {
        var options = {
            project: 'PROJECT_ID',
            // …
            ecommerce: 'dataLayer'
        };
        try {
            w.top100Counter = new top100(options);
        } catch(e) { }
    });
// …
})(window, document, "_top100q");
</script>
// …
<!-- END Top100 (Kraken) Counter -->
```

Для подключения сбора данных необходимо разместить контейнер данных на страницах сайта и настроить передачу в Топ-100 данных о событиях, происходящих с товарами (например, добавление в корзину или покупка). Данные о действиях с товарами передаются push-методом в контейнер данных в виде JavaScript-объектов, содержащих идентификатор действия и список описаний товаров, с которыми это действие произведено:

```
<script type="text/javascript">
    window.dataLayer = window.dataLayer || [];
</script>
// …
<script type="text/javascript">
    window.dataLayer.push({…});
</script>
```

Передаваемые данные должны представлять из себя eCommerce-объекты [определенного формата.](https://top-100-writer.gitbook.io/top100-documentation/peredacha-dannykh-elektronnoi-kommercii/format-ecommerce-dannykh)

Для корректного сбора статистики следуйте рекомендациям по [передаче eCommerce-данных.](https://top-100-writer.gitbook.io/top100-documentation/peredacha-dannykh-elektronnoi-kommercii/rekomendacii-po-peredache-ecommerce-dannykh)

> _Дополнительно смотрите примеры_ [_передачи eCommerce-данных._](https://top-100-writer.gitbook.io/top100-documentation/peredacha-dannykh-elektronnoi-kommercii/primery-peredachi-ecommerce-dannykh)

{% hint style="warning" %}
**ВНИМАНИЕ!** Для корректной отправки статистики необходимо сначала вызывать скрипт загрузки счётчика Топ-100 на странице, и уже потом отправлять данные в контейнер. Т.е. скрипт, содержащий «`dataLayer.push`», должен быть размещен после инициализации счётчика «`ecommerce: 'dataLayer'`».
{% endhint %}

{% hint style="info" %}
**ВНИМАНИЕ!** Используемое по умолчанию имя контейнера данных `dataLayer` и структура вкладываемых в него eCommerce-объектов соответствуют аналогичным сущностям в Яндрекс.Метрике и Google Analytics Enhanced Ecommerce. Если ваш интернет-магазин уже размечен под эти системы аналитики, достаточно добавить счётчик Топ-100 с подключенным сбором данных для eCommerce на сайт, и он автоматически начнёт собирать эти данные. При этом в качестве контейнера данных используется JavaScript-массив `window.dataLayer`. Если сайт не был предварительно размечен для передачи eCommerce-данных в Яндекс.Метрику или Google Analytics, необходимо разместить контейнер данных на страницах сайта и настроить передачу в Топ-100 событий, происходящих с товарами. Контейнер данных должен находиться в глобальном пространстве имен, а его имя соответствовать имени, заданному при настройке или инициализации счетчика.
{% endhint %}

