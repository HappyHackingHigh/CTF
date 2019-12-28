#  WebSecurity Learning Path(網站安全學習地圖)

```
[高階課程:臺灣好厲駭培訓]Topic: web-security
```
#### 進階課程HackingWeekend
```
[進階課程hackingWeekend]Web hacking and exploitation
Web Security and the OWASP Top 10
>* 1~3天課程視需求動態調整內容
>* 主要講解與實測OWASP Top 10的各種漏洞及其攻擊技術
   (如果時間許可,建議說明各種安全機制及其bypass攻擊技法)
>* 需示範使用DVWA, Webgoat,... 漏洞平台進行測試
>* 需示範講解WebCTF數題題目
>* 須確定教學環境是否設備OK??
>* 上課配套{教學環境:WebCTF.ova}包含底下的漏洞平台
       OWASP Mutillidae | OWASP Juice Shop | WebGoat | DVWA
>* 上課配套{CTF平台:WebCTF}上課前會提供網址

>* 需上過[基礎入門HappyhackingDay]MyFirstWebSecurity
   (我的第一堂網站安全課)或已經熟悉相關主題
>* 需上過CTF搶旗大賽(基礎入門)(FromLinuxToCTF)或略懂linux
```
#### 基礎入門HappyHackingDay
```
[基礎入門HappyhackingDay]MyFirstWebSecurity(我的第一堂網站安全課)
>* 3小時課程
>* 了解HTTP協定
>* 熟悉網站安全測試工具:developer Tools, Curl與Burpsuite
  (若有時間可示範OWASP Mantra或HackingBar)
>* 完成Web-CTF101的六題題目
```
# Web hacking and exploitation:OWASP Top 10

>*　進階課程hackingWeekend：：Web Security and the OWASP Top 10
>* 1~3天課程==>視需求動態調整內容
>* 主要講解與實測OWASP Top 10的各種漏洞及其攻擊技術
   (如果時間許可,建議說明各種安全機制及其bypass攻擊技法)
>* 需示範使用DVWA, Webgoat,... 漏洞平台進行測試
>* 需示範講解WebCTF數題題目

>* 須確定教學環境是否設備OK??
>* 上課配套{教學環境:WebCTF.ova}包含底下的漏洞平台
       OWASP Mutillidae | OWASP Juice Shop | WebGoat | DVWA
>* 上課配套{CTF平台:WebCTF}上課前會提供網址

上課學員要求：
>* 需上過[基礎入門HappyhackingDay]MyFirstWebSecurity
   (我的第一堂網站安全課)或已經熟悉相關主題
>* 需上過CTF搶旗大賽(基礎入門)(FromLinuxToCTF)或略懂linux


## 網站十大類型漏洞：OWASP TOP 10(2017)
```
認識網站十大類型漏洞：OWASP TOP 10(2017)
https://www.owasp.org/index.php/Top_10-2017_Top_10

A1:2017-Injection
A2:2017-Broken Authentication
A3:2017-Sensitive Data Exposure
A4:2017-XML External Entities (XXE){新增}
A5:2017-Broken Access Control
A6:2017-Security Misconfiguration
A7:2017-Cross-Site Scripting (XSS)
A8:2017-Insecure DeserializationP{新增}
Insecure deserialization often leads to remote code execution.
A9:2017-Using Components with Known Vulnerabilities
A10:2017-Insufficient Logging&Monitoring{新增}
```
### A1:2017-Injection實戰sql injection
```
完成DVWA/SQL Injection:from low to high
```
```
完成web-CTF
```

### 實戰blind sql injection

```
完成DVWA/SQL Injection (Blind):from low to high
```

### 實戰A2:2017-Broken Authentication

```
完成DVWA/Insecure CAPTCHA:from low to high
```

### A3:2017-Sensitive Data Exposure
```
```

### A5:2017-Broken Access Control實戰LFI(Local File Inclusion)漏洞

```
完成DVWA/File Inclusion:from low to high
```

