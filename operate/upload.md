# 证书上传

USSL证书管理平台支持其他平台购买证书的一键上传上传和生命周期管理服务

## **操作如下：**

### 1、进入控制台的证书管理USSL页面 

![](/images/operate/证书管理页面.png)

### 2、点击上传证书按钮 ，自定义证书名称 

![](/images/operate/上传证书页面.png)

### 3、证书上传

**普通格式**

证书文件包含：公钥：public.crt、私钥：private.key、ca证书链：CA.crt；请按照下图指引进行上传
![](/images/operate/证书文件选择.png)

**pem格式**

证书文件包含：公钥+ca证书链：public.pem、私钥-private.key；请按照下图指引进行上传
![](/images/operate/pem格式上传.png)

### 4、上传完成

上传成功的证书，平台将自动获取到证书域名、签发机构、有限时间；从证书类型及状态可判断是否为上传证书，如图所示
![](/images/operate/上传成功.png)












