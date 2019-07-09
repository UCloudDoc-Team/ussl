{{indexmenu_n>2}}

# 为App部署SSL证书 应对苹果ATS限制

## ATS（App Transport Security）与HTTPS

**App Transport Security，简称 ATS**，是苹果在 iOS 9 当中推出的一项安全功能。

在开启 ATS 安全特性之后，它会强制App应用及网页通讯自动通过 HTTPS加密传输连接网络服务，
通过加密App及网页通讯来保障用户数据安全。即
App后端服务器必须部署SSL证书，启用HTTPS加密协议，否则您的App应用将不能通过苹果商店的审核发布，导致App应用无法正常使用。

## ATS功能解读

1\. **HTTPS：** App后端服务器必须启用HTTPS加密传输网络服务

2\. **TLS1.2：** 服务器所有连接必须支持TLS协议1.2以上版本

3\. **哈希算法：** SSL证书是使用SHA256或者更高级的ECC算法

4\. **密钥：** SSL证书是使用2048位以上RSA密钥

5\. **正向保密：**加密套件配置要求，支持苹果列出的正向保密列表（苹果配置官方文档）

## 如何便捷通过ATS安全功能要求

**选择合适的服务器SSL证书，启用HTTPS加密连接。**截止2016年底，为助力App开发者应对Apple
ATS策略，我们提供更优惠的SSL证书申请。国际知名的Symantec
SSL证书可满足ATS的各项要求， <wrap em>特别是具有ECC
算法的SSL证书，公钥长度短，延长设备寿命省电并且节省流量</wrap> 。

**便捷免费的ATS检测工具：**针对ATS的要求，提供便捷免费的
[ATS检测工具](https://www.trustasia.com/apple-ats),即可一键检测与您App应用交互的服务器是否符合ATS要求。
