# Методы по работе с счётчиком Топ-100

{% hint style="info" %}
**ВНИМАНИЕ!** Перед вызовом методов следует убедиться, что экземпляр счётчика создан и доступен. Данные не будут собираться, если счётчик ещё не создан, т.к. их не с чем связать.
{% endhint %}

Поддерживаются следующие методы по работе со счетчиком:

<table><thead><tr><th width="514">Метод</th><th>Описание</th></tr></thead><tbody><tr><td><pre><code>top100Counter.trackPageView("URL");
</code></pre></td><td><a href="otpravka-sobytiya-o-prosmotre-stranicy.md">Отправка события о просмотре страницы</a></td></tr><tr><td><pre><code>top100Counter.trackEvent("EVENT_NAME", EVENT_DATA);
</code></pre></td><td><a href="otpravka-sobstvennykh-sobytii.md">Метод trackEvent [ New ]</a></td></tr><tr><td><pre><code>top100Counter.syncUserId("USER_ID" || null);
</code></pre></td><td><a href="metod-dlya-peredachi-identifikatora-avtorizovannogo-polzovatelya.md">Метод для передачи идентификатора авторизованного пользователя</a></td></tr><tr><td><pre><code><strong>top100Counter.getPublisherId();
</strong></code></pre></td><td><a href="metod-dlya-polucheniya-dannykh-ob-identifikatore-polzovatelya-ustanavlivaemogo-ploshadkoi.md">Метод для получения данных об идентификаторе пользователя, устанавливаемого площадкой</a></td></tr><tr><td><pre><code>top100Counter.drawLogoTo("ELEMENT_ID");
</code></pre></td><td><a href="metod-dlya-otrisovki-vidzheta-na-stranice.md">Метод для отрисовки виджета на странице</a></td></tr><tr><td><pre><code>top100Counter.sendBlocks();
</code></pre></td><td><a href="metod-dlya-skanirovaniya-i-otpravki-blokov.md">Метод для сканирования и отправки блоков</a></td></tr><tr><td><pre><code>top100Counter.updateOptions(COUNTER_PARAMS)
</code></pre></td><td><a href="metod-dlya-obnovleniya-parametrov-schetchika.md">Метод для обновления параметров счётчика</a></td></tr></tbody></table>
