

# 验证身份

购买证书后必须补全信息才能完成证书申请。

<wrap em>注意填写正确的手机号和邮箱，审核人员将会通过手机号和邮箱与您联系。</wrap>

## DV 类型证书

验证方式可以选择DNS验证或者文件上传

### DNS验证

![](/images/operate/dns验证.png)

**验证类型**：DNS

**绑定的域名**：显示补全信息时填写的域名

**主域名**：假如添加的域名是abc.test.ucloud.cn,主域名是ucloud.cn，也就是一级域名，格式为：一级域名.顶级域名

**TXT主机记录值**：根据域名返回的唯一的txt主机记录值，请到您的DNS服务商处尽快添加txt记录。

<wrap em>请尽快于 24 小时内手动设置 DNS 解析记录，验证通过后 20
分钟内即可签发证书，超时将导致申请失败。</wrap>

在DNS服务商比如DNSPOD添加主机记录

![](/images/operate/添加记录.png)



主机记录就是域名前缀，常见用法有：

@： 直接解析主域名 www.ucloud.cn 或者 ucloud.cn。

\*： 泛解析，匹配其他所有域名 \*.ucloud.cn。

mail： 将域名解析为mail.ucloud.cn，通常用于解析邮箱服务器。

二级域名： 如：abc.ucloud.cn，填写abc。

手机网站： 如：m.ucloud.cn，填写m。


### 文件上传

文件验证需要注意，进行验证访问的链接地址是
<https://domain+/.well-known/pki-validation/+fileauth.txt> 或者
<http://domain+/.well-known/pki-validation/+fileauth.txt>
文件内容结尾不能有回车或换行符。

<wrap em>文件验证不支持任何形式的跳转，需要直接响应200状态码和文件内容。</wrap>

举例： domain为 www.ucloud.cn; authKey为fileauth.txt，那么需要访问：
<https://www.ucloud.cn/.well-known/pki-validation/fileauth.txt获取到文件内容（authValue）201704181133503c8morpl4g9gk5naytt4dmfwpw50pokoie4d4vjoy259gmbfai则为验证成功>

<wrap em>文件内容请根据系统实际分配的进行保存。</wrap>

## OV / EV 类型证书

需要通过填写确认函上传给我们，由人工进行审核派发证书。

1\. 下载确认函

2\. 填写确认函

3\. 确认函<wrap em>打印并盖章，生成扫描件（拍照也可，请确保清晰）后到控制台上传</wrap>

4\. 我们尽快进行审批处理

5\. 审批通过后则可以下载证书，我们将短信、邮件通知申请人。
