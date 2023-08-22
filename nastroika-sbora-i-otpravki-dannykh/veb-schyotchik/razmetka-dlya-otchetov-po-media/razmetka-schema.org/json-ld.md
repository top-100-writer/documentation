# JSON-LD

**JSON-LD** — это способ разметки, при котором данные передаются с помощью объектов [связанных данных](https://ru.wikipedia.org/wiki/Linked\_data) (Linked Data, LD).Данные в формате JSON-LD описываются набором разделенных запятыми пар ключ-значение. Формат предусматривает зарезервированные ключи, с помощью которых можно определять контекст описания или связывать объекты различным образом. Например, @context определяет словарь объектов (в данном случае — Schema.org), а @type — тип описываемой сущности.Для корректной передачи информации следует настроить следующие сущности:

* [​Тип материала ](json-ld.md#tip-materiala)\[обязательно]
* [​Идентификатор материала](json-ld.md#identifikator-materiala) \[обязательно]
* [​Заголовок материала](json-ld.md#id-standartysemanticheskoimikrorazmetki-microdata-zagolovok-required) \[обязательно]
* ​[Url материала / контейнер](json-ld.md#url-materiala-konteiner) \[обязательно]
* [​Дата публикации](json-ld.md#data-publikacii) \[обязательно]
* [​Дата модификации​](json-ld.md#data-modifikacii)
* [​Рубрика​](json-ld.md#rubrika)
* [​Автор​](json-ld.md#avtor)
* [​Аннотация материала](json-ld.md#annotaciya-materiala-vvodnyi-abzac) (вводный абзац)
* [​Текст​](json-ld.md#tekst)
* [​Изображение​](json-ld.md#izobrazhenie)

Как разметить материал:

#### Тип материала <a href="#tip-materiala" id="tip-materiala"></a>

Для передачи типа необходимо воспользоваться полями [schema.org/Article](https://schema.org/Article), [schema.org/NewsArticle](http://schema.org/NewsArticle), [schema.org/BlogPosting](https://schema.org/BlogPosting) или [schema.org/WebPage](https://schema.org/WebPage).

* Article — общая разметка, подходящая всем текстовым материалам;
* NewsArticle — отдельная разметка для новостей или дополнительных материалов;
* BlogPosting — разметка для статьи из блога;
* WebPage — общая разметка, подходящая к любому материалу.

**Пример:**

`<script` `type="application/ld+json">` `{ "@context":"`[`https://schema.org`](https://schema.org/)`", "@type":"Article", ... } </script>`

#### Идентификатор материала <a href="#identifikator-materiala" id="identifikator-materiala"></a>

Для передачи идентификатора материала необходимо настроить передачу поля [identifier](https://schema.org/identifier). При этом значение propertyID должно быть **mediaId** или '**Article id**'. Идентификатор должен содержать более 3х символов.

**Пример:**

&#x20;`"identifier": { "@type": "PropertyValue", "propertyID": "mediaId", // ожидается именно такое название "value": "entity_303003" // изменяемое значение }`

#### **Заголовок материала** <a href="#id-standartysemanticheskoimikrorazmetki-microdata-zagolovok-required" id="id-standartysemanticheskoimikrorazmetki-microdata-zagolovok-required"></a>

Для передачи заголовка материала необходимо настроить передачу полей [headline](https://schema.org/headline) или [alternativeHeadline](https://schema.org/alternativeHeadline).

**Пример:**

`"name":"«Желательно получить Македонию». Даже Карпин хочет эту команду в соперники по стыкам"`

**Пример:**

`"headline":"«Желательно получить Македонию». Даже Карпин хочет эту команду в соперники по стыкам""headline":"«Желательно получить Македонию». Даже Карпин хочет эту команду в соперники по стыкам"`

#### Url материала / контейнер <a href="#url-materiala-konteiner" id="url-materiala-konteiner"></a>

Для передачи url материала и контейнера можно использовать поле [url](https://schema.org/url) или [mainEntityOfPage](https://schema.org/mainEntityOfPage)​В поле url после знака # можно передать id контейнера, где размещается текст материала. В этом случае размер материала будет вычисляться более корректно. Это влияет на параметры доскола и дочтения.

**Пример:**

`"url":"https://www.championat.com/football/article-4522451-s-kem-sygraet-sbornaya-rossii-v-stykovyh-matchah-chm-2022-severnaya-makedoniya-vozmozhnyj-sopernik-komandy-karpina.html#article_id"`

**Пример:**

`"mainEntityOfPage":{` `"@type":"WebPage", "@id":"https://www.championat.com/football/article-4522451-s-kem-sygraet-sbornaya-rossii-v-stykovyh-matchah-chm-2022-severnaya-makedoniya-vozmozhnyj-sopernik-komandy-karpina.html#article_id" }`

#### Дата публикации <a href="#data-publikacii" id="data-publikacii"></a>

Для передачи даты публикации необходимо использовать поле [datePublished](https://schema.org/datePublished). Разметка передается в формате [ISO 8601](https://www.iso.org/standard/40874.html).

**Пример:**

`"datePublished":"2021-11-24T14:00:06+03:00"`

#### Дата модификации <a href="#data-modifikacii" id="data-modifikacii"></a>

Поля [datePublished](https://schema.org/datePublished) (обязательное) и дата изменения [dateModified](https://schema.org/dateModified) (опциональное). Разметка поддерживает формат [ISO 8601](https://www.iso.org/standard/40874.html).

**Пример:**

`"dateModified":"2021-11-24T14:00:07+03:00"`

#### Рубрика <a href="#rubrika" id="rubrika"></a>

Для передачи данных по рубрикам можно использовать [breadcrumbList](https://schema.org/BreadcrumbList) или [articleSection](https://schema.org/articleSection). Рубрики отражают иерархическую структуру сайта. Рубрика может быть узкой и находиться внутри широкой темы. Определите несколько сущностей типа [ListItem](https://schema.org/ListItem) внутри класса, задайте им свойства [itemListElement](https://schema.org/itemListElement), которые описывают текущую и более широкие рубрики. Рубрикой данного материала будет считаться значение сущности с наибольшим position.

**Пример:**

`"articleSection":"Футбол"`

**Пример:**

`<script` `type="application/ld+json"> { "@context": "https://schema.org", "@type": "BreadcrumbList", "itemListElement": [ { "@type": "ListItem", "position": 1, "item": { "@id": "https://site.ru/fashion", "name": "Мода" } }, { "@type": "ListItem", "position": 2, "item": { "@id": "https://site.ru/fashion/boho", "name": "Стиль бохо" } }, { "@type": "ListItem", "position": 3, "item": { "@id": "https://site.ru/fashion/boho/woven-bags", "name": "Плетеные сумки" } } ]} </script>`

#### Автор <a href="#avtor" id="avtor"></a>

Для передачи автора можно воспользоваться полями [author](https://schema.org/author) или [person](https://schema.org/Person). Если их несколько, укажите каждого в отдельном теге.

**Пример:**

`"author":{ "@type":"Person", "name":"Павел Прохоров", "url":"`[`https://www.championat.com/authors/3889/1.html`](https://www.championat.com/authors/3889/1.html)`" }`

#### Аннотация материала (вводный абзац) <a href="#annotaciya-materiala-vvodnyi-abzac" id="annotaciya-materiala-vvodnyi-abzac"></a>

Для передачи аннотации материала используется поле [abstract](https://schema.org/abstract).

**Пример:**

`"description": "Летнее межсезонье в Российской Премьер-Лиге получилось мимолётным, многие команды уже вышли из отпуска и начали подготовку к новому розыгрышу. Футболисты попытались воспользоваться этой паузой максимально продуктивно."`

#### Текст <a href="#tekst" id="tekst"></a>

Для передачи текста материала используется поле [articleBody](https://schema.org/articleBody). Текст статьи, должен содержать более 500 знаком и быть в единственном экземпляре на странице.

**Пример:**

`<p` `itemprop="articleBody">Летнее межсезонье в Российской Премьер-Лиге получилось мимолётным, многие команды уже вышли из отпуска и начали подготовку к новому розыгрышу. Футболисты попытались воспользоваться этой паузой максимально продуктивно.</p>`

#### Изображение <a href="#izobrazhenie" id="izobrazhenie"></a>

Для передачи изображений можно использовать поле [ImageObject](https://schema.org/ImageObject) Важно не само описание изображений, а количество элементов в массиве image.

**Пример:**

`"image":[{ "@type":"ImageObject", "representativeOfPage":"true", "url":"https://img.championat.com/c/1350x759/news/big/x/o/makedoniya-vozmozhnyj-sopernik-rossii-obzor_16376953941446019056.jpg", "width":1350, "height":759 }]`
