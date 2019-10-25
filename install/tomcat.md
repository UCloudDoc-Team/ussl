

# Tomcat8.5/Tomcat9的证书部署

**一、获取jks格式证书**

登录：<https://console.ucloud.cn/ussl/ussl>

查看订单后，操作：证书下载，解压缩后看到如图的文件夹

![](/images/install/文件.png)

文件夹内文件的格式为pem，cer后缀的是证书公钥(此文件可以改名为server.pem)，key后缀的是私钥(可以改名为server.key)

需要从此处[格式转换工具](/security/ussl/faq/certificateconvert)转换为JKS格式的证书

二、到tomcat中部署证书

把jks文件存放到conf目录下，然后配置同目录下的server.xml文件，第一次配置的话，有段被注释掉的connector，使用的是NIO来做JSSE引擎的，修改为

``` 
<Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol"  maxThreads="150" SSLEnabled="true">

        <SSLHostConfig>

            <Certificate certificateKeystoreFile="conf/www.trustasia.com.jks"

              certificateKeystorePassword="刚才设置的证书密码"

              certificateKeyAlias="www.trustasia.com"

                         type="RSA" />

        </SSLHostConfig>

    </Connector>

```

<wrap em> 注：certificateKeystorePassword和certificateKeyAlias
需要添加进去。</wrap>

certificateKeystorePassword为jks密码

certificateKeyAlias为jks别名，没有特殊情况的别名就是申请的证书域名，比如申请了\_.trustasia.com.jks的通配符证书，别名为\*.trustasia.com;
www.trustasia.com.jks的别名就是www.trustasia.com

别名查看方式，jdk工具里：keytool –list –keystore jks文件 –storepass
jks文件密码。这样就可以显示出条目列表。
