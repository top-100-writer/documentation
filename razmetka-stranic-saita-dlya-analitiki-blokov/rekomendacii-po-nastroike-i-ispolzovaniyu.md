# Рекомендации по настройке и использованию

Для того чтобы настроить сбор данных по количеству показов и кликов для определённых блоков на страницах сайта, необходимо добавить data-атрибуты в разметку страниц и указать их в параметре [`attributes_dataset`](../donastroika-schetchika/atributy-schetchika.md) в коде счётчика.

При разметке блоков на странице следует придерживаться следующих принципов:

1\. Определение значения data-атрибута должно быть добавлено для каждого блока, по которому требуется собирать статистику. Название полей, используемых для этого в разметке, должно соответствовать шаблону «`data-<название>`_»_, где `<название>` – это наименование data-атрибута, из числа указываемых в коде счётчика в параметре [`attributes_dataset`](../donastroika-schetchika/atributy-schetchika.md).

Data-атрибуты можно указать при создании счётчика в интерфейсе Топ-100, тогда они  автоматически добавятся в код счётчика, который нужно будет установить на сайт. Либо  data-атрибуты можно добавить вручную в уже установленный код счётчика. ****&#x20;

**Пример передачи значения data-атрибута** `just-test-attr` **в разметке блока на сайте:**

```
<a href='link' data-just-test-attr="YOUR_LOGICAL_NAME">Link text</a>
```

**Пример установки data-атрибута** `just-test-attr` **для счётчика в интерфейсе Топ-100:**

<img src="../.gitbook/assets/image (3).png" alt="" data-size="original">

**Пример установки data-атрибута** `just-test-attr` **в коде счётчика:**

```
<!-- Top100 (Kraken) Counter -->
    // …
        var options = {
            project: PROJECT_ID,
            attributes_dataset: [ 'just-test-attr' ],
        };
    // …
<!-- END Top100 (Kraken) Counter -->
```

> _**Примечание:** После клика на блок_ `YOUR_LOGICAL_NAME` _будет зафиксировано событие “клик”_ `just-test-attr::YOUR_LOGICAL_NAME`_._



2\. Для построения дерева логической разметки необходимо использовать вложенные контейнеры с проставленными data-атрибутами.

**Пример:**

```
<div data-just-test-attr="YOUR_LOGICAL_CONTAINER">
    <a href='link' data-just-test-attr="YOUR_LOGICAL_NAME_1">Linktext</a>
    <div data-just-test-attr="YOUR_LOGICAL_CONTAINER_2">
        <a href='link' data-just-test-attr="YOUR_LOGICAL_NAME_2">Linktext</a>
    </div>
</div>
```

> _**Примечание:** При клике на ссылку_ `YOUR_LOGICAL_NAME_2` _будет зафиксировано событие_ `just-test-attr::YOUR_LOGICAL_CONTAINER::YOUR_LOGICAL_CONTAINER_2::YOUR_LOGICAL_NAME_2`_._



3\. Можно эмулировать вложенные блоки без привязки к DOM-разметке. Для этого на отдельный элемент DOM требуется назначить всю цепочку от 2-го уровня вложенности.

**Пример:**

```
<a href='link' data-just-test-attr="YOUR_LOGICAL_CONTAINER::YOUR_LOGICAL_CONTAINER_2::YOUR_LOGICAL_NAME_2">Linktext</a>
```



4\. Существует возможность добавить отправку атрибутов сразу во все счётчики, которые есть на странице. Для этого используйте параметр [`common_attributes`](../donastroika-schetchika/atributy-schetchika.md), указав в нем нужные data-атрибуты.&#x20;

**Пример:**

```
<!-- Top100 (Kraken) Counter -->
    // …
        var options = {
            project: PROJECT_ID,
            attributes_dataset: [ 'just-test-attr' ],
            common_attributes: [ 'just-common-attr' ],
        };
    // …
<!-- END Top100 (Kraken) Counter -->
```

```
<div data-just-common-attr="YOUR_LOGICAL_CONTAINER">
    <a href='link' data-just-common-attr="YOUR_LOGICAL_NAME_1">Linktext</a>
    <div data-just-common-attr="YOUR_LOGICAL_CONTAINER_2">
        <a href='link' data-just-common-attr="YOUR_LOGICAL_NAME_2">Linktext</a>
    </div>
</div>
```

> _**Примечание:** При клике на ссылку_ `YOUR_LOGICAL_NAME_2` _будет зафиксировано событие_ `just-common-attr::YOUR_LOGICAL_CONTAINER::YOUR_LOGICAL_CONTAINER_2::YOUR_LOGICAL_NAME_2`, которое будет отправлено во все счетчики на странице.



5\. С помощью метода [`sendBlocks`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) можно вызывать дополнительное сканирование блоков на странице (по атрибутам в отчётах аналитики блоков) и последующую отправку показанных новых блоков. Также в метод [`sendBlocks`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) можно передать DOM-элемент - контейнер, в рамках которого нужно осуществить поиск и отправку показанных блоков.

**Пример:**

```
window.top100Counter.sendBlocks();
```

или

```
const container = document.getElementById('container'); 
window.top100Counter.sendBlocks(container);
```
