
# 企业型(OV)/增强型(EV)证书购买签发流程
    
    总结：购买证书->补全信息->上传公司盖章确认函->后台公司信息审核->域名验证（DNS/文件验证）->签发证书
    

## Step1：新购证书

ucloud首页-\>控制台-\>全部-\>证书管理 USSL\>购买证书

![](/images/rk1.png)

![](/images/rk2.png)

![](/images/xzzs.png)

详细内容参见[购买证书](/ussl/operate/buy)介绍。

## Step2：补全信息

   购买后会看到生成了一条没有任何信息的待补全信息的证书，点击【补全信息】填写内容提交。

![](/images/procedure/待补全信息.png)

详细内容参见[补全信息](ussl/operate/complete)介绍。

## Step3：上传公司盖章确认函

### 附件信息（OV、EV证书）

OV、EV证书完成基础信息填写后，需完善附件信息上传，该步骤主要验证您的组织（企业）信息，根据不同CA中心，需提供附件分为以下两类（提交一类附件信息即可）

**确认函**

下载确认函附件表，填写相关信息后上传即可。

![](/images/qrh1.png)

![](/images/qrh2.png)

**申请资料**

需依次证书申请表、服务协议表、营业执照复印件、身份证正反面等信息

![](/images/sqzl1.png)

![](/images/sqzl2.png)

## Step4：公司信息人工审核（后台，客户无需操作，只需等待）

申请提交后CA中心将在3至7个工作日内完成审核，不同CA中心审核周期会有所区别。审核期间我们将电话、邮件联系申请人，请届时配合我们的审核。审核通过后我们会短信、邮件通知申请人。

**CA中心审核**

订单状态为待CA人工审核后，系统会自动发送域名确认邮件至相关联系人邮箱，请及时登录域名所有权邮箱或管理员邮箱进行邮件批准。

域名确认邮件批准后，订单联系人电话保持畅通，接听审核部电话。

<wrap em>注意，此处需要确认邮件，请注意查收邮箱中的邮件，有时候可能会在垃圾邮件中。</wrap>

**审核通过**

我们将邮件、短信通知申请人，接到通知后可上控制台下载证书开始使用。

**审核不通过**

我们将邮件、短信通知申请人，控制台上证书状态变为审核失败，需要重新补全信息、重新上传确认函。



## Step5：域名所有权验证

### 域名验证方式一：DNS解析验证

**1）、点击验证按钮**


![](/images/procedure/验证按钮.png)

**2）、获取验证信息**

![](/images/operate/dns验证.png)

**3）、填写验证信息**

    在域名解析平台或DNS服务商（如DNSPOD）新增域名解析，样例如下：

![](/images/operate/DNS解析配置.png)

**4）、解析验证**

    方法一：控制台自动化工具检测，点击验证按钮，显示匹配则解析添加成功
   
![](/images/operate/解析验证.png)
    
    方法二：本地客户端shell命令验证，nslookup -q=TXT __dnsauth.域名
    
![](/images/operate/手动解析.png)
   



### 域名验证方式二：文件验证（与服务器本身安全配置相关，容易出现验证不匹配的情况）



1、根据验证路径创建文本文件fileauth.txt，并输入txt值，文件内容结尾不能有回车或换行符

2、保证文件fileauth.txt路径与验证一致，可自行补齐


3、纪录值验证，浏览器访问<https://domain+/.well-known/pki-validation/+fileauth.txt> 或者<http://domain+/.well-known/pki-validation/+fileauth.txt>；并获取到对应的txt值，则表示文件解析添加成功


**举例：** 

domain为 www.ucloud.cn; authKey为fileauth.txt，访问：<https://www.ucloud.cn/.well-known/pki-validation/fileauth.txt>

获取到文件内容（authValue）201704181133503c8morpl4g9gk5naytt4dmfwpw50pokoie4d4vjoy259gmbfai则为验证成功


## Step6：证书颁发

完成以上步骤，恭喜您证书申请成功，您可下载对应证书文件部署到服务器。

![](/images/zsbf1.png)

![](/images/zsbf2.png)

证书部署详细内容参见[证书部署](/ussl/install/nginx)介绍。

**备注：**`因为域名型(DV)的验证信息是通过签发系统自动扫描签发的，不能实现100%成功签发，若24小时之内没有签发，为保障使用，请换成升级为OV证书。`

域名验证信息配置是否有效，请通过下面在线工具自助检测：
<https://myssl.com/dns_check.html#ssl_verify>
