# Модель данных

Модель данных Рамблер/топ-100 основана на событиях — это ключевая особенность счетчика. Вся аналитика строится не вокруг визитов и просмотр страниц, а вокруг событий: любое взаимодействие  с сайтом или приложением будет регистрироваться как событие. Такой подход первую очередь удобен тем, кто владеет не только веб-сайтом, но и мобильным приложением, а также различными умными устройствами.&#x20;

В модели данных Рамблер/топ-100 следующая система подсчета событий:

* Модель данных основывается на событиях и собирает кроссплатформенные данные.
* Гибкие кастомные события – в них можно передать до 30 разных параметров до 6 уровней вложенности.&#x20;

Обратите внимание, что в модели ведется более точный подсчет посетителей сайта:

* Если один и тот же пользователь приходит из другого источника трафика, то это не считается новым визитом.
* Также не считается новым визитом, если пользователь остается на сайте после 00:00. Однако такой визит будет учитываться в обоих днях.

В результате общее количество визитов может быть меньше, чем в предыдущей модели, но это будут более корректные данные.

Для передачи данных используются события, которые делятся на типы по применимости в отчетах. Все данные события должны быть переданы в параметре meta.
