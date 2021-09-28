# Разметка страниц сайта для аналитики блоков

При необходимости можно настроить сбор данных по количеству показов и нажатий на интересующие блоки страниц сайта.

Для этого следует добавить в разметку страниц сайта data-атрибуты и указать в коде счетчика через параметр [`attributes_dataset`](../donastroika-schetchika/atributy-schetchika.md) используемые наименования data-атрибутов.

Накопленная статистика будет доступна для просмотра в отчете «Аналитика блоков»:

* При указании нескольких различных data-атрибутов в отчёте «Аналитика блоков» статистика будет представлена в разрезе нескольких деревьев: название каждого data-атрибута станет первым уровнем дерева в отчёте. Так, например, если необходимо собирать три типа событий: клики по партнёрским блокам, клики по блокам с новостями, клики по панели навигации, то для удобства работы с данными в отчёте можно создать три data-атрибута: partner, news, navigation.
* Для отчёта «Аналитика блоков» собираются только показы блоков и клики по ним. В отчёте также можно увидеть CTR блока. Показы и клики суммируются на каждом уровне дерева размеченных элементов сайта \(осуществляется суммирование по вложенным элементам\). Если же вам важно видеть посетителей и визиты, используйте разметку [параметров визита](peredacha-parametrov-vizita.md) \(см. описание метода [`sendCustomVars`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md)\) вместо аналитики блоков.

При разметке страниц сайта для сбора статистики по блокам следует придерживаться следующих принципов:

1.Определение значения data-атрибута должно быть добавлено для каждого блока, по которому требуется собирать статистику. Название полей, используемых для этого в разметке, должно соответствовать шаблону «`data-<название>`_»_, где `<название>` – это наименование data-атрибута, из числа задаваемых в коде счетчика через параметр [`attributes_dataset`](../donastroika-schetchika/atributy-schetchika.md).

**Пример указания значения data-атрибута** `just-test-attr` **в разметке блока на сайте:**

`<a href=’link’ data-just-test-attr=’YOUR_LOGICAL_NAME’>Link text</a>`

**Пример передачи data-атрибута** `just-test-attr` **в атрибутах счетчика:**

```text
<!-- Top100 (Kraken) Counter -->
    // …
    var options = {
        project: PROJECT_ID,
        attributes_dataset: [ ‘just-test-attr’ ]
    };
    // …
<!-- END Top100 (Kraken) Counter -->
```

> _**Примечание:** После клика на блок_ `YOUR_LOGICAL_NAME` _будет зафиксировано событие “нажатие”_ `just-test-attr::YOUR_LOGICAL_NAME`_._

2.Для построения дерева логической разметки необходимо использовать вложенные контейнеры с проставленными data-атрибутами.

**Пример:**

`<div data-just-test-attr=’YOUR_LOGICAL_CONTAINER’>`

`<a href=’link’ data-just-test-attr=’YOUR_LOGICAL_NAME_1’>Linktext</a>`

`<div data-just-test-attr=’YOUR_LOGICAL_CONTAINER_2’>`

`<a href=’link’ data-just-test-attr=’YOUR_LOGICAL_NAME_2’>Linktext</a>`

`</div>`

`</div>`

> _**Примечание:** По нажатию на ссылку_ `YOUR_LOGICAL_NAME_2` _будет зафиксировано событие_ `just-test-attr::YOUR_LOGICAL_CONTAINER::YOUR_LOGICAL_CONTAINER_2::YOUR_LOGICAL_NAME_2`_._

3.Существует возможность эмулировать вложенные блоки без привязки к DOM-разметке. Для этого на отдельный элемент DOM требуется назначить всю цепочку от 2-го уровня вложенности.

**Пример:**

`<a href=’link’ data-just-test-attr=’YOUR_LOGICAL_CONTAINER::YOUR_LOGICAL_CONTAINER_2::YOUR_LOGICAL_NAME_2’>Link text</a>`
