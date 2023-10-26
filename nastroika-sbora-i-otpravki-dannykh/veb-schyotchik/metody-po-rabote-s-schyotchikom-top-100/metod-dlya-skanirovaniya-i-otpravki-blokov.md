# Метод для сканирования и отправки блоков

Метод для дополнительного поиска элементов, указанных в «[Аналитике блоков](../podklyuchenie-i-nastroika-analitiki-blokov/rekomendacii-po-nastroike-i-ispolzovaniyu.md)» и последующей отправке по ним данных. В метод можно передать DOM элемент – контейнер в рамках которого нужно осуществить поиск показанных блоков.

```
top100Counter.sendBlocks();
```

#### Примеры вызова метода:

```
window.top100Counter.sendBlocks();
```

```
const container = document.getElementById('container_id'); 
window.top100Counter.sendBlocks(container);
```
