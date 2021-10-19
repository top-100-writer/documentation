# Примеры передачи eCommerce-данных

Во всех примерах ниже предполагается, что счётчик инициализирован с подключением eCommerce, а передача данных производится через контейнер `window.dataLayer`.

**Показ товара (impressions):**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        impressions: [{
            id: 25315,
            name: 'Футболка с рисунком',
            list : 'Результаты поиска',
            brand: 'Печки-лавочки',
            category: 'Одежда/Мужская одежда/Футболки',
            variant: 'Серый цвет'
            position: 2,
            price: 2345.50
        },
        {
            id: 25317,
            name: 'Майка',
            list : 'Результаты поиска',
            brand: 'Печки-лавочки',
            category: 'Одежда/Мужская одежда/Футболки',
            variant: 'Зеленый цвет'
            position: 1,
            price: 1499.00
        }]
    }
});
```

**Клик по рекламе:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        promoClick: {
            promotions: [{
                id: 'P15432',
                name : 'Бейсболка',
                creative: 503.60,
                position: 'Печки-лавочки'
            }]
        }
    }
});
```

**Клик по товару:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        click: {
            products: [{
                id: 'P15432',
                name : 'Бейсболка',
                price: 503.60,
                brand: 'Печки-лавочки',
                category: 'Мужчины/Аксессуары/Бейсболки',
                variant : 'Синий цвет'
            }]
        }
    }
});
```

**Просмотр полного описания товара:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        detail: {
            products: [{
                id: 'P15432',
                name : 'Бейсболка',
                price: 503.60,
                brand: 'Печки-лавочки',
                category: 'Мужчины/Аксессуары/Бейсболки',
                variant : 'Синий цвет'
            }]
        }
    }
});
```

**Добавление товара в корзину:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        add: {
            products: [{
                id: 43521,
                name: 'Часы Citizen',
                price: 3654.32,
                brand: 'Печки-лавочки',
                category: 'Аксессуары/Часы',
                quantity: 5
            }]
        }
    }
});
```

**Удаление товара из корзины:**

```
dataLayer.push({dataLayer.push({
    ecommerce: {
        remove: {
            products: [{
                id: 176543,
                name: 'Часы Citizen',
                category: 'Аксессуары/Часы'
            }]
        }
    }
});
```

**Переход к оформлению покупки:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        checkout: {
            products: [{
                id: 'P15432',
                name : 'Бейсболка',
                price: 503.60,
                brand: 'Печки-лавочки',
                category: 'Мужчины/Аксессуары/Бейсболки',
                variant : 'Синий цвет'
            },
            {
                name: 'Значок',
                price: 46,
            }]
        }
    }
});
```

**Выбор пользователя на одном из этапов оформления покупки:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        checkout_option: {
            actionField : {
                step: 2,
                option : 'Самовывоз'
            }
        }
    }
});
```

**Покупка:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        purchase: {
            actionField: {
                id : 'b52314',
            },
            products: [{
                id: 74367,
                name: 'Свитшот с котиком',
                price: 2345.26,
                brand: 'Печки-лавочки',
                category: 'Одежда/Мужская одежда/Толстовки и свитшоты',
                variant: 'Жёлтый цвет'
                quantity: 2
            },
            {
                id: 25314,
                name: 'Футболка',
                price: 643.62,
                brand: 'Печки-лавочки',
                category: 'Одежда/Женская одежда/Футболки',
                variant: 'Белый цвет',
                quantity: 1
            }]
        }
    }
});
```

**Возврат товара:**

```
dataLayer.push({
    ecommerce: {
        currencyCode: 'RUB',
        refund: {
            products: [{
                id: 74367,
                name: 'Свитшот с котиком',
                price: 2345.26,
                brand: 'Печки-лавочки',
                category: 'Одежда/Мужская одежда/Толстовки и свитшоты',
                variant: 'Серый цвет'
                quantity: 2
            },
            {
                id: 25314,
                name: 'Футболка',
                price: 643.62,
                brand: 'Печки-лавочки',
                category: 'Одежда/Женская одежда/Футболки',
                variant: 'Белый цвет',
                quantity: 1
            }]
        }
    }
});
```
