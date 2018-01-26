---
title: HTTPS SSL证书格式转换
date: 2018-01-27 01:44:39
tags:
---

# 转换证书格式
```bash
#查看证书
openssl x509 -in cert.crt -text -noout

#查看DER encoded证书
openssl x509 -in uhttpd.crt -inform der -text -noout

#PEM to DER
openssl x509 -in cert.crt -outform der -out uhttpd.crt
openssl rsa -in cert.key -outform der -out uhttpd.key

#DER to PEM
openssl x509 -in uhttpd.crt -inform der -outform pem -out cert.crt
openssl rsa -in uhttpd.key -inform der -outform pem -out cert.key
```