

# Nginx部署

**一、 获取pem格式的证书公私钥**

首先登录SSL控制台：<https://console.ucloud.cn/ussl/ussl。然后下载证书>

证书格式：pem for nginx

解压后会获得两个文件：cer后缀的是证书公钥(此文件可以改名为server.pem)，key后缀的是私钥(可以改名为server.key)

**二、 在nginx里部署证书及优化配置ssl**

到nginx的conf目录，找到nginx.conf文件，修改或者配置这样一段

    server {
            listen       443;(ps:nginx1.15及以上的版本要修改为listen 443 ssl；)
            server_name  www.trustasia.com #你们的域名，如www.abc.com;
            ssl                  on;
            ssl_certificate      /xxx/xxx/server.pem; #根据实际的路径和文件名配置
            ssl_certificate_key   /xxx/xxx/server.key; #根据实际的路径和文件名配置
            ssl_session_timeout  5m;
            ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #按照这个协议配
            ssl_ciphers  ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;#按照这个套件配
            ssl_prefer_server_ciphers   on;
            location / {
                root   html; #站点目录
                index  index.html index.htm;
            }
    }

下面为配置文件参数说明： <WRAP round box> listen 443

SSL访问端口号为443

-----

ssl on

启用SSL功能

-----

ssl\_certificate

证书文件server.pem

-----

ssl\_certificate\_key

私钥文件server.pem

-----

ssl\_protocols

使用的协议

-----

ssl\_ciphers

配置加密套件，写法遵循openssl标准 </WRAP>

配置完成后，先用bin/nginx –t来测试下配置是否有误，正确无误的话，建议重启nginx。

**三、 使用全站加密，http自动跳转https（可选）**

对于用户，不是不知道https，就是知道https也因为懒，不愿意输入https。这样就有一个需求，让服务器自动把http的请求重定向到https。

在服务器这边的话配置的话，可以在页面里加js脚本，也可以在后端程序里写重定向，当然也可以在web服务器来实现跳转。Nginx是支持rewrite的（只要在编译的时候没有去掉pcre）

在http的server里 增加rewrite ^(.\*) <https://$host$1> permanent;

这样就可以实现80进来的请求，重定向为https了。
