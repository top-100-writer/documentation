# Метод для обновления параметров счетчика

Метод для обновления параметров счетчика. Обновляет ограниченное кол-во параметров конкретного счетчика. Список параметров счетчика указан в разделе [Параметры счетчика](../parametry-schyotchika-top-100.md). Также с помощью метода можно установить email пользователя.

```
top100Counter.updateOptions(COUNTER_PARAMS);
```

**COUNTER\_PARAMS** - объект с параметрами которые необходимо обновить. Список параметров счетчика указан в разделе [Параметры счетчика](../parametry-schyotchika-top-100.md).

#### Примеры использования метода:

{% code overflow="wrap" %}
```
window.top100Counter.updateOptions({ pub_id: 'abcde1234'); // id пользователя от площадки
window.top100Counter.updateOptions({ email: 'test@mail.com' }); // email пользователя
```
{% endcode %}
