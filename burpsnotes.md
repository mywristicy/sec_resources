## General Burp Suite notes
#### Settings Info
- *Response Interception*: By default the proxy does not intercept server responses unless explicitly requested on a per-request basis.
- The "Intercept responses based on the following rules" checkbox, along with the defined rules, allows for a more flexible response interception.
- Search for "Response intercept rules" in settings to find this. Should be under "Proxy".
- *Match and Replace*: This section in the Proxy settings enables the user of regular expressions (regex) to modify incoming and outgoing requests. This feature allows for dynamic changes such as modifying the user agent or manipulating cookies.

#### FoxyProxy
- To use Burp Suite Proxy, we need to configure our local web browser to redirect traffic through Burp Suite.
- Firefox only: Download & install FoxyProxy Basic extension (https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/)
- Once installed, click on the FoxyProxy button to access the app and its options.
- Next, click "Options" and from the new page click "Add". Fill in the details with the following values.
```
Title: Burp
Proxy type: HTTP
IP: 127.0.0.1
Port: 8080
```
- After saving the settings, click the extension button again and select the "Burp" configuration we just created. This will redirect the browser traffic through 127.0.0.1:8080.
- Finally, go to Burp Suite and ensure that Intercept is turned on in the Proxy tab.
- To test the proxy, open firefox and try accessing a site. The browser should hang and the proxy will populate with the HTTP request.
- 