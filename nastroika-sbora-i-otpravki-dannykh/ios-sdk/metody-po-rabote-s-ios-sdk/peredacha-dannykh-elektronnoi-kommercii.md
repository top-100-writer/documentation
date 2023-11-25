# Передача eCommerce-данных

Для передачи действий пользователя с eCommerce-данными необходимо собрать и передать данные в событие в определенном формате \<TrackerTop100ECommerce>:

#### Формат данных \<TrackerTop100ECommerce>

| Поле         | Тип данных                                                                                                        | Описание                                                                                                                                                                                                                                            |
| ------------ | ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| currencyCode | `String`                                                                                                          | Трехбуквенный [код валюты по ISO 4217](https://en.wikipedia.org/wiki/ISO\_4217#Active\_codes). Если передается иная валюта, будут отправлены нулевые значения вместо валюты и суммы.                                                                |
| action       | [\<TrackerTop100ECommAction>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md)      | Дополнительные данные, описывающие действие, произведённое с товаром или набором товаров. Данные передаются в виде объекта [\<TrackerTop100ECommAction>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).            |
| products     | [\[\<TrackerTop100ECommProduct>\]](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md) | Список описаний товаров, с которыми было произведено указанное действие. Описание каждого из товаров представляет собой объект вида [\<TrackerTop100ECommProduct>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).  |
| impressions  | [\[\<TrackerTop100ECommProduct>\]](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md) | Список описаний товаров, относящихся к действию impressions (показ товара или набора товаров). Данные передаются в виде объекта [\<TrackerTop100ECommProduct>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).      |
| promotions   | [\[\<TrackerTop100ECommPromo>\]](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md)   | Массив данных, описывающих связанное с рекламной акцией действие. Данные передаются в виде объекта [\<TrackerTop100ECommPromo>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).                                     |

#### Отправка события ECommerce

{% tabs %}
{% tab title="Swift" %}
```swift
TrackerTop100.trackEcomm(eventName: "EVENT_NAME", ecommParams: ECOMM_PARAMS)
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
[TrackerTop100 trackEcommWithEventName: @"EVENT_NAME" ecommParams: ECOMM_PARAMS];
```
{% endtab %}
{% endtabs %}

**EVENT\_NAME** (обязательный) — произвольное название события

**ECOMM\_PARAMS** (опциональный) — ECommerce данные о событии, соответствующие формату \<TrackerTop100ECommerce>

#### Примеры передачи ECommerce данных

Показ товара (impressions):

{% tabs %}
{% tab title="Swift" %}
```swift
import TrackerTop100SDK
// ...
let product1 = TrackerTop100ECommProduct(
    id: "25317",
    name: "Майка",
    list: "Результаты поиска",
    brand: "Печки-лавочки",
    category: "Одежда/Мужская одежда/Футболки",
    position: "1",
    price: "1499.00",
    variant: "Зеленый цвет"
)

let product2 = TrackerTop100ECommProduct(
    id: "25315",
    name: "Футболка с рисунком",
    list: "Результаты поиска",
    brand: "Печки-лавочки",
    category: "Одежда/Мужская одежда/Футболки",
    position: "2",
    price: "2345.50",
    variant: "Серый цвет"
)

let ecommParams = TrackerTop100ECommerce(
    currencyCode: "RUB",
    impressions: [product1, product2]
)
        
TrackerTop100.trackEcomm(eventName: "impressions", ecommParams: ecommParams)
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@import TrackerTop100SDK;
// ...
TrackerTop100ECommProduct *product1 = [[TrackerTop100ECommProduct alloc]
                                           initWithId: @"25317"
                                           name: @"Майка"
                                           list: @"Результаты поиска"
                                           brand: @"Печки-лавочки"
                                           category: @"Одежда/Мужская одежда/Футболки"
                                           coupon: nil
                                           position: @"1"
                                           price: @"1499.00"
                                           quantity: nil
                                           variant: @"Зеленый цвет"];
    
TrackerTop100ECommProduct *product2 = [[TrackerTop100ECommProduct alloc]
                                           initWithId: @"25315"
                                           name: @"Футболка с рисунком"
                                           list: @"Результаты поиска"
                                           brand: @"Печки-лавочки"
                                           category: @"Одежда/Мужская одежда/Футболки"
                                           coupon: nil
                                           position: @"2"
                                           price: @"2345.50"
                                           quantity: nil
                                           variant: @"Серый цвет"];
    
TrackerTop100ECommerce *ecommParams = [[TrackerTop100ECommerce alloc]
                                           initWithCurrencyCode: @"RUB"
                                           action: nil
                                           products: nil
                                           impressions: @[product1, product2]
                                           promotions: nil];
    
[TrackerTop100 trackEcommWithEventName: @"impressions" ecommParams: ecommParams];
```
{% endtab %}
{% endtabs %}

Клик по промо-акции:

{% tabs %}
{% tab title="Swift" %}
```swift
import TrackerTop100SDK
// ...
let promo = TrackerTop100ECommPromo(
    id: "P15432",
    name: "Сезонная распродажа",
    creative: "sale_banner1",
    position: "slot_2"
)
        
let ecommParams = TrackerTop100ECommerce(
    currencyCode: "RUB",
    promotions: [promo]
)
        
TrackerTop100.trackEcomm(eventName: "promoClick", ecommParams: ecommParams)
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@import TrackerTop100SDK;
// ...
TrackerTop100ECommPromo *promo = [[TrackerTop100ECommPromo alloc]
                                      initWithId: @"P15432"
                                      name: @"Сезонная распродажа"
                                      creative: @"sale_banner1"
                                      position: @"slot_2"];
    
TrackerTop100ECommerce *ecommParams = [[TrackerTop100ECommerce alloc]
                                           initWithCurrencyCode:@"RUB"
                                           action: nil
                                           products: nil
                                           impressions: nil
                                           promotions: @[promo]];
    
[TrackerTop100 trackEcommWithEventName: @"promoClick" ecommParams: ecommParams];
```
{% endtab %}
{% endtabs %}

Клик по товару:

{% tabs %}
{% tab title="Swift" %}
<pre class="language-swift"><code class="lang-swift">import TrackerTop100SDK
// ...
<strong>let product1 = TrackerTop100ECommProduct(
</strong><strong>    id: "25317",
</strong>    name: "Майка",
    list: "Результаты поиска",
    brand: "Печки-лавочки",
    category: "Одежда/Мужская одежда/Футболки",
    position: "1",
    price: "1499.00",
    variant: "Зеленый цвет"
)
        
let ecommParams = TrackerTop100ECommerce(
    currencyCode: "RUB",
    products: [product1]
)
        
TrackerTop100.trackEcomm(eventName: "click", ecommParams: ecommParams)
</code></pre>
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@import TrackerTop100SDK;
// ...
TrackerTop100ECommProduct *product1 = [[TrackerTop100ECommProduct alloc]
                                           initWithId: @"25317"
                                           name: @"Майка"
                                           list: @"Результаты поиска"
                                           brand: @"Печки-лавочки"
                                           category: @"Одежда/Мужская одежда/Футболки"
                                           coupon: nil
                                           position: @"1"
                                           price: @"1499.00"
                                           quantity: nil
                                           variant: @"Зеленый цвет"];
    
TrackerTop100ECommerce *ecommParams = [[TrackerTop100ECommerce alloc]
                                           initWithCurrencyCode:@"RUB"
                                           action: nil
                                           products: @[product1]
                                           impressions: nil
                                           promotions: nil];
    
[TrackerTop100 trackEcommWithEventName: @"click" ecommParams: ecommParams];
```
{% endtab %}
{% endtabs %}

Добавление товара в корзину:

{% tabs %}
{% tab title="Swift" %}
<pre class="language-swift"><code class="lang-swift">import TrackerTop100SDK
// ...
<strong>let product1 = TrackerTop100ECommProduct(
</strong><strong>    id: "43521",
</strong>    name: "Часы Citizen",
    brand: "Печки-лавочки",
    category: "Аксессуары/Часы",
    price: "3654.32",
    quantity: "5"
)
        
let ecommParams = TrackerTop100ECommerce(
    currencyCode: "RUB",
    products: [product1]
)
        
TrackerTop100.trackEcomm(eventName: "add", ecommParams: ecommParams)
</code></pre>
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@import TrackerTop100SDK;
// ...
TrackerTop100ECommProduct *product1 = [[TrackerTop100ECommProduct alloc]
                                           initWithId: @"43521"
                                           name: @"Часы Citizen"
                                           list: nil
                                           brand: @"Печки-лавочки"
                                           category: @"Аксессуары/Часы"
                                           coupon: nil
                                           position: nil
                                           price: @"3654.32"
                                           quantity: @"5"
                                           variant: nil];
    
TrackerTop100ECommerce *ecommParams = [[TrackerTop100ECommerce alloc]
                                           initWithCurrencyCode:@"RUB"
                                           action: nil
                                           products: @[product1]
                                           impressions: nil
                                           promotions: nil];
    
[TrackerTop100 trackEcommWithEventName: @"add" ecommParams: ecommParams];
```
{% endtab %}
{% endtabs %}

Покупка товаров:

{% tabs %}
{% tab title="Swift" %}
<pre class="language-swift"><code class="lang-swift">import TrackerTop100SDK
// ...
<strong>let action = TrackerTop100ECommAction(
</strong>    id: "b52314",
    step: "2",
    option: "Самовывоз"
)

let product1 = TrackerTop100ECommProduct(
    id: "25317",
    name: "Майка",
    brand: "Печки-лавочки",
    category: "Одежда/Мужская одежда/Футболки",
    price: "1499.00",
    variant: "Зеленый цвет"
)

let product2 = TrackerTop100ECommProduct(
    id: "25315",
    name: "Футболка с рисунком",
    brand: "Печки-лавочки",
    category: "Одежда/Мужская одежда/Футболки",
    price: "2345.50",
    variant: "Серый цвет"
)

let ecommParams = TrackerTop100ECommerce(
    currencyCode: "RUB",
    action: action,
    products: [product1, product2]
)
        
TrackerTop100.trackEcomm(eventName: "purchase", ecommParams: ecommParams)
</code></pre>
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@import TrackerTop100SDK;
// ...
TrackerTop100ECommAction *action = [[TrackerTop100ECommAction alloc]
                                        initWithId: @"b52314"
                                        coupon: nil
                                        revenue: nil
                                        affilation: nil
                                        tax: nil
                                        shipping: nil
                                        list: nil
                                        step: @"2"
                                        option: @"Самовывоз"];
    
TrackerTop100ECommProduct *product1 = [[TrackerTop100ECommProduct alloc]
                                           initWithId: @"25317"
                                           name: @"Майка"
                                           list: @"Результаты поиска"
                                           brand: @"Печки-лавочки"
                                           category: @"Одежда/Мужская одежда/Футболки"
                                           coupon: nil
                                           position: @"1"
                                           price: @"1499.00"
                                           quantity: nil
                                           variant: @"Зеленый цвет"];
    
TrackerTop100ECommProduct *product2 = [[TrackerTop100ECommProduct alloc]
                                           initWithId: @"25315"
                                           name: @"Футболка с рисунком"
                                           list: @"Результаты поиска"
                                           brand: @"Печки-лавочки"
                                           category: @"Одежда/Мужская одежда/Футболки"
                                           coupon: nil
                                           position: @"2"
                                           price: @"2345.50"
                                           quantity: nil
                                           variant: @"Серый цвет"];
    
TrackerTop100ECommerce *ecommParams = [[TrackerTop100ECommerce alloc]
                                           initWithCurrencyCode:@"RUB"
                                           action: action
                                           products: nil
                                           impressions: @[product1, product2]
                                           promotions: nil];
    
[TrackerTop100 trackEcommWithEventName: @"purchase" ecommParams: ecommParams];
```
{% endtab %}
{% endtabs %}
