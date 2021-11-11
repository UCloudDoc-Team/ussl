

# 域名型(DV)

**验证内容：**域名所有权

**验证方式：**DNS验证；文件验证。

**备注：**`因为域名型(DV)的验证信息是通过签发系统自动扫描签发的，不能实现100%成功签发，若24小时之内没有签发，为保障使用，请换成升级为OV证书。`

域名验证信息配置是否有效，请通过下面在线工具自助检测：
<https://myssl.com/dns_check.html#ssl_verify>

## Step1：进入SSL证书管理

产品与服务-\>优盾-\>证书管理 USSL

![](/images/procedure/导航.png)

## Step2：购买证书

![](/images/procedure/购买证书.png)

在首页，点击【购买证书】，然后选择合适的证书下单购买。

## Step3：补全信息

购买后会看到生成了一条没有任何信息的待补全信息的证书，点击【补全信息】填写内容提交。

![](/images/procedure/待补全信息.png)

填写内容参见[补全信息](ussl/operate/complete)介绍。

## Step4：验证信息

<wrap em>注意：请尽快于 24 小时内手动设置 DNS 解析记录，验证通过后 20
分钟内即可签发证书，超时将导致申请失败。</wrap>

补全后必须进行验证才能收到证书。补全信息中选择的验证方式不同，操作就不一样。首先点击【验证】

![](/images/procedure/验证按钮.png)

### DNS验证方式

![](/images/operate/dns验证.png)

**验证类型**：DNS

**绑定的域名**：显示补全信息时填写的域名

**主域名**：假如添加的域名是abc.test.ucloud.cn,主域名是ucloud.cn，也就是一级域名，格式为：一级域名.顶级域名

**TXT主机记录值**：根据域名返回的唯一的txt主机记录值，请到您的DNS服务商处尽快添加txt记录。

<wrap em>请尽快于 24 小时内手动设置 DNS 解析记录，验证通过后 20
分钟内即可签发证书，超时将导致申请失败。</wrap>

在DNS服务商比如DNSPOD添加主机记录

![](/images/operate/添加记录.png)

<WRAP left round box 100%>

主机记录就是域名前缀，常见用法有：

@： 直接解析主域名 www.ucloud.cn 或者 ucloud.cn。

\*： 泛解析，匹配其他所有域名 \*.ucloud.cn。

mail： 将域名解析为mail.ucloud.cn，通常用于解析邮箱服务器。

二级域名： 如：abc.ucloud.cn，填写abc。

手机网站： 如：m.ucloud.cn，填写m。

</WRAP>

### 文件上传

文件验证需要注意，进行验证访问的链接地址是
<https://domain+/.well-known/pki-validation/+fileauth.txt> 或者
<http://domain+/.well-known/pki-validation/+fileauth.txt>
文件内容结尾不能有回车或换行符。

<wrap em>文件验证不支持任何形式的跳转，需要直接响应200状态码和文件内容。</wrap>

举例： domain为 www.ucloud.cn; authKey为fileauth.txt，那么需要访问：
<https://www.ucloud.cn/.well-known/pki-validation/fileauth.txt获取到文件内容（authValue）201704181133503c8morpl4g9gk5naytt4dmfwpw50pokoie4d4vjoy259gmbfai则为验证成功>

<wrap em>文件内容请根据系统实际分配的进行保存。</wrap>

## Step5：等待10分钟左右

等待大概10分钟的时间，然后刷新控制台，看到状态变为“已颁发”，操作中出现【下载】按钮后，即可下载证书使用。

DV证书验证中出现问题，可以通过[工具自查](ussl/faq/dv)原因。

## Step6：下载证书&部署

在控制台中下载证书后就可以在自己的服务器中部署证书了，部署证书可参考[帮助文档](ussl/install)。
