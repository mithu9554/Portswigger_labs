## Lab: JWT authentication bypass via algorithm confusion with no exposed key

#### Brute-force the server's public key
1. Base64-encoded public key in both X.509 and PKCS1 format.
2. tampered JWT signed with each of these keys.

```
docker run --rm -it portswigger/sig2n <token1> <token2>
```

linux commend
```
sudo systemctl start docker
sudo service docker restart
```
