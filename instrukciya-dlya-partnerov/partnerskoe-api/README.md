# Партнерское API

Для того, чтобы начать использовать партнерские API получите от вашего менеджера в Рамблере специальный авторизационный ключ (токен), привязанный к вашему Рамблер ID пользователю.

Полученный ключ необходимо передавать вместе с каждым вызовом API в заголовке `Authorization` ([RFC-7235](https://tools.ietf.org/html/rfc7235)) с типом `Key`.

**Пример**

```
POST /api/partner/v2.0/projects HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: Key <token>
Connection: keep-alive
Content-Length: 0
Host: localhost:8081
User-Agent: HTTPie/0.9.9
```

* [API каталога](api-kataloga/)
* [API управления счетчиками](api-kataloga/)
