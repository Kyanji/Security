# OpenSSL
## Basics
Gen private key - more info - encrypt sk
```
openssl genrsa -out key.pem 1024
openssl rsa -in key.pem -text -noout
openssl rsa -in key.pem -des3 -out enc-key.pem
```
Extract public key

```
openssl rsa -in key.pem -pubout -out pub-key.pem
```
Encrypt - Decrypt
```
openssl pkeyutl -encrypt -in text.txt -inkey pub-key.pem -out text-cipher.txt -pubin
openssl pkeyutl -decrypt -in text-cipher.txt -inkey key.pem -out text-not-cipher.txt
```
## Digital signatures
Hash
```
openssl dgst -md5 -out digest-file.txt text.txt
```
Digital signature and validation
```
 openssl pkeyutl -sign -in digest-file.txt -out text-signed.txt -inkey key.pem
 openssl pkeyutl -verify -sigfile text-signed.txt -in digest-file.txt -inkey pub-key.pem -pubin
```

# Certificate

```
openssl req
-newkey rsa:2048 -nodes -keyout domain.key
-out domain.csr

openssl ca -selfsign \
    -config etc/root-ca.conf \
    -in ca/root-ca.csr \
    -out ca/root-ca.crt \
    -extensions root_ca_ext
```
X509
```
openssl x509
-in domain.crt
-signkey domain.key
-x509toreq -out domain.csr
```
sign 
```
openssl ca 
 -in server.csr -out server.cer
```
```
```