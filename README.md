
# Rapport

Följande är gjort i denna uppgift, programkod följer efter.
1. Bytte namn på applikationen i res/values/strings.xml.
2. Applikationen gavs åtkomst till internet i AndroidManifest.xml.
3. I activity_main.xml togs textview elementet bort och ett webview
element lades till med ett nytt id "my_webview".
4. I MainActivity.java importerades nödvändiga klasser och deklarerade privata 
klassvariabler för webview elementet och websettings.
I samma fil så instantieras myWebView i "onCreate()" metoden och associeras med 
xml elementet via findViewById()-metoden. En ny webview client skapades och Javascript 
exekvering aktiverades.
5. I metoden "onOptionsItemSelected()" lades metodanrop till för metoder som skall
exekveras när dropdown-menyn används.
6. Ett simpelt html dokument lades till i app/src/main/assets/internalpage.html.
7. I metoden som anropas lades "myWebView.loadUrl()" för att dirigera användaren 
till önskad sida.
```
1. 
<string name="app_name">Emils app</string>

2.
<uses-permission android:name="android.permission.INTERNET" />

3.
<WebView
       android:id="@+id/my_webview"
       android:layout_width="match_parent"
       android:layout_height="match_parent" />"

3.
import android.webkit.WebSettings;
import android.webkit.WebView;
import android.webkit.WebViewClient;

private WebView myWebView;
private WebSettings webSettings;
 
4. 
myWebView = (WebView) findViewById(R.id.my_webview);
myWebView.setWebViewClient(new WebViewClient());
webSettings = myWebView.getSettings();
webSettings.setJavaScriptEnabled(true);
 
5.
if (id == R.id.action_external_web) {
        showExternalWebPage();
        return true;
}

if (id == R.id.action_internal_web) {
       showInternalWebPage();
       return true;
}"
 
6. 
<!DOCTYPE html>
<html>
<body>
<br>
<br>
<h1>This is the internal webpage</h1>
<p>It works!</p>

</body>
</html>

7. 
public void showExternalWebPage(){
        myWebView.loadUrl("https://his.se");
}

public void showInternalWebPage(){
       myWebView.loadUrl("///android_asset/internalpage.html");
}
  
  
```

![](Screenshot_20240408_203733.png)
![](Screenshot_20240408_203733.png)
