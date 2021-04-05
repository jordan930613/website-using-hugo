---
title: "Java ThreadPoolExecutor 學習 20210315"
date: 2021-04-05T18:15:52+08:00
author: "Johnson"
---

###### tags: `Java`

Java提供了ThreadPoolExecutor，讓我們可以客製化自己的ThreadPool

```
public ThreadPoolExecutor(int corePoolSize, 
                            int maximumPoolSize, 
                            long keepAliveTime,
                            TimeUnit unit,    
                            BlockingQueue     
                            workQueue,
                            RejectedExecutionHandler handler)
```
* 參數介紹：
    1. corePoolSize，定義最少的執行緒數量。
    2. maximumPoolSize，定義最大執行緒數量。
    3. keepAliveTime，定義執行緒閒置後存活的時間，回收的執行緒不一定是回收一開始corePoolSize所產生的執行緒。
    4. unit，定義keepAliveTime時間單位。
    5. workQueue，定義Task在Queue中的等待形式。 

* 程式執行流程：
    1. 假設定義corePoolSize = 3, maximumPoolSize = 6, workQueue大小設爲10。
    2. 當加入20個任務時，首先會執行1,2,3，因爲corePoolSize = 3，4...13會被加到workQueue裡，當workQueue塞不下後，因爲maximumPoolSize值還未達到，所以這時會增加剩下的三個Thread讓14,15,16執行，剩下的17...20則會被reject掉


* 以上參考來源：
    1. https://www.aiwalls.com/java%E7%B7%A8%E7%A8%8B%E6%95%99%E5%AD%B8/25/9298.html
    2. https://yu-jack.github.io/2019/02/19/java-executor/



