# Передача идентификатора пользователя

Для сбора статистики в разрезе пользователей необходимо присвоить пользователям уникальные идентификаторы и включать их в данные, отправляемые в счетчик Топ-100. Это позволит соотносить в Топ-100 активности на сайте \(просмотры, клики и т.п.\) с заданными пользователями.

Передавать идентификатор пользователя в Топ-100 нужно следующим образом:

* Указывая идентификатор пользователя в качестве параметра [`user_id`](../donastroika-schetchika/atributy-schetchika.md) и [`user_scope`](../donastroika-schetchika/atributy-schetchika.md) в коде счетчика при инициализации.

**Пример:**

```text
<!-- Top100 (Kraken) Counter -->
    // …
    var options = {
        // …
        user_id: <USER_ID>, || null
        user_scope: <USER_SCOPE>
    };
    // …
<!-- END Top100 (Kraken) Counter -->
```

* Либо передавая идентификатор через метод [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md).

Добавив в код страницы вызов [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md), можно переопределить значение [`user_id`](../donastroika-schetchika/atributy-schetchika.md), указанное в настройках счётчика при инициализации.

**Пример:**

`top100Counter.syncUserId(<USER_ID>, <USER_SCOPE>);`

**ВНИМАНИЕ!** Если планируется использование метода [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md), то обязательно в коде счетчика необходимо указать параметр [`user_id`](../donastroika-schetchika/atributy-schetchika.md) и [`user_scope`](../donastroika-schetchika/atributy-schetchika.md). Если на момент инициализации счётчика пользователь неизвестен, то в качестве [`user_id`](../donastroika-schetchika/atributy-schetchika.md) нужно указать `null`. Без указания параметра [`user_id`](../donastroika-schetchika/atributy-schetchika.md) при вызове [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) будет напечатано предупреждение в консоли.

Так можно учитывать в собираемой статистике поведение пользователя. Например:

* Если требуется указать, что пользователь разлогинился, надо вызвать метод [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) с аргументом `null`:

`top100Counter.syncUserId(null)`

* Если человек пришёл незалогиненный и залогинился в процессе работы с сайтом: в атрибутах счетчика при инициализации следует указать «`user_id: null`» и далее после авторизации передать нужный идентификатор пользователя через [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md).
* Если человек пришёл залогиненным, затем разлогинился и перелогинился: в атрибутах счетчика при инициализации следует указать исходный идентификатор пользователя, потом через [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) передать `null` \(если это необходимо\) и снова через [`syncUserId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) передать новый идентификатор.
* Если необходимо получить идентификатор пользователя и его scope можно воспользоваться методом [`getPublisherId`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md), в котором вернутся строковые значения id и scope.

`top100Counter.getPublisherId ();  
// вернет  
{  
    id: <USER_ID>,   
    scope: <USER_SCOPE>  
}`

