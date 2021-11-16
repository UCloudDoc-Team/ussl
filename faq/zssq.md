

# 为App部署SSL证书 应对苹果ATS限制

2021年12月1日起， 使用文件验证(HTTP)的域名 只能为被验证域名本身签发证书，不支持签发通配符证书和其下级子域名证书

1、 目前，行业允许仅对主域名(domain.com)进行域名验证即可，适用于通配符证书(如\*.domain.com或\*.sub.domain.com等)和其下级所有子域名(如sub.domain.com或sub2.sub1.domain.com等)。

2、 DigiCert将在2021年11月15日后，对于使用文件方式验证的域名，只能为被验证域名本身签发证书。如 使用文件验证方式验证域名domain.com，则只能为domain.com签发证书，不能为\*.domain.com 或sub.domain.com 签发证书。

3、DNS验证和邮箱验证方式则不受影响，建议优先使用DNS或邮件验证方式。

DigiCert 公告: https://knowledge.digicert.com/alerts/domain-authentication-changes-in-2021.html

GlobalSign公告：https://www.globalsign.com/en/blog/upcoming-changes-publicly-trusted-tls-certificates