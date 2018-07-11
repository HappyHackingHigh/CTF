3 概述

socat，是linux下的一個工具，其功能與有“瑞士軍刀”之稱的netcat類似，不過據說可以看做netcat的加強版。的確如此，它有一些netcat所不具備卻又很有需求的功能，例如ssl連接這種。nc可能是因為比較久沒有維護，確實顯得有些陳舊了。

# 安裝

Ubuntu:sudo apt-get install socat

也可以去官網下載源碼包socat

基本語法
```
socat [options] <address> <address>
```

其中這2個address就是關鍵了，如果要解釋的話，address就類似於一個檔描述符，socat所做的工作就是在2個address指定的描述符間建立一個pipe用於發送和接收資料。

那麼address的描述就是socat的精髓所在了，幾個常用的描述方式如下：
```
-,STDIN,STDOUT ：表示標準輸入輸出，可以就用一個橫杠代替，這個就不用多說了吧….
/var/log/syslog : 也可以是任意路徑，如果是相對路徑要使用./，打開一個檔作為資料流程。
TCP:: : 建立一個TCP連接作為資料流程，TCP也可以替換為UDP
TCP-LISTEN: : 建立TCP監聽埠，TCP也可以替換為UDP
EXEC: : 執行一個程式作為資料流程。
以上規則中前面的TCP等都可以小寫。
```

在這些描述後可以附加一些選項，用逗號隔開，如fork，reuseaddr，stdin，stdout，ctty等。
```
socat當cat


socat - -
cat文件

1
socat - /home/user/chuck
寫文件

1
echo "hello" | socat - /home/user/chuck
socat當netcat
連接遠端埠

1
2
nc localhost 80
socat - TCP:localhost:80
監聽埠

1
2
nc -lp localhost 700
socat TCP-LISTEN:700 -
正向shell

1
2
nc -lp localhost 700 -e /bin/bash
socat TCP-LISTEN:700 EXEC:/bin/bash
反彈shell

1
2
nc localhost 700 -e /bin/bash
socat tcp-connect:localhost:700 exec:'bash -li',pty,stderr,setsid,sigint,sane
代理與轉發
將本地80埠轉發到遠端的80埠

1
socat TCP-LISTEN:80,fork TCP:www.domain.org:80
其他
其實從這裡才是重點

SSL連接
SSL伺服器

1
socat OPENSSL-LISTEN:443,cert=/cert.pem -
需要首先生成證書檔

SSL用戶端

1
socat - OPENSSL:localhost:443
fork伺服器
接下來這個例子，就是我認識socat的原因，可以將一個使用標準輸入輸出的單進程程式變為一個使用fork方法的多進程服務，非常方便。

1
socat TCP-LISTEN:1234,reuseaddr,fork EXEC:./helloworld
不同設備的通信
將U盤進行網路共用

1
socat -d -d /dev/ttyUSB1,raw,nonblock,ignoreeof,cr,echo=0 TCP4-LISTEN:5555,reuseaddr
-d -d 指的是調試信息的級別

將終端轉發到COM1

1
socat READLINE,history=$HOME/.cmd_history /dev/ttyS0,raw,echo=0,crnl
socat還有個readbyte的option，這樣就可以當dd用了。

小結
因為在Linux/UNIX中，一切都是檔，無論是socket還是其他設備。所以從理論上來說，一切能夠在檔層級訪問的內容都可以成為socat的資料流程的來源，2個address可以任意發揮，能夠做到的事情還有很多。特別是其fork的功能，確實是netcat所不能比的。

參考文獻
借鑒的幾篇博文：

Some Useful Socat Commands

Socat: A very powerful networking tool

Socat Examples
```
