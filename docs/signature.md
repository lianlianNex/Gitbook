# Signature

Signature is the only criterion for determining data authenticity between you and LianLian. We use MD5withRSA algorithm with key size 1024 to generate [RSA signature](https://en.wikipedia.org/wiki/RSA_(cryptosystem)).

There are two sets of public and private keys, one from merchant and another one is from LianLian in the whole verification process:

* When **you submit request to our server**, you need to build the [signature source](#signature-source)and encrypt it with your ```private key``` to generate signature. After receiving your requests, we decrypt the signature with your ```public key``` and then check the authenticity. 

* When **you receive requests from our server**, you need to obtain the signature and parameters in our requests first, and then verify them with the ```public key``` provided by us.

> You may also refer to [RSA Data Security Digital Signature Process](https://technet.microsoft.com/en-us/library/cc962021.aspx).

###### Signature Source

In order to build signature source, remove parameters whose value is empty and then put all needed the parameters with format ```{key}={value}``` and connect them with ```&``` character together in ascending order of the first letter. e.g.

```html
busi_partner=101001&dt_order=20130516131212&info_order=用户13958069593购买了3桶羽毛球&money_order=210.97&name_goods=羽毛球&no_order=20130516000000001&notify_url=http://payhttp.xiaofubao.com/***/back.shtml&oid_partner=201304121000001004&sign_type=RSA
```

***

## Keys Generation

You need to use [openssl](https://www.openssl.org/) to generate keys.

###### Generate private key

```html
openssl genrsa -out rsa_private_key.pem 1024
```
A file named ```rsa_private_key.pem``` should be generated in your current folder. 

The following steps are required for Java and C#, if you are using PHP, you can continue with [Generate public key](#generate-public-key).

Convert ```rsa_private_key.pem``` in the format of PKCS8.

```html
openssl pkcs8 -topk8 -inform PEM -in rsa_private_key.pem -outform PEM -nocrypt
```

Remove the header, footer, line breaks of the output and save it. e.g.

```html
MIICdgIBADANBgkqhkiG9w0BAQEFAASCAmAwggJcAgEAAoGBALrnBQVM/VUTaECLW/VaMfJK4Lb6WZaL6Iy6MYWr0D4rSk3VU/33LvubRPUQAylWUpT8sgaHb2bkPl+1+DAvAELoR+2yIGRNq6X6oqAR/Drv/b6MOokzEGq9KxOQM44aRHgwBEbDTt1IWFIj241A5WBJpmrLLnyKAZm7jTmCmITpAgMBAAECgYBFuxlZb+74RcRYiGXntR37WspaGi9AhrRdhL4jNAX+m+IeBeBPWWCTCMwCblXvn0AyS9ETtIXwqmlHBjoxp+d9atLEyFN2GMu811gvfWTrK2LKQxO+eo5ulpJKuSAQkpz7bZzq5ByG8vlT8QZ+YKCp/7XCHto2PHtA2YO7CeR8gQJBAPL64oEfRsEi+NxOYN7mBeUPEcH1HCQ9hBcVaatSzWcdnJP/MCcL7V7Y02zwCJQxBSIbU5d/5brCEtVzMWLGupECQQDE6uHCzk+aWx1trioOAiwegENL7jy3E40cJ7ie8OvkP/mJZpbjNjSBefpsY/semzjBwd77hJKH0+SIpB/KTmDZAkB23e+DFYbqoy41sI5JXSRTG50nUr7Sp9l/5XTNYHOl12GrMTMgVwBn3xEHgSHhRV3qgo3RVrtPMvQ9wd3OIcRRAkBZucTg5Oz0omvIXEGhXHAJ/dusL4POz8POfnLrSU/TEyt65hn+seY+0PvAg9Ya3hOAhfw6ku/JoE1TzaUGo6wRAkEAr4e9y/swoH7SiDtuvCNHLha2sSDdmNVDWzWpvGNiomST17W2UuXxaLmFPZB5+Jd3bGndppYFsVKAD6Qf3ECBHQ==
```

###### Generate public key and upload it to LianLian dashboard

```html
openssl rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem
```

In your current folder, a file named ```rsa_public_key.pem``` should be generated. Open it and you will get something like this:

```html
-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC65wUFTP1VE2hAi1v1WjHySuC2
+lmWi+iMujGFq9A+K0pN1VP99y77m0T1EAMpVlKU/LIGh29m5D5ftfgwLwBC6Eft
siBkTaul+qKgEfw67/2+jDqJMxBqvSsTkDOOGkR4MARGw07dSFhSI9uNQOVgSaZq
yy58igGZu405gpiE6QIDAQAB
-----END PUBLIC KEY-----
```

Remove the header, footer, line breaks.

```html
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC65wUFTP1VE2hAi1v1WjHySuC2+lmWi+iMujGFq9A+K0pN1VP99y77m0T1EAMpVlKU/LIGh29m5D5ftfgwLwBC6EftsiBkTaul+qKgEfw67/2+jDqJMxBqvSsTkDOOGkR4MARGw07dSFhSI9uNQOVgSaZqyy58igGZu405gpiE6QIDAQAB
```

Upload it to [merchant dashboard](https://b.lianlianpay.com/trader/login.htm).

###### Obtain LianLian public key

Go to [merchant dashboard](https://b.lianlianpay.com/trader/login.htm) and obtain the file whose name is ```llpay_public_key.pem```.