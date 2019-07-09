{{indexmenu_n>4}}

# JBoss证书部署

**第一步：获取并导入证书**

下载Jboss类型证书，您将收到三段证书代码，将“您的SSL证书”下面的代码（包括“-----BEGIN
CERTIFICATE-----”和“-----END CERTIFICATE-----”）复制粘贴到文本文档 并保存成
cer格式的文件 如server.cer
。以同样的方法把“XX型SSL中级证书”下面的代码保存成intermediate.cer把“XX型SSL交叉证书”下面的代码保存成
cross.cer
最后把server.cer、intermediate.cer、cross.cer和server.jks(生成CSR时产生的文件)几个文件保存到同一个目录，例如c盘根目录目录下。

导入中级证书：

`keytool -import -alias intermediate -keystore c:\server.jks
-trustcacerts –file c:\intermediate.cer`

提示“认证已添加至keystore中”则导入成功。

导入交叉证书：

`keytool -import -alias cross -keystore c:\server.jks -trustcacerts
-file c:\cross.cer`

提示“认证已添加至keystore中” 则导入成功。

导入服务器证书：

进入Java\_JRE\\bin目录，如 cd C:\\PROGRA\~1\\Java\\jre1.6.0\_10\\bin，运行如下命令：

`keytool -import -alias mykey -keystore c:\server.jks -trustcacerts
-file c:\server.cer`

输入密码后 提示：“认证回复已安装在 keystore中”说明导入成功。

**第二步：更新 server.xml配置文件**

将已正确导入认证回复的server.jks文件到Jboss安装目录下

用文本编辑器打开Jboss安装目录下server/default/deploy/jbossweb.sar目录中的server.xml文件，

并更新以下内容

``` 

      <Connector protocol="HTTP/1.1" SSLEnabled="true" 

      port="443" address="${jboss.bind.address}"

      scheme="https" secure="true" clientAuth="false" 

      keystoreFile="/usr/local/jboss/server.jks "

      keystorePass="123456" sslProtocol = "TLS" />
```

下面为配置文件参数说明：

port="443"

SSL访问端口号为443

keystoreFile

私钥库文件 server.jks

keystorePass

私钥库密码 123456

按照以上的步骤配置完成后，重新启动 Jboss。

如有任何问题或疑问请直接与我们联系，谢谢！
