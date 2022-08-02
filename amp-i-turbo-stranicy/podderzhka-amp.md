# Поддержка AMP

Для сбора базовой статистики с [AMP-страниц](https://www.ampproject.org/) на каждой их них необходимо разместить код вида:

```
<!-- Top100.rambler.ru example -->
<amp-analytics type="top100" id="top100" config="https://kraken.rambler.ru/amp/config.json">
<script type="application/json">
{
    "vars": {
        "pid": "PROJECT_ID"
    }
}
</script>
</amp-analytics>
<!-- End Top100.rambler.ru example -->
```

При этом в коде в блоке `vars` обязательно необходимо указывать в качестве параметра `pid`идентификатор соответствующего счетчика.

Накопленная статистика будет доступна для просмотра в отчетах:

* Посещаемость,
* Технологии,
* Содержание,
* Аудитория,
* Источники трафика.
