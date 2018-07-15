---
title: diy-arduino-uno
tags: electronica
---

# Arduino的DIY筆記(1)-安裝bootloader
=============================

在使用過一陣子Arduino的板子過後，難免會想要自己DIY出一塊獨一無二的Arduino，原因有很多種，一、因為自己製作的Arduino比較便宜，弄壞了比較不心疼；二、自己做得比較有感覺，而且可以搭配不同自己所需要的電路來設計；三、Arduino還是太大塊了，有些功能根本不需要，想要自己做出一個很小的。但是對於我而言，我最主要的理由還是”我只是單純的想要DIY”。

不管你的原因是什麼，接下來就開始介紹怎麼DIY吧

[![](http://2.bp.blogspot.com/-Bq6g2PSpZgI/UB_cT4xO4sI/AAAAAAAAAJU/kZ1BjjoDGzM/s400/DSCN8906.JPG)](http://2.bp.blogspot.com/-Bq6g2PSpZgI/UB_cT4xO4sI/AAAAAAAAAJU/kZ1BjjoDGzM/s1600/DSCN8906.JPG)

這篇適合的對象：目前有一塊Uno的玩家+剛好手邊有一大堆ATmega8  
DIY電路板所需要的部份

1.  電烙鐵
2.  銲錫
3.  洞洞板，你會將零件焊接在這上面(有黃色或是綠色那種，黃色很便宜，綠色版貴很多)

電源部分：

[![](http://4.bp.blogspot.com/-mbhUEt9lgKc/UB_nENECtkI/AAAAAAAAAKM/MLl2LgVxL1w/s400/power.jpg)](http://4.bp.blogspot.com/-mbhUEt9lgKc/UB_nENECtkI/AAAAAAAAAKM/MLl2LgVxL1w/s1600/power.jpg)

主要使用7805去得到穩定5V的電源，幫大家找了一下電路圖

[http://www.hyivs.tnc.edu.tw/pic/course1/7805%E9%9B%BB%E6%BA%90%E9%9B%BB%E8%B7%AF\_Page\_1.jpg](http://www.hyivs.tnc.edu.tw/pic/course1/7805%E9%9B%BB%E6%BA%90%E9%9B%BB%E8%B7%AF_Page_1.jpg)

1.  9V電源連接頭— 一個
2.  開關—一個
3.  0.1uf電解電容—兩個
4.  47uf電解電容—一個
5.  二極體1n4003—一個
6.  LED—一個
7.  220歐姆電阻—一個
8.  IC 7805—一個

以上是電源的部份，按照上面的電路可以輸出穩定的5V，是為了提供給arduino電源，當然你也可以直接拿電池搭配電阻硬生生去弄出5V的電源，但是那樣是非常不建議的，雖然我最初玩8051自走車的時候也的確是這麼做，因為當時並不知道有IC 7805，因此直覺就是拿電阻去配出5V的電源，因為以前國中上課的時候也只知道分壓定理，但現在看過這篇文章知道了，就盡量不要這麼做，這麼做的缺點是電壓不穩定，而且電池會隨著電力的消耗而降低伏特數，你總不可能每次都拿電表加上可變電阻在那邊調阿調的，永遠都調不到5V，而7805可以讓你直接使用大於5V以上的電源進來，然後輸出標準5V的輸出電源，只要你提供約6.5V~12V左右的電源，就通通變成5V給你，多好用阿，剩下的部份就會藉由發熱來散失，因此也不要給過大福特的電源，除了沒效率，還會讓7805增加燒壞的可能性。  
Arduino本身

[![](http://3.bp.blogspot.com/-HJKsns3zqms/UB_nAw7ubkI/AAAAAAAAAJ8/00xdGb437RU/s400/arduino.jpg)](http://3.bp.blogspot.com/-HJKsns3zqms/UB_nAw7ubkI/AAAAAAAAAJ8/00xdGb437RU/s1600/arduino.jpg)

首先先介紹一下我參考過的網站，沒有他們就沒有今天這塊DIY板子了~

[Cooper Maa](http://coopermaa2nd.blogspot.tw/)

[ARDUINO DIY](http://arduino-diy.blogspot.tw/)

[http://arduino-diy.blogspot.tw/2009/10/whats-arduino.html#more](http://www.blogger.com/%20%20http://arduino-diy.blogspot.tw/2009/10/whats-arduino.html#more)

首先Arduino其實就是使用AVR的IC製作出來的，仔細看看自己的Uno上面，寫的就是ATmeaga328，那到底和AVR差別在哪裡？據我目前所知，AVR是必須經過ISP燒錄線才能將程式燒錄進去的，但是很奇怪的是我們在使用Arduino從來沒有聽說過有這條線，但仔細看看下圖，reset按鈕旁邊有六個pin腳，從來沒有使用過，上面寫著ICSP，不小心google一下才知道，icsp = In-circuit serial programming 就是所謂的ISP線上燒錄的意思。  
當然如果你想要更加了解什麼是 icsp 線上燒錄，我找到網路上有位露天賣家rushoun寫的文章，個人覺得寫的挺詳細的，給大家參考看看。

[http://rushoun.myweb.hinet.net/PIC/ICSP%20Programmer.htm](http://rushoun.myweb.hinet.net/PIC/ICSP%20Programmer.htm%20)

[![File:Arduino Diecimila.jpg](http://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Arduino_Diecimila.jpg/800px-Arduino_Diecimila.jpg)](http://upload.wikimedia.org/wikipedia/commons/1/17/Arduino_Diecimila.jpg)

那不說AVR，Arduino到底有什麼樣的神力？我們不需要透過isp線即可燒錄程式？關鍵在於他在賣給大家之前已經燒錄了一個程式進去，他叫做”bootloader”，有了這個東西之後，你只需要使用USB線就可以燒錄囉，對於DIY來說這是一個嚴重的問題，因為我們剛買來的ATmega8毫無疑問根本沒有bootloader………  
沒有bootloader….就沒辦法製作arduino，但是要燒錄bootloader這個程式就一定得要有isp線才可以，難道我還得花一筆錢去買isp線嗎？這樣不是反倒花了更多錢，幸好，你有了這塊Uno，坦白說我後來才體會到Uno是一塊多划算的板子，他可以偽裝成ISP線幫你燒錄bootloader，而且你也不用去網路上慢慢找bootloader在哪邊了，就在arduino的exe檔裡面。

在Cooper Maa的網站裡面，這篇有教學

[http://coopermaa2nd.blogspot.tw/2011/03/arduino-avr-ispin-system-programmer-2.html](http://coopermaa2nd.blogspot.tw/2011/03/arduino-avr-ispin-system-programmer-2.html)  
你得準備好幾條單心線，還有要準備燒錄的ATmega8

1.22pf的電容

2.16MHz的石英震盪器

3\. 10K歐姆的電阻

圖上面顯示的ATmega168換成ATmega8

[![](http://3.bp.blogspot.com/-mg9iaJnLF8c/UF3f8yHAvII/AAAAAAAAAQo/J-cs6bnjoEs/s640/2012-09-22_234654.jpg)](http://3.bp.blogspot.com/-mg9iaJnLF8c/UF3f8yHAvII/AAAAAAAAAQo/J-cs6bnjoEs/s1600/2012-09-22_234654.jpg)

接著把你的Uno插上電腦，先依照下圖給他下載ArduinoISP的程式

[![](http://1.bp.blogspot.com/-AIiXcpHV1t4/UB_uQb95toI/AAAAAAAAAKg/d3CXBfrAC-M/s1600/1.jpg)](http://1.bp.blogspot.com/-AIiXcpHV1t4/UB_uQb95toI/AAAAAAAAAKg/d3CXBfrAC-M/s1600/1.jpg)

[![](http://2.bp.blogspot.com/-R-XeRmvTaUg/UB_uQ6Zhb8I/AAAAAAAAAKo/NoW2uay0z8A/s1600/2.jpg)](http://2.bp.blogspot.com/-R-XeRmvTaUg/UB_uQ6Zhb8I/AAAAAAAAAKo/NoW2uay0z8A/s1600/2.jpg)

燒錄ArduinoISP在Uno成功之後，接著到Tools那邊準備開始進行燒錄，這邊特別注意，Serial Port的部份還是要選擇在Uno的port上面。

選擇最下面的 Arduino NG or older w/ ATmega8

[![](http://1.bp.blogspot.com/-AHuyINcF8BE/UB_vTEij8uI/AAAAAAAAAKw/UHoj-JGIEKU/s1600/3.jpg)](http://1.bp.blogspot.com/-AHuyINcF8BE/UB_vTEij8uI/AAAAAAAAAKw/UHoj-JGIEKU/s1600/3.jpg)

接著下一步選擇Arduino as ISP

[![](http://3.bp.blogspot.com/-YNnJVjpaieE/UB_vTbDzfQI/AAAAAAAAAK4/R8x5-thhdSQ/s1600/4.jpg)](http://3.bp.blogspot.com/-YNnJVjpaieE/UB_vTbDzfQI/AAAAAAAAAK4/R8x5-thhdSQ/s1600/4.jpg)

最後按下 Burn Bootloader 就會開始進行燒錄囉。

[![](http://4.bp.blogspot.com/-NZgYoX-zoXM/UB_vT2K2J8I/AAAAAAAAALA/0IUDCyO7DOI/s1600/5.jpg)](http://4.bp.blogspot.com/-NZgYoX-zoXM/UB_vT2K2J8I/AAAAAAAAALA/0IUDCyO7DOI/s1600/5.jpg)

最後就會出現一串成功訊息，就表示燒錄完成了~  
今天就先到這邊吧，這邊額外提醒大家，在最後這一個步驟裡面，可能會一直不斷的發生問題，導致無法燒錄，我自己在這邊就卡關了好久，後來才發現是我的ATmega8有點問題，換了一塊之後就沒事了，如果有發生什麼其他奇怪的問題，歡迎大家一起在下面討論吧。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/arduino%e7%9a%84diy%e7%ad%86%e8%a8%981-%e5%ae%89%e8%a3%9dbootloader/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=185&action=edit)

# Arduino的DIY筆記(2)-Max232
=======================

[![](http://3.bp.blogspot.com/-vtrionslCuk/UB_nCNuQVXI/AAAAAAAAAKE/DyK1M222tbE/s400/max232.JPG) ](http://3.bp.blogspot.com/-vtrionslCuk/UB_nCNuQVXI/AAAAAAAAAKE/DyK1M222tbE/s1600/max232.JPG)

費了不少了力氣總算完成了Arduino的bootloader，那麼接著我們該怎麼樣用USB燒錄程式進去呢？

由於我目前不會自己製作USB轉RS232的接頭，因此我直接去買了一個來使用，假如你不想購買這個接頭，那可以燒錄程式進去Arduino裡面嗎？也還是可以的，目前一般的桌上型電腦還會有RS232的port，直接接上去也可以燒錄。

今天這篇主要介紹的部分是將電腦的rs232 level 轉換成 TTL level ，然後藉由那兩根TX和RX來傳輸我們的程式，而這件事情直接使用簡單的電路就可以做到，甚至還有專門的IC來為我們做好這件事情，他就是MAX232。

我剛畫好的電路圖如下

[![](http://4.bp.blogspot.com/-eQkbxQHCYug/UN64PGHjplI/AAAAAAAAAVQ/Ckje5I8eAAE/s640/rs232.jpg)](http://4.bp.blogspot.com/-eQkbxQHCYug/UN64PGHjplI/AAAAAAAAAVQ/Ckje5I8eAAE/s1600/rs232.jpg)

下面這份是相對應的電路圖

[http://www.amobbs.com/thread-4663228-1-1.html](http://www.amobbs.com/thread-4663228-1-1.html)

![](http://cache.ourdev.cn/bbs_upload782111/files_38/ourdev_629325YVMK5B.jpg)  
在燒錄的過程中，如果pin4沒有接上我圖中的那條白線和一顆10uF的電容，那麼你在燒錄的時候就必須手動Reset才能燒錄，因此還是建議接一下比較OK囉。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/arduino%e7%9a%84diy%e7%ad%86%e8%a8%982-max232/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=200&action=edit)