# Debug режим счётчика (IOS SDK)

Debug режим позволяет проверить корректность работы счетчика и его параметры. По умолчанию debug режим выключен. Для того чтобы его активировать, необходимо поменять в AppDelgate в функции`TrackerTop100.setupDebugActive` **"false"** на **"true"**.

<figure><img src="../../.gitbook/assets/дебаг ios 1.png" alt=""><figcaption><p>Параметр debug включен</p></figcaption></figure>

После чего в консоль будет выводиться логирование событий, где будет информация о названии счетчика, его параметрах и действиях.&#x20;

<figure><img src="../../.gitbook/assets/дебаг ios 2.png" alt=""><figcaption><p>Активированный debug режим</p></figcaption></figure>

Для выключения режима debug поменяйте в функции`TrackerTop100.setupDebugActive` **"true"** на **"false".**
