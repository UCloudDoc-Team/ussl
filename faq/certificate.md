

# 证书格式的区别

## 根据web服务软件选择

**Tomcat**、**Weblogic**、**JBoss等**，使用Java提供的密码库。通过Java的Keytool工具，生成Java
Keystore（JKS）格式的证书文件。

**Apache**、**Nginx等**，使用OpenSSL提供的密码库，生成PEM、KEY、CRT等格式的证书文件。

此外，IBM的产品，如**Websphere**、**IBM Http
Server（IHS）等**，使用IBM产品自带的iKeyman工具，生成KDB格式的证书文件。

微软Windows Server中的**Internet Information
Services（IIS）**，使用Windows自带的证书库生成PFX格式的证书文件。

## 根据证书后缀名选择

**DER、CER** : 这样的证书文件是二进制格式，只含有证书信息，不包含私钥。通常只保存公钥。

**CRT** : 二进制格式或者文本格式，适合Apache、Nginx等使用

**PEM** : 一般是文本格式，可以放证书或私钥，或者两者都包含。 \*.PEM如果只包含私钥，那一般用
\*.KEY代替。适合Apache、Nginx等使用

**PFX**、\*\* P12\*\* 是二进制格式，同时含证书和私钥，一般有密码保护。适用于微软的IIS。

**JKS** ： 适用于Tomcat、weblogic、JBoss等
