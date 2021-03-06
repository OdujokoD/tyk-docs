---
date: 2017-03-23T14:36:28Z
title: TLS and SSL
menu:
  main:
    parent: "Security"
weight: 2
url: "/security/tls-and-ssl"
---

Tyk supports TLS connections, and as of version 2.0 all TLS connections will also support HTTP/2. To enable SSL in your Tyk gateway and dashboard, you will need to modify the `tyk.conf` and `tyk_analytics` files to include a server options section like so:

```{.copyWrapper}
"http_server_options": {
  "use_ssl": true,
  "server_name": "yoursite.com",
  "min_version": 771,
  "certificates": [
    {
      "domain_name": "*.yoursite.com",
      "cert_file": "./new.cert.cert",
      "key_file": "./new.cert.key"
    }
  ]
},
```
    

You can enter multiple certificates, that link to multiple domain names, this enables you to have multiple SSL certs for your gateways or dashboard domains if they are providing access to different domains via the same IP.

The `min_version` setting is optional, you can set it to have Tyk only accept connections from TLS V1.0, 1.1 and 1.2 respectively.

#### Values for TLS Versions

You need to use the following values for setting the TLS `min_version`:

| TLS Version   | Value to Use   |
|---------------|----------------|
|      1.0      |      769       |
|      1.1      |      770       |
|      1.2      |      771       |


#### Specify TLS Cipher Suites

You can optionally add the additional `http_server_options` config option `ssl_ciphers` which takes an array of strings as its value.

Each string must be one of the allowed cipher suites as defined at https://golang.org/pkg/crypto/tls/#pkg-constants

For example:

```{.copyWrapper}
"http_server_options": {
  "ssl_ciphers": [
    "TLS_RSA_WITH_AES_128_GCM_SHA256", 
    "TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA"
  ]
},
```
