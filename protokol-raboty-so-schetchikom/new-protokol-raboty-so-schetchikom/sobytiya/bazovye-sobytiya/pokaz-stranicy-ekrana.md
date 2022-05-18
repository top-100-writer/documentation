# Показ страницы / экрана

Событие показа страницы передается со значением **event\_name=page\_view**. Дополнительную информацию можно пережать в формате JSON в параметре meta. Возможное поля:

| **Параметр**     | **Формат**    | **Описание**                                                                                                                                                                                                  |
| ---------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| referer          | URL           | <p>Аналог referer в web. Следует передавать координаты предыдущего скрина/события в формате аналогичном url: app://{app_name}/{screen}/{action}<br><strong>Пример: app://rambler_mail/login/load</strong></p> |
| browser\_screen  | NumberхNumber | <p>Размеры страницы. <br><strong>Пример: 123x123</strong></p>                                                                                                                                                 |
| page\_title      | String        | <p>Заголовок страницы. Ограничение: не более 250 символов<br><strong>Пример: Lenta.ru - Новости России и мира сегодня</strong></p>                                                                            |
| screen\_size     | NumberхNumber | <p>Разрешение экрана.<br><strong>Пример: 123х123</strong></p>                                                                                                                                                 |
| color\_depth     | Number-bit    | <p>Глубина цвета<br><strong>Пример: 24-bit</strong></p>                                                                                                                                                       |
| language         | String        | <p>Язык браузера<br><strong>Пример: ru-RU</strong></p>                                                                                                                                                        |
| browser          | String        | <p>Имя браузера<br><strong>Пример: Mozilla</strong></p>                                                                                                                                                       |
| browser\_version | String        | Версия браузера                                                                                                                                                                                               |
| platforma        | String        | <p>Тип устройства (mobile, desktop, smarttv, etc)<br><strong>Пример: desktop</strong></p>                                                                                                                     |
| timezone         | Number        | <p>Таймзона (число минут)<br>П<strong>ример: -180</strong></p>                                                                                                                                                |
| hash             | String        | Хэш из адресной строки. Подробнее про передачу параметра – см. «[Учет хешей](../../../../razmetka-celevykh-deistvii/uchet-kheshei.md)».                                                                       |
| screen\_id       | String        | Дополнительный идентификатор для точного определения экрана                                                                                                                                                   |
| сonnection       | String        | Тип подключения к сети Интернет (wifi/mobile)                                                                                                                                                                 |
| app\_name        | String        | Название приложения                                                                                                                                                                                           |
| app\_verion      | String        | Версия приложения                                                                                                                                                                                             |

**Пример:**

