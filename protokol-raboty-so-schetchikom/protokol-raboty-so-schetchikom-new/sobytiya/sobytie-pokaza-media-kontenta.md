# Событие показа медиа контента

Событие показа медиа контента передается со значением **event\_name=page\_view**, при этом **event\_type=media**. Дополнительную информацию можно пережать в формате JSON в параметре meta. Возможное поля:

| Параметр         | Формат | Описание                                         |
| ---------------- | ------ | ------------------------------------------------ |
| name             | String | Названием медиа контента                         |
| type             | String | Тип контента (article/news/blog/..)              |
| id               | String | Id контента                                      |
| url              | String | Канонический url контента (без query параметров) |
| date\_published  | String | Дата публикации                                  |
| date\_modified   | String | Дата модификации                                 |
| description      | String | Описание материала, не более 500 символов        |
| article\_height  | String | Высота контента в px                             |
| article\_start   | String | Смещение контента от начала страницы в px        |
| article\_symbols | Number | Количество символов в контенте                   |
| article\_words   | Number | Количество слов в контенте                       |
| article\_images  | Number | Количество картинок в контенте                   |
| author\_name     | String | Имя автора                                       |
| author\_id       | String | Идентификатор автора                             |
| author\_url      | String | Ссылка на страницу автора                        |
| themes           | String | Мета теги                                        |
| category         | String | Категория                                        |
| schema           | String | Тип разметки (micro/ld)                          |

**Пример:**

`https://kraken.rambler.ru/cnt/v2/?`
