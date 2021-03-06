# Передача параметров визита

Можно расширить состав собираемой статистики по визитам пользователей, добавив ряд дополнительных параметров.

Для этого в код страницы необходимо добавить вызов метода [`sendCustomVars`](../donastroika-schetchika/metody-po-rabote-so-schetchikom.md) для созданного экземпляра счетчика и передать параметром объект с данными, которые надо отправить в счетчик. Это следует проделать со всеми страницами сайта, для которых необходимо отслеживать соответствующие события.

Накопленная статистика будет доступна для просмотра в отчёте «Параметры визитов».

**Пример отправки данных о шагах реализуемого сценария:**

`window.top100Counter.sendCustomVars({'<partner>::<product>::<utm_campaing>::<step_id>': 1})`

В примере выше необходимо заменить переменные `<partner>`, `<product>`, `<utm_campaing>`, `<step_id>` на нужные вам.

**Пример фрагмента сценария:**

Шаг 1: Выбор услуги

\-> Никаких действий не нужно.

Шаг 2: Оформление услуги

\-> После загрузки формы необходимо вызвать функцию счётчика:

`window.top100Counter.sendCustomVars({'ivan_and_partners::service::summercampaign::step_1': 1})`

Шаг 3: Ознакомление с формой электронного сертификата на получение услуги

\-> После загрузки формы необходимо вызвать функцию счётчика

`window.top100Counter.sendCustomVars({'ivan_and_partners::service::summercampaign::step_2': 1})`

> _**Примечание:** Состав отслеживаемых шагов может быть различным в зависимости от специфики реализуемых на сайте пользовательских сценариев._
