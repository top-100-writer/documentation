# Передача данных в web-view

Если есть необходимость связать события отправляемые из SDK и JS-счëтчика, то необходимо добавить следующий код:

{% tabs %}
{% tab title="Swift" %}
```swift
import WebKit
import TrackerTop100SDK

class WebViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        
        // Добавляем script после того как html загрузится
        let userScript = WKUserScript(
            source: TrackerTop100.getDataToWebView(), 
            injectionTime: .atDocumentEnd, 
            forMainFrameOnly: true
        )
        
        // Устанавлваем скрипт в конфигурацию загрузки webview
        let userContentController = WKUserContentController()
        userContentController.addUserScript(userScript)
        let configuration = WKWebViewConfiguration()
        configuration.userContentController = userContentController
        
        let webView = WKWebView(frame: view.bounds, configuration: configuration)
        
        //...
    }
}
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
#import "WebViewController.h"
@import TrackerTop100SDK;

@interface WebViewController ()

@end

@implementation WebViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    // Добавляем script после того как html загрузится
    WKUserScript *userScript = [[WKUserScript alloc] initWithSource: [TrackerTop100 getDataToWebView] injectionTime:WKUserScriptInjectionTimeAtDocumentEnd forMainFrameOnly:YES];
    
    // Устанавлваем скрипт в конфигурацию загрузки webview
    WKUserContentController *userContentController = [[WKUserContentController alloc] init];
    [userContentController addUserScript: userScript];
    WKWebViewConfiguration *configuration = [[WKWebViewConfiguration alloc] init];
    configuration.userContentController = userContentController;
    
    WKWebView *webView = [[WKWebView alloc] initWithFrame: self.view.bounds configuration: configuration];
    
    //...
}

@end
```
{% endtab %}
{% endtabs %}
