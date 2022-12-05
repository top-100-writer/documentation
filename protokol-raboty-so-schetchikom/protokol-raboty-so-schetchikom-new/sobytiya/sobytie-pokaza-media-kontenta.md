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

https://kraken.rambler.ru/cnt/v2/?et=pvm\&v=3.12.12\&pid=4422985\&tid=t1.-1.1938537918.1643966398357\&rid=1670228383.771-1293337191\&fid=pA8AAENKs1fTzF29Ab8DNQA%3D\&fip=pA8AAENKs1fnZVqRATvpYAA%3D\&eid=255983840736098\&aduid=6a0ff610-8f49-4896-9c25-ed9643715b94\&aduidsc=rambler.ru\&stid=115197320\_1670228368305\&sn=10\&sen=5\&rf=https%3A%2F%2Fwww.rambler.ru%2F\&ct=web\&url=https%3A%2F%2Fnews.rambler.ru%2Fincidents%2F49813016-smi-chechenskiy-bloger-tumso-abdurahmanov-ubit-v-shvetsii%2F\&exp=%5B%5B%22exp\_bot%22%2C%22split\_a%22%5D%2C%5B%22exp\_ping%22%2C%22no%22%5D%5D\&mp=%7B%22sch%22%3A%22ld%22%2C%22title%22%3A%22%D0%A1%D0%9C%D0%98%3A%20%D1%87%D0%B5%D1%87%D0%B5%D0%BD%D1%81%D0%BA%D0%B8%D0%B9%20%D0%B1%D0%BB%D0%BE%D0%B3%D0%B5%D1%80%20%D0%A2%D1%83%D0%BC%D1%81%D0%BE%20%D0%90%D0%B1%D0%B4%D1%83%D1%80%D0%B0%D1%85%D0%BC%D0%B0%D0%BD%D0%BE%D0%B2%20%D1%83%D0%B1%D0%B8%D1%82%20%D0%B2%20%D0%A8%D0%B2%D0%B5%D1%86%D0%B8%D0%B8%22%2C%22des%22%3A%22%D0%A7%D0%B5%D1%87%D0%B5%D0%BD%D1%81%D0%BA%D0%B8%D0%B9%20%D0%BE%D0%BF%D0%BF%D0%BE%D0%B7%D0%B8%D1%86%D0%B8%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9%20%D0%B1%D0%BB%D0%BE%D0%B3%D0%B5%D1%80%20%D0%A2%D1%83%D0%BC%D1%81%D0%BE%20%D0%90%D0%B1%D0%B4%D1%83%D1%80%D0%B0%D1%85%D0%BC%D0%B0%D0%BD%D0%BE%D0%B2%20%D0%B1%D1%8B%D0%BB%20%D1%83%D0%B1%D0%B8%D1%82%2C%20%D1%81%D0%BE%D0%BE%D0%B1%D1%89%D0%B0%D0%B5%D1%82%20Telegram-%D0%BA%D0%B0%D0%BD%D0%B0%D0%BB%20%C2%AB%D0%A0%D0%B0%D0%B4%D0%B8%D0%BE%20%D0%A1%D0%B2%D0%BE%D0%B1%D0%BE%D0%B4%D0%B0%C2%BB%20(%D0%BE%D1%80%D0%B3%D0%B0%D0%BD%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F%20%D0%B2%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B0%20%D0%9C%D0%B8%D0%BD%D1%8E%D1%81%D1%82%D0%BE%D0%BC%20%D0%B2%20%D1%81%D0%BF%D0%B8%D1%81%D0%BE%D0%BA%20%D0%B8%D0%BD%D0%BE%D0%B0%D0%B3%D0%B5%D0%BD%D1%82%D0%BE%D0%B2)%2C%20%D1%81%D1%81%D1%8B%D0%BB%D0%B0%D1%8F%D1%81%D1%8C%20%D0%BD%D0%B0%20%D0%B5%D0%B3%D0%BE%20%D1%81%D0%BE%D1%80%D0%B0%D1%82%D0%BD%D0%B8%D0%BA%D0%BE%D0%B2%20%D0%A3%D1%82%D0%BE%D1%87%D0%BD%D1%8F%D0%B5%D1%82%D1%81%D1%8F%2C%20%D1%87%D1%82%D0%BE%20%D0%B1%D0%BB%D0%BE%D0%B3%D0%B5%D1%80%20%D0%B1%D1%8B%D0%BB%20%D0%B7%D0%B0%D1%81%D1%82%D1%80%D0%B5%D0%BB%D1%8F%D0%BD%20%D0%B2%20%D0%A8%D0%B2%D0%B5%D1%86%D0%B8%D0%B8%2C%20%D0%B3%D0%B4%D0%B5%20%D0%B2...%22%2C%22url%22%3A%22https%3A%2F%2Fnews.rambler.ru%2Fincidents%2F49813016-smi-chechenskiy-bloger-tumso-abdurahmanov-ubit-v-shvetsii%2F%22%2C%22type%22%3A%22NewsArticle%22%2C%22mid%22%3A%2249813016%22%2C%22thm%22%3A%22%D0%9F%D1%80%D0%BE%D0%B8%D1%81%D1%88%D0%B5%D1%81%D1%82%D0%B2%D0%B8%D1%8F%22%2C%22dpub%22%3A%222022-12-05T10%3A48%3A58%2B03%3A00%22%2C%22dmod%22%3A%222022-12-05T11%3A14%3A16%2B03%3A00%22%2C%22arth%22%3A1380%2C%22artst%22%3A150%2C%22arts%22%3A1102%2C%22artw%22%3A122%2C%22img%22%3A3%2C%22anm%22%3A%22%D0%93%D0%B0%D0%B7%D0%B5%D1%82%D0%B0.Ru%22%7D
