# Ручная отправка события контакта с медиа

Информацию о взаимодействии с медиа контентом можно передать через вызов метода счетчика, при этом передать необходимые параметры.

**Пример:**

`window.top100Counter.trackPageViewMedia({`\
&#x20;   `title: 'Стиль бохо входит в моду летом 2019',`\
&#x20;   `type: 'Article',`\
&#x20;   `itemId: 'entity_78686',`\
&#x20;   `url: 'rambler.ru',`\
&#x20;   `datePublished: '2021-09-03T12:00:08+03:00',`\
&#x20;   `dateModified: '2021-09-04T12:00:08+03:00',`\
&#x20;   `description: 'description Media',`\
&#x20;   `author: {`\
&#x20;       `name: 'author Name Media',`\
&#x20;       `id: 'author Id Media',`\
&#x20;       `url: 'author Url Media'`\
&#x20;   `},`\
&#x20;   `themes: 'test meta',`\
&#x20;   `category: 'category',`\
&#x20;   `articleContainer: document.getElementById('article_container')`\
`});`
