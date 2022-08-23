

# 域名型(DV)证书购买签发流程

    流程总结： 新购证书->补全信息->域名验证（DNS/文件验证）->验证通过->签发证书


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

## Step3：域名所有权验证

### 域名验证方式一：DNS解析验证

**1）、点击验证按钮**

![](/images/procedure/验证按钮.png)

**2）、获取验证信息**

![](/images/procedure/cname验证信息.png)

**3）、填写验证信息**

    在UDNS域名解析平台或DNS服务商（如DNSPOD）新增域名解析，样例如下：

![](/images/procedure/cname解析添加.png)

**4）、解析验证**

    方法一：控制台自动化工具检测，点击验证按钮，显示匹配则解析添加成功
   
![](/images/procedure/Cname解析验证按钮.png)
    
    方法二：本地客户端shell命令验证，nslookup -q=CNAME 文件记录.主域名
    
![](/images/procedure/cname手动解析验证.png)
   



### 域名验证方式二：文件验证（与服务器本身安全配置相关，容易出现验证不匹配的情况）



1、根据验证路径创建文本文件文件名称，并输入文件内容，文件内容结尾不能有回车或换行符

2、保证文件名称路径与验证一致，缺少可自行补齐


3、纪录值验证，浏览器访问<https://domain+/.well-known/pki-validation/+文件名称> 或者<http://domain+/.well-known/pki-validation/+文件名称>；并获取到对应的txt值，则表示文件解析添加成功


**举例：** 

domain为 www.ucloud.cn; 访问：<https://www.ucloud.cn/.well-known/pki-validation/文件名称>获取到文件内容则为验证成功

![](/images/procedure/文件解析验证.png)


## Step4：证书签发

等待大概10分钟的时间，然后刷新控制台，看到状态变为“已颁发”，操作中出现【下载】按钮后，即可下载证书使用。

DV证书验证中出现问题，可以通过[工具自查](ussl/faq/dv)原因。

## Step5：下载证书&部署

在控制台中下载证书后就可以在自己的服务器中部署证书了，部署证书可参考[帮助文档](ussl/install)。

