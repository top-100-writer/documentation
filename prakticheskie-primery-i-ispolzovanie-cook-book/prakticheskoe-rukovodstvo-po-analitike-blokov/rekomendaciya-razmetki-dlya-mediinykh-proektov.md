# Рекомендация разметки для медийных проектов

### Общая схема разметки

data-\[проект]\[-\[desktop|mobile]]=\[группа компонентов]::\[компонент]::\[порядковый номер компонента]::\[группа элементов]:: \[элемент]::\[порядковый номер элемента]::\[состояние]&#x20;

* проект – символьный код проекта из списка&#x20;
* <mark style="color:green;">desktop или mobile</mark> – обозначение платформы&#x20;
* <mark style="color:green;">группа компонентов</mark> – группа, состоящая из отдельных, повторяющихся компонентов, например группа виджетов&#x20;
* компонент м название компонента, например карточка кластера или виджет&#x20;
* <mark style="color:green;">порядковый номер компонента</mark> – если компонент повторяются в рамках одной группы&#x20;
* <mark style="color:green;">группа элементов</mark> – общее название для элементов, если они обобщены, например элементы списка в саджесте поиска&#x20;
* <mark style="color:green;">элемент</mark> – название отдельного простого элемента&#x20;
* <mark style="color:green;">порядковый номер элемента</mark> – если элемент находится в списке&#x20;
* <mark style="color:green;">состояние</mark> – назначается, если элемент принимает разные состояния, например: opened и closed

{% hint style="info" %}
Обратите внимание! Зеленым шрифтом указаны необязательные уровни&#x20;
{% endhint %}

### Описание разметки&#x20;

**Первый уровень** – обязательный и устанавливается проектом.&#x20;

**Второй уровень** указывается, если состоит из обобщенных одним смыслом компонентов. Таким образом он автоматически добавит уровень к дереву аналитики. Указывается как один уровень, т.е. без разделителя "::"

```
<div data-head-desktop="group">
 ...
</div>
```

**Третий и последующие уровни** назначаются для каждого компонента, группы элементов и элемента в отдельности....

<pre><code><strong>&#x3C;div data-head-desktop="component::1">
</strong> &#x3C;div data-head-desktop="items">
  &#x3C;span data-head-desktop="item::1::checked">
   ...
<strong>  &#x3C;/span>
</strong><strong> &#x3C;/div>
</strong>&#x3C;/div>

</code></pre>