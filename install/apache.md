{{indexmenu_n>3}}

# Apache 2.x 证书部署

**第一步：获取服务器证书和保存到同一个目录**

证书审批通过后可以从控制台直接下载证书，证书文件的内容格式如下，把第一段代码保存成一个crt格式的文件（文本格式）如 domain.crt
，第二段和第三段粘贴到一个文本中保存一个 crt格式的文件如 CA.crt。

``` 
    -----BEGIN CERTIFICATE-----
    MIIDDTCCAfUCAQAwgZQxCzAJBgNVBAYTAkNOMRIwEAYDVQQIDAnkuIrmtbfluIIx
    EjAQBgNVBAcMCeS4iua1t+W4gjEtMCsGA1UECgwk5LiK5rW35Z+f6IGU6L2v5Lu2
    5oqA5pyv5pyJ6ZmQ5YWs5Y+4MRIwEAYDVQQLDAnmioDmnK/pg6gxGjAYBgNVBAMT
    EXd3dy50cnVzdGFzaWEuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKC
    AQEAyr8u1KAV2ZZ7UmnFgssNV/iyGoNsBsRCI8ZtDneM8gDM1EoteG0nMitPxuPZ
    Vwfar9TTYGmJ8PTP3G80aM+hC1oQQbs3iOVWIus/R/AXCtTNQ8CpMDvXjLLMjV5X
    KbZotyVL1KpoEw8nyWwtoiDXPJe3OyFYZ7HHx1qBPWvHogwQgn4UhPH/k3/e1GYc
    lErZnWq2h2vVDB6sk01X1GuRTXYWozeB7dXYrCcU++umo4Q+pbGw8aWkhZ4WxuWg
    vssYC2bHbrv7HiBzBq/E/v8=
    -----END CERTIFICATE-----
```

最后把domain.crt 、CA.crt和domain.key (在申请证书时生成的那个私钥保存成 domain.key )<wrap
em>三个文件保存到同一个目录</wrap>，例如/usr/local/apache/conf目录下。

**第二步：更新 httpd.conf 配置文件**

1.用文本编辑器打开Apache根目录下 conf/httpd.conf 文件 找到

``` 
  #LoadModule ssl_module modules/mod_ssl.so 
```

和

``` 
  #Include conf/extra/httpd-ssl.conf 
```

去掉前面的 \# 号 2.用文本编辑器打开Apache根目录下 conf/extra/httpd-ssl.conf 文件修改一下内容：

    <VirtualHostwww.trustasia.com:443>
        DocumentRoot "/var/www/html"
        ServerName www.trustasia.com
        SSLEngine on
        SSLCertificateFile /usr/local/apache/conf/domain.crt
        SSLCertificateKeyFile /usr/local/apache/conf/domain.key
        SSLCertificateChainFile /usr/local/apache/conf/CA.crt
    </VirtualHost>

下面为配置文件参数说明：

<WRAP round box>

SSLEngine on

启用SSL功能

-----

SSLCertificateFile

证书文件domain.crt

-----

SSLCertificateKeyFile

私钥文件domain.key

-----

SSLCertificateChainFile

证书链文件 CA.crt

</WRAP>

按照以上的步骤配置完成后，重新启动 Apache 就可以使用https:// *来访问了。*

如有任何问题或疑问请直接与我们联系，谢谢
