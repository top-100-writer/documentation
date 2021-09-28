# Формат eCommerce-данных

В общем случае eCommerce-объект характеризуется следующими полями:

| **Поле** | **Тип** | **Описание** |
| :--- | :--- | :--- |
| ecommerce | object | Обязательное поле. Контейнер полей-параметров eCommerce-объекта. |
| currencyCode | string | Трехбуквенный [код валюты по ISO 4217](https://en.wikipedia.org/wiki/ISO_4217#Active_codes). Если передается иная валюта, будут отправлены нулевые значения вместо валюты и суммы. Указывается в коде в качестве параметра поля ecommerce. |
| &lt;actionType&gt; | string | Идентификатор действия, произведённого с набором товаров. Указывается в коде в качестве параметра поля ecommerce. Возможные значения: click – клик по товару \(ссылке на товар\); detail – просмотр полного описания \(карточки\) товара; add – добавление товара в корзину; remove – удаление товара из корзины; checkout – переход к оформлению покупки; checkout\_option – выбор пользователя на определенном этапе оформления покупки; purchase – покупка товара; refund – возврат одного или нескольких товаров. |
| actionField | object [&lt;actionField&gt;](format-ecommerce-dannykh.md#struktura-obekta-s-dannymi-o-deistvii-less-than-actionfield-greater-than) | Дополнительные данные, описывающие действие, произведённое с товаром или набором товаров. Данные передаются в виде объекта [&lt;actionField&gt;](format-ecommerce-dannykh.md#struktura-obekta-s-dannymi-o-deistvii-less-than-actionfield-greater-than). Поле обрабатывается, только для данных о покупках \(&lt;actionType&gt;=purchase\). Указывается в коде в качестве параметра поля &lt;actionType&gt;. |
| products | array [&lt;productFieldObject&gt;](format-ecommerce-dannykh.md#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara) | Список описаний товаров, с которыми было произведено указанное действие. Данные обязательны для событий &lt;actionType&gt;. Описание каждого из товаров представляет собой объект вида [&lt;productFieldObject&gt;](format-ecommerce-dannykh.md#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara). Указывается в коде в качестве параметра поля &lt;actionType&gt;. |
| impressions | array [&lt;productFieldObject&gt;](format-ecommerce-dannykh.md#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara) | Список описаний товаров, относящихся к действию impressions \(показ товара или набора товаров\). Указывается в коде в качестве параметра поля ecommerce. Данные передаются в виде объекта [&lt;productFieldObject&gt;](format-ecommerce-dannykh.md#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara). Надо передавать в следующих случаях: просмотр каталога, загрузка главной страницы, просмотр разделов \(и подразделов\) сайта с товарами. **ВНИМАНИЕ!** Следует передавать только те товары, которые действительно были показаны на странице, а не в принципе подгрузились. _Например, если в блоке «Новинки» показывается по 3 товара за раз, а дальше карусель, нужно передавать 3 товара в первый момент, а не, например, 8, которые были предзагружены._ |
| &lt;promoActionType&gt; | string | Идентификатор промо-действия, произведённого с набором товаров. Возможные значения: promoView, promoClick. |
| promotions | array [&lt;promoFieldObject&gt;](format-ecommerce-dannykh.md#struktura-obekta-less-than-promofieldobject-greater-than-s-dannymi-o-reklamnoi-akcii) | Массив данных, описывающих связанное с рекламной акцией действие &lt;promoActionType&gt;. Данные передаются в виде объекта [&lt;promoFieldObject&gt;](format-ecommerce-dannykh.md#struktura-obekta-less-than-promofieldobject-greater-than-s-dannymi-o-reklamnoi-akcii). Указывается в коде в качестве параметра поля &lt;promoActionType&gt;. |

Вложенность параметров eCommerce-объекта в общем случае следующая:

```text
window.dataLayer.push({
    “ecommerce”: {
        “currencyCode”: “<код валюты по ISO 4217>”,
        “<actionType>” : {
            “actionField” : <actionField>,
            “products” : [<productFieldObject>, <productFieldObject>, …]
        },
        “impressions” : [<productFieldObject>, <productFieldObject>, …],
        “<promoActionType>” : {
            “promotions” : [<promoFieldObject>, <promoFieldObject>, …]
        }
    }
});
```

Какие именно группы полей отправлять зависит от конкретной ситуации/события.

Так, например, при отображении страницы с каталогом товаров и рекламным объявлением следует передавать `impressions` c перечнем показанных товаров и `promoView` в качестве `<promoActionType>` с данными по рекламе:

```text
window.dataLayer.push({
    “ecommerce”: {
        “currencyCode”: “<код валюты по ISO 4217>”,
        “impressions” : [<productFieldObject>, <productFieldObject>, …],
        “promoView” : {
            “promotions” : [<параметры конкретной рекламы в формате promoFieldObject>]
        }
    }
});
```

При клике по конкретному товару из списка результатов поиска – `click` в качестве `<actionType>` c данными по товару и, например, названием блока «Результаты поиска»:

```text
window.dataLayer.push({
    “ecommerce”: {
        “currencyCode”: “<код валюты по ISO 4217>”,
        “click” : {
            “actionField” : {
                “list” = “Результаты поиска”
            },
            “products” : [<параметры конкретного товара в формате productFieldObject>]
        }
    }
});
```

Рекомендации по тому, какие группы полей для каких ситуаций и событий передавать, приводятся в разделе «[Рекомендации по передаче eCommerce-данных](rekomendacii-po-peredache-ecommerce-dannykh.md)».

## Структура объекта &lt;productFieldObject&gt; с описанием товара:

| **Поле** | **Тип** | **Описание** |
| :--- | :--- | :--- |
| id | string | Обязательное поле.Идентификатор товара. Пример: «SKU». |
| name | string | Название товара. Пример: «Футболка». Поле опциональное, но рекомендуется его передавать. |
| list | string | Название блока, куда входит/ отображается товар. Пример: «Результаты поиска», «Вы недавно смотрели», «Вам также могут понравиться». |
| brand | string | Бренд, торговая марка, ассоциированная с товаром. Пример: «Печки-лавочки». |
| category | string | Категория, к которой относится товар. Поддерживается иерархия категорий до 5 уровней вложенности. Разделителем уровней является символ «/». Пример: «Одежда/Мужская одежда/Футболки». |
| coupon | string | Промокод, ассоциированный с товаром. Пример: «PARTNER\_SITE\_15». |
| position | number | Положение товара в списке. Пример: «2». |
| price | number | Итоговая стоимость единицы товара с учетом всех скидок. |
| quantity | integer | Количество единиц товара. |
| variant | string | Разновидность товара. Пример: «Красный цвет». |

## Структура объекта &lt;promoFieldObject&gt; с данными о рекламной акции:

| **Поле** | **Тип** | **Описание** |
| :--- | :--- | :--- |
| id | string | Обязательное поле.Идентификатор рекламной акции. Пример: «PROMO12». |
| name | string | Название рекламной акции. Пример: «Сезонная распродажа». Поле опциональное, но рекомендуется его передавать. |
| creative | string | Cвязанное с рекламной акцией объявление. Пример: «sale\_banner1». |
| position | string | Позиция объявления. Пример: «slot\_2». |

## Структура объекта с данными о действии &lt;actionField&gt;:

| **Поле** | **Тип** | **Описание** |
| :--- | :--- | :--- |
| id | string | Обязательное поле. Идентификатор покупки. Пример: «TRX\#54321». |
| coupon | string | Промокод, ассоциированный со всей покупкой целиком. |
| revenue | number | Полученный доход. Если не указан, вычисляется автоматически как сумма цен всех товаров, ассоциированных с покупкой. |
| affilation | string | Магазин или филиал, в котором произошла транзакция. |
| tax | number | Сумма всех налогов для данной покупки. |
| shipping | number | Стоимость доставки данной покупки. |
| list | string | Название блока, куда входят/отображаются товары из данной покупки. Примеры: «Новинки», «Результаты поиска». |
| step | number | Число, представляющее этап последовательности покупки. Передается для действий типа checkout и checkout\_option. |
| option | string | Дополнительное поле, передаваемое для действий типа checkout и checkout\_option. Предоставляет информацию о выборе пользователя на определенном этапе оформления покупки \(например, о выбранном способе оплаты\). |

