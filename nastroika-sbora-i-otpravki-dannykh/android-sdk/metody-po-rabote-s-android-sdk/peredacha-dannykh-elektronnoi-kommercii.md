# Передача данных электронной коммерции

Для передачи действий пользователя с ECommerce данными необходимо собрать и передать данные в событие в определенном формате \<ECommerceEvent>:

#### Формат данных \<ECommerceEvent>

| Поле         | Тип данных                                                                                               |                                                                                                                                                                                                                                            |
| ------------ | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| currencyCode | String                                                                                                   | Трехбуквенный [код валюты по ISO 4217](https://en.wikipedia.org/wiki/ISO\_4217#Active\_codes). Если передается иная валюта, будут отправлены нулевые значения вместо валюты и суммы.                                                       |
| action       | [\<ECommerceAction>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md)      | Дополнительные данные, описывающие действие, произведённое с товаром или набором товаров. Данные передаются в виде объекта [\<ECommerceAction>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).            |
| products     | [\[\<ECommerceProduct>\]](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md) | Список описаний товаров, с которыми было произведено указанное действие. Описание каждого из товаров представляет собой объект вида [\<ECommerceProduct>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).  |
| impressions  | [\[\<ECommerceProduct>\]](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md) | Список описаний товаров, относящихся к действию impressions (показ товара или набора товаров). Данные передаются в виде объекта [\<ECommerceProduct>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).      |
| promotions   | [\[\<ECommercePromo>\]](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md)   | Массив данных, описывающих связанное с рекламной акцией действие. Данные передаются в виде объекта [\<ECommercePromo>](../../veb-schyotchik/peredacha-e-commerce-dannykh/format-ecommerce-dannykh.md).                                     |

#### Отправка события ECommerceEvent

Показ товара (impressions):

{% tabs %}
{% tab title="Kotlin" %}
```
val product1 = ECommerceProduct("779213")
    .apply {
        name = "Футболка" // Optional.
        list = "Вы недавно смотрели" // Optional.
        brand = "Печки-лавочки"
        category = "Одежда/Мужская одежда/Футболки"
        coupon = "PARTNER_SITE_15"
        position = 2
        price = BigDecimal(145.555)
        quantity = 5
        variant = "Красный цвет"
    }

val product2 = ECommerceProduct("25315")
    .apply {
        name = "Футболка с рисунком" // Optional.
        list = "Результаты поиска" // Optional.
        brand = "Печки-лавочки"
        category = "Одежда/Мужская одежда/Футболки"
        coupon = "PARTNER_SITE_15"
        position = 2
        price = BigDecimal(2345.50)
        variant = "Красный цвет"
    }


val eventParam = ECommerceEvent.setParams("RUB", listOf(product1, product2))
Kraken.trackEcom("impressions", eventParam
```
{% endtab %}

{% tab title="Java" %}
```
ECommerceProduct product = new ECommerceProduct("779213")
    .setName("Футболка")
    .setList("Вы недавно смотрели")
    .setBrand("Печки-лавочки")
    .setCategory("Одежда/Мужская одежда/Футболки")
    .setCoupon("PARTNER_SITE_15")
    .setPosition(2)
    .setPrice (145)
    .setQuantity(5)
    .setVariant("Красный цвет");

ECommerceAction action = new ECommerceAction("TRX#54321")
    .setCoupon("TRX")
    .setRevenue(444.4444)
    .setAffiliation("SPORTMASTER")
    .setTax(123.4444)
    .setShipping(567.897)
    .setList("Новинки")
    .setStep(2)
    .setOption("способ оплаты");

ECommercePromo promo = new ECommercePromo("PROMO12")
    .setName("Сезонная распродажа")
    .setCreative("sale_banner1")
    .setPosition("slot_2");

String eventParam = ECommerceEvent.setParams("RUB", Arrays.asList(product), action, Arrays.asList(promo));
Kraken.trackEcom("impressions", eventParam);
```
{% endtab %}
{% endtabs %}

Клик по промо-акции:

{% tabs %}
{% tab title="Kotlin" %}
```
val promo = ECommercePromo("PROMO12")
    .apply {
        name = "Сезонная распродажа"
        creative = "sale_banner1"
        position = "slot_2"
    }
val eventParam = ECommerceEvent.setPromoParams("RUB", listOf(promo))
Kraken.trackEcom("promoClick", eventParam)
```
{% endtab %}

{% tab title="Java" %}
```
ECommercePromo promo = new ECommercePromo("PROMO12")
    .setName("Сезонная распродажа")
    .setCreative("sale_banner1")
    .setPosition("slot_2");

String eventParam = ECommerceEvent.setPromoParams("RUB", Arrays.asList(promo));
Kraken.trackEcom("promoClick", eventParam);
```
{% endtab %}
{% endtabs %}

Клик по товару:

{% tabs %}
{% tab title="Kotlin" %}
```
val product = ECommerceProduct("779213")
    .apply {
        name = "Футболка" // Optional.
        list = "Результаты поиска" // Optional.
        brand = "рога и копыта"
        category = "Одежда/Мужская одежда/Футболки"
        coupon = "PARTNER_SITE_15"
        position = 1
        price = BigDecimal(1499.00)
        quantity = 2
        variant = "Красный цвет"
    }
val eventParam = ECommerceEvent.setParams("RUB", listOf(product))
Kraken.trackEcom("click", eventParam)
```
{% endtab %}

{% tab title="Java" %}
```
ECommerceProduct product = new ECommerceProduct("779213")
    .setName("Футболка с рисунком")
    .setList("Результаты поиска")
    .setBrand("рога и копыта")
    .setCategory("Одежда/Мужская одежда/Футболки")
    .setPosition(1)
    .setPrice (1499)
    .setQuantity(2)
    .setVariant("СиКрасныйний цвет");

ECommerceAction action = new ECommerceAction("TRX#54321")
    .setCoupon("TRX")
    .setRevenue(444.4444)
    .setAffiliation("SPORTMASTER")
    .setTax(123.4444)
    .setShipping(567.897)
    .setList("Новинки")
    .setStep(2)
    .setOption("способ оплаты");

ECommercePromo promo = new ECommercePromo("PROMO12")
    .setName("Сезонная распродажа")
    .setCreative("sale_banner1")
    .setPosition("slot_2");

String eventParam = ECommerceEvent.setParams("RUB", Arrays.asList(product), action, Arrays.asList(promo));
Kraken.trackEcom("click", eventParam);
```
{% endtab %}
{% endtabs %}

Добавление товара в корзину:

{% tabs %}
{% tab title="Kotlin" %}
```
val product = ECommerceProduct("779213")
    .apply {
        name = "Футболка"
        list = "Вы недавно смотрели"
        brand = "Печки-лавочки"
        category = "Одежда/Мужская одежда/Футболки"
        coupon = "PARTNER_SITE_15"
        position = 2
        price = BigDecimal(145.555)
        quantity = 5
        variant = "Красный цвет"
    }
val eventParam = ECommerceEvent.setParams("RUB", listOf(product))
Kraken.trackEcom("add", eventParam)
```
{% endtab %}

{% tab title="Java" %}
```
ECommerceProduct product = new ECommerceProduct("453454")
    .setName("Футболка")
    .setList("Вы недавно смотрели")
    .setBrand("Печки-лавочки")
    .setCategory("Одежда/Мужская одежда/Футболки")
    .setCoupon("PARTNER_SITE_15")
    .setPosition(2)
    .setPrice (145)
    .setQuantity(5)
    .setVariant("Красный цвет");

String eventParam = ECommerceEvent.setParams("RUB", Arrays.asList(product));
Kraken.trackEcom("add", eventParam);
```
{% endtab %}
{% endtabs %}

Показ информации о товаре:

{% tabs %}
{% tab title="Kotlin" %}
```
val product = ECommerceProduct("779213")
    .apply {
        name = "Футболка" // Optional.
        list = "Результаты поиска" // Optional.
        brand = "рога и копыта"
        category = "Одежда/Мужская одежда/Футболки"
        coupon = "PARTNER_SITE_15"
        position = 1
        price = BigDecimal(1499.00)
        quantity = 2
        variant = "Красный цвет"
    }
val action = ECommerceAction("TRX#54321")
    .apply {
        coupon = "TRX"
        revenue = BigDecimal(444.4444)
        affiliation = "SPORTMASTER"
        tax = BigDecimal(123.4444)
        shipping = BigDecimal(567.897)
        list = "Новинки"
        step = 2
        option = "способ оплаты"
    }

val eventParam = ECommerceEvent.setParams("RUB", listOf(product))
Kraken.trackEcom("detail", eventParam)
```
{% endtab %}

{% tab title="Java" %}
```
ECommerceProduct product = new ECommerceProduct("P15432")
    .setName("Бейсболка")
    .setList("Вы недавно смотрели")
    .setBrand("Печки-лавочки")
    .setCategory("Одежда/Мужская одежда/Футболки")
    .setPrice (503.60)
    .setVariant("Синий цвет");

String eventParam = ECommerceEvent.setParams("RUB", Arrays.asList(product));
Kraken.trackEcom("detail", eventParam);
```
{% endtab %}
{% endtabs %}

