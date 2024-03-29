# Разметка разделов сайта

С помощью Топ-100 можно собирать статистику в разрезе заданного перечня страниц сайта.

Для этого каждой странице сайта нужно присвоить свой уникальный идентификатор. И указать его в добавляемом на страницу коде счетчика в качестве значения атрибута [`chapters`](parametry-schyotchika-top-100.md). Так событие просмотра пользователем страницы будет однозначно ассоциировано с соответствующим идентификатором.

Если на сайте существует определенная иерархия страниц, и необходимо ее отразить в статистике, то можно объединить идентификаторы страниц в деревья вида `'landing::page_1::page_2'`. Для этого в коде счётчика каждой страницы в атрибуте [`chapters`](parametry-schyotchika-top-100.md) необходимо передавать список идентификаторов от корневой страницы до текущей.

Накопленная статистика будет доступна для просмотра в отчете «Разделы сайта».

Если в настройках счетчика задана иерархия страниц, то при подсчете событий для каждой страницы будет выполняться суммирование по дочерним страницам. В результате будет доступна как агрегированная статистика по головным страницам, так и отдельная статистика по дочерним.

На множестве страниц одного сайта можно задать несколько разных иерархий. Таким образом, в отчете «Разделы сайта» может существовать более чем одно дерево страниц.

**ВНИМАНИЕ!** У каждой страницы должен быть строго один идентификатор, иначе обсчёт будет некорректным.

**Пример кода экземпляра счетчика с определением атрибута** `chapters`**:**

```
<!-- Top100 (Kraken) Counter -->
    // …
    var options = {
        // …
        chapters: [ // chapters страницы
            'landing',
            'page_1',
            'page_2'
        ]
    };
    // …
<!-- END Top100 (Kraken) Counter -->
```

