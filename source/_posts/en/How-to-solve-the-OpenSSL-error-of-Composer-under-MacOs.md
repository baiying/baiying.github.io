---
title: How to solve the OpenSSL error of Composer under MacOs
date: 2022-11-29 10:18:26
categories: [Programming, Skill]
tags: [MacOS, PHP, Composer, OpenSSL]
---
When using Composer under macOS system, sometimes you will encounter the following error message:

```bash
OpenSSL Error messages: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed 
Failed to enable crypto
```

The reason for this error is that the CA certificate in the local php.ini is not enabled or has expired, which leads to the failure of https verification. The solution is also very simple, the steps are as follows:

1. If the CA certificate is not enabled in the local php.ini, you need to download a newest certificate file, download address: [http://curl.haxx.se/docs/caextract.html](http://curl.haxx.se/docs/caextract.html).
2. After the download is complete, save the certificate file in a directory, and I put it in the /usr/local/ssl directory.
3. Find the local php.ini file, find the "openssl.cafile" item, remove the ';' in front of it, and fill in the certificate storage path after the equal sign, for example:
```bash
openssl.cafile=/usr/local/ssl/cacert.pem
```
4. OK, now you should be able to use Composer normally.

If it is due to the expiration of the local CA certificate, the processing is also very simple, just download the latest certificate from [http://curl.haxx.se/docs/caextract.html](http://curl.haxx.se/docs/caextract.html) and replace the old certificate with its content.
