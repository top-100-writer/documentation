# Передача данных в web-view

Если есть необходимость связать события отправляемые из sdk и js-счетчика, то необходимо добавить следующий код в Activity:

{% tabs %}
{% tab title="Kotlin" %}
```
import ru.top100.tracker.kraken.di.Kraken.getData
import android.webkit.JavascriptInterface

//...

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
    val myWebView: WebView = findViewById(R.id.webViewIds)
    myWebView.settings.javaScriptEnabled = true
    myWebView.loadUrl("http://www.example.com")
    myWebView.addJavascriptInterface(MyJavascriptInterface(), "kraken")
}

class MyJavascriptInterface {
    @get:JavascriptInterface
    val data: String
        get() = getData()
}
```
{% endtab %}
{% endtabs %}
