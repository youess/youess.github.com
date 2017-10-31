---
title: datetime与系统时间不一致
date: 2017-10-31 10:01:52
tags: [python, datetime]
---

在程序中使用datetime遇到的一个小问题，程序中`datetime.today()`出来的时间和shell中`date`不一致。程序中采用的UTC的时间，但是机器是`Asia/Shanghai`的。

**为什么暂时不明白**，多个人使用的服务器上暂时想不出为什么

解决思路：

1. 利用datetime模块里面的timezone进行改变

```
from datetime import datetime, timezone, timedelta

tz_delta = timedelta(hours=8)
tz = timezone(tz_delta)
today = datetime.now(tz).date()
```


2. 在脚本中直接加入环境变量TZ


```
import os
os.environ['TZ'] = 'Asia/Shanghai'
```
