# Базовые параметры запроса

Для каждого запроса необходимо передавать следующие базовые параметры:\
\* - обязательный к передаче\


<table><thead><tr><th width="238">Параметр</th><th width="160.4402985074627">Формат</th><th>Описание</th></tr></thead><tbody><tr><td>event_type *</td><td>String</td><td>Тип события, по факту которого осуществляется отправка запроса в Топ-100. Указывается одно из <a href="../../model-dannykh/tipy-sobytii.md">возможных значений</a><br><strong>Пример:</strong> <code>base</code></td></tr><tr><td>event_name *</td><td>String</td><td>Название события, по факту которого осуществляется отправка запроса в Топ-100. <br><strong>Пример:</strong> <code>page_view</code></td></tr><tr><td>project_id *</td><td>Number</td><td>Идентификатор счетчика, сгенерированный в Топ-100 при регистрации счетчика. <br><strong>Пример:</strong> <code>29811</code></td></tr><tr><td>request_id *</td><td>Number.Number-Number</td><td>Идентификатор для группировки событий, произошедших в рамках одного показа страницы. Позволяет корректно учитывать в статистике аудиторные показатели. События с одинаковым rid считаются случившимися в рамках одного и того же показа страницы. Идентификатор следует сгенерировать один раз при загрузке страницы. Можно это сделать следующим образом: (+new Date / 1000).toString() + '-' + Math.round(2147483647*Math.random()).toString(). Или генерировать его по собственному алгоритму, но так, чтобы сгенерированное значение соответствовало шаблону (&#x3C;float>-&#x3C;int>): &#x3C;timestamp_with_msecs> + '-' + &#x3C;some_random_value>, где &#x3C;timestamp_with_msecs> - с миллисекундами. <br><strong>Пример:</strong> <code>1461774198.139-396177806</code></td></tr><tr><td>event_id *</td><td>String</td><td><p>Параметр уникальности каждого события</p><p>Лимит на размер строки: 36 символов<br><strong>Пример:</strong> <code>6210531992879190</code></p></td></tr><tr><td>split</td><td>Array&#x3C;String></td><td>Набор пользовательских <a href="../veb-schyotchik/splitovanie.md">сплитов</a><br><strong>Пример:</strong> <code>["split_1","split_2","split_3"]</code></td></tr><tr><td>top100_id</td><td>String</td><td>First-party идентификатор пользователя. Допустимо передавать любое строковое значение которое будет одинаковым для одной установки приложения на устройство пользователя и разным для разных установок приложения. Лимит на размер строки: 100 символов<br><strong>Пример:</strong> <code>f8eb35f2-94b0-4f19-affa-9d8b9c878270</code></td></tr><tr><td>ruid</td><td>String</td><td>Third-party идентификатор пользователя.<br><strong>Пример:</strong> <code>f8eb35f2-94b0-4f19-affa-9d8b9c878270</code></td></tr><tr><td>rambler_id</td><td>String</td><td>Идентификатор авторизованного пользователя в системе Rambler_id</td></tr><tr><td>adtech_uid</td><td>String</td><td>First-party идентификатор пользователя. Лимит на размер строки: 36 символов<br><strong>Пример:</strong> <code>f8eb35f2-94b0-4f19-affa-9d8b9c878270</code></td></tr><tr><td>adtech_uid_scope</td><td>String</td><td>Domain / bundle_id, граница применимости идентификатора<br><strong>Пример:</strong> <code>app_lenta</code></td></tr><tr><td>auth_uid</td><td>String</td><td>Идентификатор авторизованного пользователя. Передается в запросе, если известен. Лимит на размер строки: 36 символов<br><strong>Пример:</strong> <code>f67c2bcbfcfa30f</code></td></tr><tr><td>publisher_uid</td><td>String</td><td>First-party идентификатор пользователя приложением. Допустимо передавать любое строковое значение которое будет одинаковым для одной установки приложения на устройство пользователя и разным для разных установок приложения. Лимит на размер строки: 36 символов<br><strong>Пример:</strong> <code>f8eb35f2-94b0-4f19-affa-9d8b9c878270</code></td></tr><tr><td>publisher_uid_scope</td><td>String</td><td>Domain / bundle_id, граница применимости идентификатора<br><strong>Пример:</strong> <code>app_rambler</code></td></tr><tr><td>sber_id</td><td>String</td><td>Сквозной идентификатор Сбера, верный для всех партнеров</td></tr><tr><td>sber_id_sub</td><td>String</td><td>Идентификатор Сбера, верный для одного партнера</td></tr><tr><td>email_hash</td><td>String</td><td>Хэш sha256 от email пользователя<br><strong>Пример:</strong> <code>7af224cee0ac7ddb0da574fbb3dc2890e33b4d1e99a335394858f3221b548a7a</code></td></tr><tr><td>phone_hash</td><td>String</td><td>Хэш sha256 от телефона пользователя, формат 999-999-99-99<br><strong>Пример:</strong> <code>76ab9e619bb699897571f6860f44144b07d6560a1fbab09dc88e5f14e1098f48</code></td></tr><tr><td>gaid</td><td>String</td><td>Рекламный идентификатор в android</td></tr><tr><td>idfa</td><td>String</td><td>Рекламный идентификатор в ios</td></tr><tr><td>oaid</td><td>String</td><td>Рекламный идентификатор huawei</td></tr><tr><td>sberdevice_id</td><td>String</td><td>Идентификатор устройства от sberdevice</td></tr><tr><td>profile</td><td>Json</td><td>Любые данные о пользователи, которые может передать площадка</td></tr><tr><td>fingerprint</td><td>Json</td><td><p>Фингерпринт</p><p><strong>Пример:</strong> <code>{fingerprint: pA8AAENKs1d4BLyuAdJxQQA=}</code></p></td></tr><tr><td>rambler_id</td><td>String</td><td>Идентификатор пользователя в Рамблере<br></td></tr><tr><td>model</td><td>String</td><td>Модель устройства <br><strong>Пример:</strong> <code>iPhone 5s</code> или <code>SM-J500M</code></td></tr><tr><td>device</td><td>String</td><td>Название устройства по классификации производителя (hwm)</td></tr><tr><td>os</td><td>String</td><td>Операционная система устройства</td></tr><tr><td>os_version</td><td>String</td><td>Версия OS<br><strong>Пример:</strong> <code>10.34</code></td></tr><tr><td>idfv</td><td>String</td><td>Идентификатор пользователя в ios, верный в рамках скоупа приложений одного издателя</td></tr><tr><td>android_id</td><td>String</td><td>Аналог idfv в android</td></tr><tr><td>session_id *</td><td>String</td><td>Идентификатор сессии<br><strong>Пример:</strong> <code>1703949555_1650546049152</code></td></tr><tr><td>session_number *</td><td>Number</td><td>Порядковый номер сессии<br><strong>Пример:</strong> <code>1</code></td></tr><tr><td>session_event_number *</td><td>Number</td><td>Порядковый номер события в сессии<br><strong>Пример:</strong> <code>1</code></td></tr><tr><td>url *</td><td>URL</td><td>URL адрес страницы, на которой произошло событие. В общем случае параметр запроса url необязателен. Но если он не передается, то адрес страницы должен обязательно передаваться в запросе в заголовке HTTP referer.<br><strong>Пример:</strong> <code>https://rambler.ru/main_page</code></td></tr><tr><td>screen_name</td><td>String</td><td>Название экрана, класса приложения<br><strong>Пример:</strong> <code>mainActivity</code></td></tr><tr><td>counter_type *</td><td>String</td><td>Технический параметр. Передаем тип потока данных.<br><strong>Пример:</strong> <code>app</code></td></tr><tr><td>version</td><td>N.N.N</td><td>Версия счётчика. Если параметр не передан, то по умолчанию используется последняя версия счетчика.<br><strong>Пример:</strong> <code>0.0.1</code></td></tr><tr><td>random</td><td>Number</td><td>Случайное число<br><strong>Пример:</strong> <code>12323423432</code></td></tr></tbody></table>