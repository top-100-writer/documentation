# Microdata

**Microdata** — это способ разметки, при котором данные передаются в стандартных элементах языка HTML.

Для разметки материала добавьте атрибут itemscope к любому тегу, в котором содержится описываемая сущность. Чтобы указать, что это за сущность, сразу после itemscope добавьте атрибут itemtype и в качестве его значения пропишите нужный класс в виде `itemtype="http://schema.org/<Имя класса>"`. Сущности также можно вкладывать друг в друга. Чтобы указать свойства сущности, используйте атрибут itemprop.

Для корректной передачи информации следует настроить следующие сущности:

* [Тип материала](microdata.md#tip-materiala) \[обязательно]
* [Идентификатор материала](microdata.md#identifikator-materiala) \[обязательно]
* [Заголовок материала](microdata.md#id-standartysemanticheskoimikrorazmetki-microdata-zagolovok-required) \[обязательно]
* [Дата публикации](microdata.md#data-publikacii) \[обязательно]
* [Дата модификации](microdata.md#data-modifikacii)
* [Рубрика](microdata.md#rubrika)
* [Тематика](microdata.md#tematika)
* [Автор](microdata.md#avtor)
* [Аннотация материала ](microdata.md#annotaciya-materiala-vvodnyi-abzac)(вводный абзац)
* [Текст](microdata.md#tekst)
* [Видео](microdata.md#video)

Как разметить материал:

### Тип материала

Для передачи типа необходимо воспользоваться полями [schema.org/Article](https://schema.org/Article), [schema.org/NewsArticle](http://schema.org/NewsArticle), [schema.org/BlogPosting](https://schema.org/BlogPosting) или [schema.org/WebPage](https://schema.org/WebPage).

* Article — общая разметка, подходящая всем текстовым материалам;
* NewsArticle — отдельная разметка для новостей или дополнительных материалов;
* BlogPosting — разметка для статьи из блога;
* WebPage — общая разметка, подходящая к любому материалу.

**Пример:**

`<div` `itemtype="`[`http://schema.org/Article`](http://schema.org/Article)`">`\
&#x20;   `<h1>Крым, Турция, США. Как отдыхают футболисты</h1>`\
&#x20;   `<p>Летнее межсезонье в Российской Премьер-Лиге получилось мимолётным, многие команды уже вышли из отпуска и начали подготовку к новому розыгрышу. Футболисты попытались воспользоваться этой паузой максимально продуктивно. </p>`\
`</div>`

### Идентификатор материала

Для передачи идентификатора материала необходимо настроить передачу поля [identifier](https://schema.org/identifier). Идентификатор должен содержать более 3х символов.

**Пример:**

`<meta` `itemprop="identifier"` `content="entity_78686">`

### **Заголовок материала** <a href="#id-standartysemanticheskoimikrorazmetki-microdata-zagolovok-required" id="id-standartysemanticheskoimikrorazmetki-microdata-zagolovok-required"></a>

Для передачи заголовка материала необходимо настроить передачу полей [headline](https://schema.org/headline) или [alternativeHeadline](https://schema.org/alternativeHeadline).&#x20;

**Пример:**

`<h1` `itemprop="headline">Стиль бохо входит в моду летом 2019</h1>`

### Дата публикации

Для передачи даты публикации необходимо использовать поле [datePublished](https://schema.org/datePublished). Разметка передается в формате [ISO 8601](https://www.iso.org/standard/40874.html).

**Пример:**&#x20;

`<time itemprop="datePublished"` `datetime="2019-07-17T11:45:13+04:00">17.07.2019, 11:45</time>`

### Дата модификации

Поля [datePublished](https://schema.org/datePublished) (обязательное) и дата изменения [dateModified](https://schema.org/dateModified) (опциональное). Разметка поддерживает формат [ISO 8601](https://www.iso.org/standard/40874.html).

**Пример:**

`<meta itemprop="dateModified"` `content="2019-07-18T08:21:11+04:00">`

### Рубрика

Для передачи данных по рубрикам можно использовать **** [breadcrumbList](https://schema.org/BreadcrumbList) или [genre](https://schema.org/genre).\
Рубрики отражают иерархическую структуру сайта. Рубрика может быть узкой и находиться внутри широкой темы. Определите несколько сущностей типа [ListItem](https://schema.org/ListItem) внутри класса, задайте им свойства [itemListElement](https://schema.org/itemListElement), которые описывают текущую и более широкие рубрики. Рубрикой данного материала будет считаться значение сущности с наибольшим position.

**Пример:**

`<p><meta itemprop="genre" content="style, fashion"/>Новый стиль моды в Москве</p>`

**Пример:**

`<ol` `itemscope=""` `itemtype="`[`http://schema.org/BreadcrumbList`](http://schema.org/BreadcrumbList)`">` \
&#x20; `<li` `itemprop="itemListElement"` `itemscope=""` `itemtype="`[`http://schema.org/ListItem`](http://schema.org/ListItem)`">` \
&#x20;   `<a` `itemprop="item"` `href="//site.ru/fashion">` \
&#x20;   `<span` `itemprop="name">Мода</span></a>` \
&#x20;   `<meta` `itemprop="position"` `content="1">` \
&#x20; `</li>` \
&#x20; `<li` `itemprop="itemListElement"` `itemscope=""` `itemtype="`[`http://schema.org/ListItem`](http://schema.org/ListItem)`">` \
&#x20;   `<a` `itemprop="item"` `href="//site.ru/fashion/boho">` \
&#x20;   `<span` `itemprop="name">Стиль бохо</span></a>` \
&#x20;   `<meta` `itemprop="position"` `content="2">` \
&#x20; `</li>` \
&#x20; `<li` `itemprop="itemListElement"` `itemscope=""` `itemtype="`[`http://schema.org/ListItem`](http://schema.org/ListItem)`">` \
&#x20;   `<a` `itemprop="item"` `href="//site.ru/fashion/boho/woven-bags">` \
&#x20;   `<span` `itemprop="name">Плетеные сумки</span></a>` \
&#x20;   `<meta` `itemprop="position"` `content="3">` \
&#x20; `</li>` \
`</ol>`

### Тематика

Для передачи тематики необходимо использовать поле [about](https://schema.org/about). Тематики отражают содержание статьи. В отличие от рубрик, количество тематик материала не ограничено. Обозначьте ее ключевыми словами или тегами.

**Пример:**

`<div` `itemprop="about">Мода</div>` \
&#x20; `<div` `itemprop="about"` `itemscope=""` `itemtype="`[`https://schema.org/Thing`](https://schema.org/Thing)`">` `` \
&#x20; `<span` `itemprop="name">Одежда</span>` \
`</div>`

### Автор

Для передачи автора можно воспользоваться полями [author](https://schema.org/author) или [person](https://schema.org/Person). Если их несколько, укажите каждого в отдельном теге.

`<div` `itemprop="author">Автор статьи</div>`\
`<div` `itemprop="author"` `itemscope=""` `itemtype="`[`http://schema.org/Person`](http://schema.org/Person)`">    <span` `itemprop="name">Автор статьи</span></div>`

### Аннотация материала (вводный абзац)

### Текст

### Видео







