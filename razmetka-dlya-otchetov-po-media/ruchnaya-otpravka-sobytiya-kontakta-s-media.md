# Ручная отправка события контакта с медиа

Информацию о взаимодействии с медиа контентом можно передать через вызов метода счетчика, при этом передать необходимые параметры.

**Пример:**

`window.top100Counter.trackPageViewMedia({`\
&#x20;   `title: 'Стиль бохо входит в моду летом 2019',`\
&#x20;   `type: 'Article',`\
&#x20;   `itemId: 'entity_78686',`\
&#x20;   `url: 'https://www.championat.com/football/article-4522451-s-kem-sygraet-sbornaya-rossii-v-stykovyh-matchah-chm-2022-severnaya-makedoniya-vozmozhnyj-sopernik-komandy-karpina.html#article_id',`\
&#x20;   `datePublished: '2021-09-03T12:00:08+03:00',`\
&#x20;   `dateModified: '2021-09-04T12:00:08+03:00',`\
&#x20;   `description: 'Летнее межсезонье в Российской Премьер-Лиге получилось мимолётным, многие команды уже вышли из отпуска и начали подготовку к новому розыгрышу. Футболисты попытались воспользоваться этой паузой максимально продуктивно.',`\
&#x20;   `author: {`\
&#x20;       `name: 'Павел Прохоров',`\
&#x20;       `id: 'author Id Media',`\
&#x20;       `url: 'https://www.championat.com/authors/3889/1.html'`\
&#x20;   `},`\
&#x20;   `themes: 'football, boho',`\
&#x20;   `category: 'fashion',`\
&#x20;   `articleContainer: document.getElementById('article_container')`\
`});`
