# Интеграция для RamblerCo

Добавьте в корневой `build.gradle` следующий репозиторий:

```
allprojects {
    repositories {
        ...
        maven { url 'https://art.rambler.ru/ui/native/rds-android/' }
    }
}
```

Добавьте в `build.gradle` вашего модуля следующую зависимость:

```
implementation 'ru.top100.tracker:tracker-top100-sdk:0.0.16'
```
