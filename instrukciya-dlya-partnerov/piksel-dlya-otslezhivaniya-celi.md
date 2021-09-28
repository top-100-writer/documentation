# Пиксель для отслеживания цели

Шаблон кода:

```text
<!-- Top100 (Kraken) Counter -->
<script>
(function (w, d, c) {
  (w[c] = w[c] || []).push(function() {
      var goals = {
        'goal': '<GOAL-ID>'
      };   
      var options = {
          project: <PROJECT_ID>,
          custom_vars: goals
      }; 
      try {
          w['t<PROJECT_ID>'] = new top100(options);
      } catch(e) { }
  });

  var n = d.getElementsByTagName("script")[0],
      s = d.createElement("script"),
      f = function () { n.parentNode.insertBefore(s, n); };
  s.type = "text/javascript";
  s.async = true;
  s.src =
      (d.location.protocol == "https:" ? "https:" : "http:") +
      "//st.top100.ru/top100/top100.js";

  if (w.opera == "[object Opera]") {
      d.addEventListener("DOMContentLoaded", f, false);
  } else { f(); }
})(window, document, "_top100q");
</script>
<!-- END Top100 (Kraken) Counter -->
```

При такой разметке параметр отправляется с логом pv при инициализации счетчика.

Вместо &lt;PROJECT\_ID&gt; необходимо вставить идентификатор счетчика, аналогичный идентификатору в коде на все страницы.

Вместо &lt;GOAL-ID&gt; необходимо вставить идентификатор цели. Идентификатором цели может быть любая строка. Для удобства лучше использовать осмысленные идентификаторы, например x5m\_testdrive, x5mconfigurator и т.д. Идентификатор цели может содержать символы a-z, A-Z, 0-9, \_ Желательно, чтобы символы были в одном регистре.

