

# 如何验证域名所有权

申请域名型证书时，系统需通过以下方式验证域名的所有权

1.管理员邮箱验证

系统会向你选择的管理员邮箱 发送验证邮件，能够收到验证邮件

并点击邮件中验证链接 即可完成验证。

域名管理员邮箱须符合以下任意规则：

1.域名 whois 管理联系人邮箱

2.域名 whois 技术联系人邮箱

3.默认管理员前缀的邮箱：

``` 
   admin@domain.com
   administrator@domain.com
   hostmaster@domain.com
   webmaster@domain.com
   postmaster@domain.com 
```

2.DNS验证

通过解析指定的DNS记录验证域名所有权

例如 （linux系统下面） dig www.ucloud.cn txt; (windows下面) nslookup www.ucloud.cn
txt

若能检测到 并且与指定的值匹配 则最多等候10分钟可完成域名所有权验证。

<WRAP round box>

如果域名存在CNAME解析 需要特殊处理一下

在主机名前端加\_dnsauth

配置 域名 \_dnsauth.www.demo.com， TXT记录值为 系统返回的txt记录值 </WRAP>

3.文件验证

通过在域名根目录下创建指定的文件验证域名所有权

例如：创建文件 irmvo302.htm 文件内容 NtdutxbskfhWvP3OffXW

系统会定时尝试访问 <http://xxx.domain/irmvo302.htm> 这个文件,若能访问到 并且内容匹配即可完成域名所有权验证。
