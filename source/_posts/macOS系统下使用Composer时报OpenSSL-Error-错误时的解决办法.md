---
title: macOS系统下使用Composer时报OpenSSL Error 错误时的解决办法
---
在macOS系统下使用Composer时，有时会遇到下面的错误信息
```bash
OpenSSL Error messages: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed 
Failed to enable crypto
```

出现该错误的原因是本地php.ini中的CA证书没有启用或者已经过期，导致https验证失败。解决办法也很简单，步骤描述如下：

1. 如果本地php.ini中没有启动CA证书，则需要下载一个最新的证书文件，下载地址：[http://curl.haxx.se/docs/caextract.html](http://curl.haxx.se/docs/caextract.html)
2. 下载完毕后将证书文件保存到一个目录中，我放在了/usr/local/ssl目录中
3. 找到本地php.ini文件，找到其中的 "openssl.cafile"项，将其前面的';'去掉，并将证书存放路径填写到等号后面，例如：
```bash
openssl.cafile=/usr/local/ssl/cacert.pem
```
4. OK，到这里应该可以正常使用Composer了。

如果是由于本地CA证书过期的话，处理也很简单，从[http://curl.haxx.se/docs/caextract.html](http://curl.haxx.se/docs/caextract.html)下载最新的证书，用其内容替换掉老证书即可。

---
date: 2022-08-23 17:59:26
tags: [PHP, Composer, SSL, OpenSSL]
---
