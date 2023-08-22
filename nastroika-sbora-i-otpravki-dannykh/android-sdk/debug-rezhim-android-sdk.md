# Debug режим (Android SDK)

Debug режим позволяет проверить корректность работы счетчика и его параметры. По умолчанию debug режим выключен. Для того чтобы его активировать, необходимо поменять переменную flag в функции `.debug` с **"false"** на **"true"**.

<figure><img src="../../.gitbook/assets/дебаг android 1.1.png" alt=""><figcaption><p>Параметр debug выключен</p></figcaption></figure>

После чего в консоль будет выводиться логирование событий, где будет информация о названии счетчика, его параметрах и действиях.&#x20;

<figure><img src="../../.gitbook/assets/дебаг android 2.png" alt=""><figcaption><p>Активированный debug режим</p></figcaption></figure>

Для выключения debug режима поменяйте переменную flag в функции `.debug` с **"true" на** **"false".**