### 實戰A6:2017-Security Misconfiguration
```
完成bwapp/
```

### 實戰A7:2017-Cross-Site Scripting (XSS)

```

```
### 實戰A9:2017-Using Components with Known Vulnerabilities
```
使用OWASP MutillidaeII(2018-03-12::2.6.60版)
https://sourceforge.net/projects/mutillidae/files/
Web Pen Testing Instructional Videos: http://www.youtube.com/user/webpwnized/
```
```
測看看下列OWASP MutillidaeII(2018-03-12::2.6.60版)
PHP MyAdmin Console
PHP Info Page
CBC-bit Flipping
SSL Misconfiguration
```

### 實戰A10:2017-Insufficient Logging&Monitoring
```
測看看OWASP MutillidaeII(2018-03-12::2.6.60版)

```

第一天課程結束

# 第二天課程

### 實戰A4:2017-XML External Entities (XXE)
```

```

### 實戰SSRF
```

```

### 實戰A8:2017-Insecure Deserialization{新增}
```

```

### 實戰SSTI
```

```

# MyFirstWebSecurity(我的第一堂網站安全課)

>* 基礎入門HappyHackingDay
>* 3小時課程
>* 了解HTTP協定
>* 熟悉網站安全測試工具:developer Tools, Curl與Burpsuite
  (若有時間可示範OWASP Mantra或HackingBar)
>* 完成Web-CTF101的六題題目

## Web-CTF101
```
請同學先登入網站註冊並實際看看Web-CTF101的題目
```

# A1:Developer Tools
```
https://developer.chrome.com/devtools

Chrome DevTools Masterclass
https://www.youtube.com/watch?v=KykP5Z5E4kA&t=2s

Debugging The Web (Chrome Dev Summit 2016)
https://www.youtube.com/watch?v=HF1luRD4Qmk

GoogleChrome/lighthouse
Auditing, performance metrics, and best practices for Progressive Web App
https://github.com/GoogleChrome/lighthouse
```

### A1_1:使用{developer Tools開發者工具}來查看網站應用程式的原始碼Web-CTF101

### A1_2:使用{developer Tools開發者工具}來解HITCON2017的Visual Acuity

http://ctf2017.hitcon.org/

![result](pic/HITCON2017.png)

### A2:認識robots.txt
```
https://zh.wikipedia.org/wiki/Robots.txt
```

### A2_1:解Web-CTF101那題robots.txt

## B.1.HTTP協定(1): Http request and response

```



```
### B.2.Curl

### B.2.1.使用Curl測試HTTP協定

### B.2.2.使用Curl解Web-CTF101/flashing redirect

### B.2.3.使用Curl測試HTTP方法==>解Web-CTF101/New Http Methond

### C.burp suite

### C.1.使用burp suite:HTTP封包攔截與竄改session


# 下一階段學習：Web hacking and exploitations

```
認識網站十大類型漏洞：OWASP TOP 10(2017)
https://www.owasp.org/index.php/Top_10-2017_Top_10
```

```
A1:2017-Injection

A2:2017-Broken Authentication

A3:2017-Sensitive Data Exposure

A4:2017-XML External Entities (XXE){新增}

A5:2017-Broken Access Control

A6:2017-Security Misconfiguration

A7:2017-Cross-Site Scripting (XSS)

A8:2017-Insecure DeserializationP{新增}
Insecure deserialization often leads to remote code execution.

A9:2017-Using Components with Known Vulnerabilities

A10:2017-Insufficient Logging&Monitoring{新增}
```

### D.先體驗一下：A1:2017-Injection

```
單單Injection的各種面向就可以講兩天：
SQL injection(SQLi)
NoSQL injection
Command injection(cmdi) 
XPATH injection
LDAP injection

現在先體驗看看什麼是SQL injection
```
### D.1.我的第一次SQL Injection

### D.2.我的第一次Command Injection

# 想要學習更多,記得一定要報上｛網站安全研習營｝的課

## HTTP協定(2):HTTP Authentication認證{網站安全研習營再講}


