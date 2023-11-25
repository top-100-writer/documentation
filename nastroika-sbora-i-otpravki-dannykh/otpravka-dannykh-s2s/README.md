# Отправка данных S2S

Данные о событиях в приложении можно отправлять напрямую на серверы Топ-100 посредством HTTPS-запросов вида:

* `https://kraken.rambler.ru/cnt/v2/?<params>`

В качестве `<params>` следует передавать строку с интересующими параметрами:

* Каждый параметр передается как `<param_name>=<param_value>`, где`<param_name>` – имя передаваемого параметра, `<param_value>` – его значение. Причем для значения `<param_value>` предварительно должен быть применен `encodeURIComponent (param_value = encodeURIComponent(param_value))`. Затем все параметры конкатенируются с '&'.

Итоговый вид запроса будет следующий:

`https://kraken.rambler.ru/cnt/v2/?<param_name1>=<param_value1>&<param_name2>=<param_value2>&...`

Передаваемые в запросе параметры можно условно разделить на базовые параметры, которые отправляются на каждый запрос, и параметры, специфичные для каждого отслеживаемого типа событий. Если нет данных для какого-то параметра, то он опускается в запросе.

Читайте в этом разделе:

* [Заголовки запроса](https://top-100-writer.gitbook.io/dokumentaciya-top-100-po-novoi-modeli-progress/nastroika-sbora-i-otpravki-dannykh/otpravka-dannykh-s2s/zagolovki-zaprosa)
* [Базовые параметры запроса](https://top-100-writer.gitbook.io/dokumentaciya-top-100-po-novoi-modeli-progress/nastroika-sbora-i-otpravki-dannykh/otpravka-dannykh-s2s/bazovye-parametry-zaprosa)
* [Параметры событий](https://top-100-writer.gitbook.io/dokumentaciya-top-100-po-novoi-modeli-progress/nastroika-sbora-i-otpravki-dannykh/otpravka-dannykh-s2s/parametry-sobytii)
