## Lab: Exploiting a mass assignment vulnerability

##### Obtain the server's public key
``` /jwks.json ```

1. In Burp, go to the JWT Editor Keys tab in Burp's main tab bar.

2. Click New RSA Key.

3. In the dialog, make sure that the JWK option is selected, then paste the JWK that you just copied. Click OK to save the key.

4. Right-click on the entry for the key that you just created, then select Copy Public Key as PEM.

5. Use the Decoder tab to Base64 encode this PEM key, then copy the resulting string.

6. Go back to the JWT Editor Keys tab in Burp's main tab bar.

7. Click New Symmetric Key. In the dialog, click Generate to generate a new key in JWK format. Note that you don't need to select a key size as this will automatically be updated later.

8. Replace the generated value for the k property with a Base64-encoded PEM that you just created.

9. Save the key.


