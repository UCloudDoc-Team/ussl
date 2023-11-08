

# 验证身份

购买证书后必须补全信息才能完成证书申请。

<wrap em>注意填写正确的手机号和邮箱，审核人员将会通过手机号和邮箱与您联系。</wrap>

## DV 类型证书

验证方式可以选择DNS验证或者文件上传

### DNS验证

![](/images/operate/dnsyz.png)

**验证类型**：DNS

**记录类型**：CNAME

**绑定的域名**：显示补全信息时填写的域名

**CNAME主机记录**：根据域名返回的唯一的CNAME主机记录。

**CNAME记录值**：根据域名返回的唯一的CNAME记录值，请到您的DNS服务商处尽快添加CNAME记录。

<wrap em>请尽快于 24 小时内手动设置 DNS 解析记录，通过后 20
分钟内即可签发证书，超时将导致申请失败。</wrap>

在DNS服务商比如DNSPOD添加主机记录

![](/images/operate/dnsyz2.png)






### 文件验证

![](/images/operate/wjyz.png)

**1、创建文件**： 文件验证方式一般需要您的站点管理人员进行操作，先创建C5704CE6BB76F223420F371E8346A609.txt，并将验证的文件文件内容粘贴在文件中进行保存。

**2、创建目录**： 在站点的根目录下创建.well-known/pki-validation子目录。注意第一层目录是带点的隐藏目录，Windows下命令为：m".well-known"。将创建的文件放在该子目录中； 如果你的站点由于某种原因无法创建隐藏目录，选择其他DNS验证方式。

**3、配置监测**

<wrap em>（1）HTTPS配置检验链接：https://domain+/.well-known/pki-validation/C5704CE6BB76F223420F371E8346A609.txt</wrap>

<wrap em>（2）HTTP配置检测链接：http://domain+/.well-known/pki-validation/C5704CE6BB76F223420F371E8346A609.txt</wrap>

domain+为您的域名文件，内容结尾不能有回车或换行符。 文件验证不支持任何形式的跳转，需要直接响应200状态码和文件内容。


### 解析校验

**手动解析**：手动解析可以帮助客户确认添加的解析是否正确
    
 本地客户端shell命令验证，nslookup -q=CNAME 文件记录.主域名      
    
![](/images/procedure/cname手动解析验证.png)


证书吊销使用txt验证的订单，命令使用nslookup -q=TXT 主机记录.主域名
   


## OV / EV 类型证书

需要通过填写确认函上传给我们，由人工进行审核派发证书。

1\. 下载确认函

2\. 填写确认函

3\. 确认函<wrap em>打印并盖章，生成扫描件（拍照也可，请确保清晰）后到控制台上传</wrap>

4\. 我们尽快进行审批处理

5\. 审批通过后则可以下载证书，我们将短信、邮件通知申请人。
