---
title: CRLF和LF 导致的问题
---

### 首先CF LF是什么?

CR：Carriage Return  即“回车”
LF：Line Feed 即“换行” 

### 导致的问题

有时候执行php脚本会出现这个问题#/usr/local/php/bin/php^M
uinx的文件在windows打开变成一行（目前win10没有发现这个问题）

### 原因

主要是由windows与linux的换行符不一致导致的
linux的换行符为 LF \n windows的换行符为 CRLF \r\n

### 解决办法

使用编辑器切换换行符为LF保存文件即可解决

具体参考: [https://www.jianshu.com/p/ec9564fe1c2b](https://www.jianshu.com/p/ec9564fe1c2b)