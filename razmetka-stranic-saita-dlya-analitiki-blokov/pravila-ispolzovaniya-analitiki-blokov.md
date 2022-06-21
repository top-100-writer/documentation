# Правила использования аналитики блоков

Для того чтобы настроить сбор данных по количеству показов и нажатий на интересующие блоки страниц сайта, следует добавить в разметку страниц сайта data-атрибуты и указать в коде счетчика через параметр [`attributes_dataset`](../donastroika-schetchika/atributy-schetchika.md) используемые наименования data-атрибутов.

При разметке страниц сайта для сбора статистики по блокам следует придерживаться следующих принципов:

1\. Определение значения data-атрибута должно быть добавлено для каждого блока, по которому требуется собирать статистику. Название полей, используемых для этого в разметке, должно соответствовать шаблону «`data-<название>`_»_, где `<название>` – это наименование data-атрибута, из числа задаваемых в коде счетчика через параметр [`attributes_dataset`](../donastroika-schetchika/atributy-schetchika.md).

Data-атрибуты можно указать при создании счетчика в интерфейсе Топ-100. При этом, указанные data-атрибуты автоматически добавятся в код счетчика, который нужно будет установить на сайт. Также, data-атрибуты можно вручную добавить в уже установленный код счетчика. ****&#x20;

**Пример указания значения data-атрибута** `just-test-attr` **в разметке блока на сайте:**

```
<a href='link' data-just-test-attr="YOUR_LOGICAL_NAME">Link text</a>
```

**Пример передачи data-атрибута** `just-test-attr` **в атрибутах счетчика в интерфейсе Топ-100:**

<img src="../.gitbook/assets/image (3).png" alt="" data-size="original">

**Пример передачи data-атрибута** `just-test-attr` **в атрибутах счетчика:**

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



3\. Существует возможность эмулировать вложенные блоки без привязки к DOM-разметке. Для этого на отдельный элемент DOM требуется назначить всю цепочку от 2-го уровня вложенности.

**Пример:**

```
<a href='link' data-just-test-attr="YOUR_LOGICAL_CONTAINER::YOUR_LOGICAL_CONTAINER_2::YOUR_LOGICAL_NAME_2">Linktext</a>
```



4\. Существует возможность добавить отправку атрибутов сразу во все счетчики, которые есть на странице. Для этого можно воспользоваться параметром [`common_attributes`](../donastroika-schetchika/atributy-schetchika.md) и указать в нем нужные data-атрибуты.&#x20;

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



5\. С помощью метода [`sendBlocks`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) можно вызвать дополнительное сканирование блоков на странице (по атрибутам в отчетах аналитики блоков) и последующую отправку показанных новых блоков. Также в метод [`sendBlocks`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) можно передать DOM элемент - контейнер в рамках которого нужно осуществить поиск и отправку показанных блоков.

**Пример:**

```
window.top100Counter.sendBlocks();
```

или

```
const container = document.getElementById('container'); 
window.top100Counter.sendBlocks(container);
```
