---
title: quadrocopter
tags: robot
---

# 飛行蜘蛛(1)-前導文章
============

 今天主要和大家介紹我想要製作的機器人，在三月到八月這僅僅六個月的實習生時間中，我想要製作一些比較特別和好玩的機器人，因此選擇了一種比較新穎的機器人類型。 

蜜蜂機器人!!!!!(飛行型的機器人)

       製作到最後的目的是他能夠飛行在空中，執行一些任務，像是採蜜、建築蜂窩，能夠團體活動，並且同時自由自在的在不同地方執行不同的任務，以達到分工合作，互相協助的能力。

         一開始會想到做蜜蜂機器人的想法是來自於哆啦A夢，他有著竹蜻蜓可以到處飛，然後在地面上的時候還可以執行各種想要的任務。而且以避障的功能來說，不管地面環境多惡劣，例如像是樓梯，明顯高低差的桌面，這些都是一般的地面避障車不太能做到的，但是飛行機器人只要飛越過去就免除困難了。即使飛行機器人有許多優點，但是要製作出這樣的蜜蜂機器人也不是一件太容易的事情，為了不要讓這樣的事情化為空談，我必須來說明我要如何架構這樣的  “蜜蜂機器人”。

蜜蜂的致動器架構分別來自於飛行的翅膀和六隻可以爬行移動的腳，首先我得往這兩者去思考和簡化一些目前較難以達成的部分，像是人類最初在製作飛機的過程一樣，學習找到一種新的方法，去解決本來無法解決的問題。

翅膀：

要會飛就要有翅膀，但是目前能有多少飛機是像小鳥一樣拍拍翅膀就能飛行？因此我往直升機的方向去思考，他是一種比較特別的飛機，可以停懸在空中，但是據說，直升機的缺點就是無法上升到很高的高度，不過在小型的機器人上面我暫時可以不用考量這樣的問題，但是直升機的架構還是很複雜，有許多齒輪箱還有配重的問題得處理，而且在墜毀的時候的修機費用又相當的高，後來我找到一種新的替代品，他類似直升機，但是他的操作原理比較簡單好理解，配種問題比直升機更好解決，於是我就選擇了他

四軸飛行器!!!!!!!!!!!!!!!!!!!!!

![](http://2.bp.blogspot.com/-Bs7io1dawQg/T4Y1HvRwxcI/AAAAAAAAAEk/SBGK2DTR0y8/s1600/DSCN0011.JPG)

他是由四個螺旋槳組成的直升機，其鄰邊的螺旋槳轉向恰好不同，為了抵抗直升機的旋轉，只要藉由調整四顆馬達的轉速就可以飛行，而直升機則是調整螺旋槳的螺距、轉速和方向，這樣的優點對我來說是非常方便去製作蜜蜂機器人的。

\[http://www.youtube.com/watch?v=AZ7Xt2b61Us\]

六隻腳：

![](https://images1-focus-opensocial.googleusercontent.com/gadgets/proxy?url=http://ytimg.googleusercontent.com/vi/FmqFVDr0F8E/hqdefault.jpg&container=focus&gadget=a&rewriteMime=image/*&refresh=31536000&resize_w=402&no_expand=1)

蜜蜂利用他的腳去採花粉，那麼我的機器人該怎麼去處理這部分？

關於這部分我選擇使用類似六足機器人的架構，下方是隻機器蜘蛛，約有六隻到八隻腳可以移動，能夠使用這些腳去執行一些簡單的任務，例如撿拾球和寶特瓶。但是為了要輕量化，我還得在這部份多作些思考，要盡可能減少使用馬達的數量，否則四軸飛行器也是無法負荷。

Format [Chat](http://192.168.1.233/type/chat/)Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e8%a1%8c%e8%9c%98%e8%9b%9b1-%e5%89%8d%e5%b0%8e%e6%96%87%e7%ab%a0/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=314&action=edit)

# 飛行蜘蛛(2)-第一代架構
=============

雖然計劃快要結束了，但是為了以後有心想要玩四軸機或是四足機器人的夥伴們，我將會把這一次計畫的所有過程和做法和大家說明，或許之後我自己或是其他的MAKE or 愛DIY 的夥伴們看到這份文章，可以有新的體會和想法。  
最初想要設計的架構是使用RoBoard RB-100加上Razor 9DOF IMU做控制

[![RoBoard RB-100  圖片來自：http://www.roboard.com/index.htm](http://1.bp.blogspot.com/-kiliU-itAx0/UVhQ94FFczI/AAAAAAAAAuc/U1klRkAGXQA/s1600/RoBoardV2_1.jpg "RoBoard RB-100  圖片來自：http://www.roboard.com/index.htm")](http://1.bp.blogspot.com/-kiliU-itAx0/UVhQ94FFczI/AAAAAAAAAuc/U1klRkAGXQA/s1600/RoBoardV2_1.jpg)

DMP Roboard

[![](https://dlnmh9ip6v2uc.cloudfront.net/images/products/9/6/2/3/09623-01b_i_ma.jpg)](https://dlnmh9ip6v2uc.cloudfront.net/images/products/9/6/2/3/09623-01b_i_ma.jpg)

為什麼會選擇使用這兩者呢？

RoBoard RB-100 可以控制24軸的伺服馬達`，我之後使用的電子變速器和各種感測器都非常需要PWM訊號來控制，而一般的單晶片是無法達成這樣的事情，原因在於一般的單晶片程式執行速度不夠快，因此要精確、即時的去控制伺服馬達是無法單純用程式來彌補的，必須要在硬體方面多下點功夫。  
Razor 9DOF IMU，Inertial measurement unit，他其實就是具備了陀螺儀、加速度規和地磁儀，這三種合而為一的感測器，一般來說這種東西也只會被裝在飛機上面，但是近年來，智慧型手機也開始被裝上這樣的感測器，以達到各式各樣的人機互動效果。  
在我那台X400上面使用RoBoard RB-100作為主控板，然後利用這塊IMU來當作感測器，這樣不僅可以控制我的伺服馬達們，利用RB-100身為電腦的處理速度，應該可以順利完成任務吧。

我來說個關於我自己的小故事吧

有一次在上課，老師問同學：「我們上課教了這麼多種的感測器，現在假設要拿來製作植物工廠的感測器你應該要使用什麼溫度感測器來測量溫度呢？」

這問題在這邊不會有任何的解答，但是對於我來說，卻有個不是答案的特別想法

首先植物工廠是一個利用電腦來觀察植物和種植植物的一個系統，不同於傳統的種菜，還有溫室菜園，那些都偏向於使用農夫這樣人工的方式來種植，而植物工廠就是利用電腦來處理這些事情，什麼時候該澆水，灑肥料， 而這種方式種出來的菜比一般的還要貴，其實還不算是很普通的方式，所以在現階段這是一個模模糊糊的概念和不成熟的技術，但它是一個新的東西，並無法單純藉由以前學過多少感測器就知道該用什麼好。

在創造新的東西這樣的階段，當然過去的經驗和學習是十分重要的，但是新的想法是必須經過多次的嘗試才有可能得到一個適合的做法，而過去的經驗只是讓我們一開始稍微有個起頭，大概知道怎麼去做，並不是只要看看課本和感測器的datasheet，就能夠用數學的方式計算出最好的做法，甚至面對老師說的那個問題，或許目前真正適合的感測器根本沒有，需要我們再另外製作出來一個防水，抗髒的好感測器。

DIY的過程，Do it yourself，也就是在沒有專家和沒有特殊專業技術的情況下，我們還能夠利用我們已知的一些常識和能力去達成任務，雖然在過程中常常出包，但是這些錯誤嘗試的過程，就是讓我們學習創造的過程，而我第一代的架構的確受到某些因素影響而無法順利運作，但是身為一個DIY製作的玩家們，是不能因為失敗就氣餒的，因為我們要的就是這樣失敗的過程所帶來的快樂，當然，能夠成功也不錯=)

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e8%a1%8c%e8%9c%98%e8%9b%9b2-%e7%ac%ac%e4%b8%80%e4%bb%a3%e6%9e%b6%e6%a7%8b/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=323&action=edit)

# 飛行蜘蛛(3)-第二代架構
=============

當時在挑選馬達和電子變速器的時候，已經往更高POWER的方向去挑選，配出了一個也不算是小的四旋翼架構，但是後來發現，當我的飛機額外再裝上四顆金屬齒的伺服機後，竟然無法飛起來，原因當然是動力不夠，再加上我的電子變速器有過電流保護，以至於油門都打到底了，還是無法飛起來，甚至啟動斷電保護，直接關機。  
如果我再另外裝上RoBoard和那塊IMU不就連動都不能動？……..

面對這種情況有兩種解決方針

1.  加大所有馬力，馬達換成更高檔的，從本來的300塊錢一顆換成1200一顆電子變速器，20A的換成40A的，電池也加強威力。
2.  減輕重量，減輕材料的重量，將所有站體積和空間的東西都拆除。

因此最後我在這兩者之間做了一個決斷

先減輕材料，爾後再往加大馬力的方向前進，畢竟當時去買馬達的時候，老闆都和我說這顆馬達超猛，可以2秒向上衝十公尺，所以應該是我真的放太重了，之前拿隻摺疊傘都飛得上去了，所以我先閒置了RoBoard和IMU，而選擇比較輕薄的單晶片製作。

但是，別忘了，最初就說了用單晶片會有許多的問題得面對。

現在開始，當時以為沒有的問題就全部出來要面對了。

既然使用單晶片？要如何達到夠小？

甚至除了夠小之外，還得用起來夠方便和好用，而且不能是一個大錢坑

例如，買了XX就得再買YY才可以用，既然買了YY何不再買ZZ會更方便，結果本來XX的價格又不親民……..

DIY就是要自己製作的感覺，舉例來說，雖然說鑽洞這件事情我們可能會需要一支電鑽就好，你也可以畫好設計圖拿去工廠請專業的師傅幫你用，但是後者就會很花錢又沒有自己做到東西的感覺。

後來我選擇使用Arduino作為我的主要控制器，我之前有購買他的UNO板，用起來很順手，不昂貴，而且還可以自己DIY出自己想要的Arduino控制板，網路上還不少code、電路和各式各樣的文章提供給參考，這也是為什麼會有下面兩篇系列文。

*   Arduino的DIY筆記(1)-安裝bootloader
*   Arduino的DIY筆記(2)-Max232

這兩篇只是個開頭，將來會持續使用Arduino做各式各樣的計畫和專題，也會持續和大家分享這些資料。

選擇使用Arduino之後，一開頭我就遇到了兩個困難，第一個，PWM腳位只有四個，無法控制四足機器人，因為四足機器人每一足要三個伺服馬達， 第二個，程式的處理速度不夠快，因此要分別控制四旋翼和四足機器人是無法以目前單純的做法來達到的，為了要處理這兩件事情，我打算將這兩件事情先分工出去，之後再想辦法處理，或許這部分只要增加些電路或是修改程式就能夠處理的，我先將能不能動和能不能飛這兩件事情做結合，我將這兩件事情分工給  飛控板  和  伺服控制板。  
這是一個很恐怖的過程，因為完全不知道做出來到底能不能走，或是，能不能飛？

先來看個圖片吧，目前架構圖。

[![](http://2.bp.blogspot.com/-JDrlgwSIb70/UDslxqh7VNI/AAAAAAAAAPE/kuUQBtKau8U/s1600/DSCN9000.JPG)](http://2.bp.blogspot.com/-JDrlgwSIb70/UDslxqh7VNI/AAAAAAAAAPE/kuUQBtKau8U/s1600/DSCN9000.JPG)

本來打算使用RP製作骨架，結果發生了一些操作上的問題而失敗收尾，不過已經知道哪邊出包了，打算重新來過，正製作更輕的骨架，來取代鋁方管。

眼尖的各位應該可以看到我使用了一種更小的伺服馬達，9g伺服機，重量很輕，就是如名稱一樣的9公克，想必可以讓我減輕不少重量。

[![圖片來源：http://fireflyhobbies.co.za/index.php?main_page=product_info&products_id=260](http://fireflyhobbies.co.za/images/tower_pro_sg90.jpg "輝盛正廠Tower Pro SG90 9G伺服器")](http://fireflyhobbies.co.za/images/tower_pro_sg90.jpg)

輝盛正廠Tower Pro SG90 9G伺服器

[![](http://2.bp.blogspot.com/-uGboFTvkU2g/UDsl8OKRvdI/AAAAAAAAAP8/4aLlPHk2jNU/s1600/DSCN9007.JPG)](http://2.bp.blogspot.com/-uGboFTvkU2g/UDsl8OKRvdI/AAAAAAAAAP8/4aLlPHk2jNU/s1600/DSCN9007.JPG)

上面兩張就是搭配好電路後的主機，剩下程式的部分就可以試飛了。

目前的架構是使用遙控器的接收機發訊號給arduino，當我要變成四軸飛機的時候arduino將訊號傳送給飛控板去執行關於陀螺儀和加速度計的控制，藉由飛控板去控制電子變速器來調整馬達的轉速，當我要變身成為蜘蛛的時候，arduino又會將訊號傳給伺服控制器，再由伺服控制器做直接的控制，這樣一來讓事情分散出去了，我只需要簡單的處理遙控器訊號，然而這兩件分工出去的事情，在將來我會再好好找到相對應的DIY方法來自己做看看，因為分成三塊板子還是不夠簡便，希望可以直接做在一起，成為一塊專屬我自己的Arduino飛控蜘蛛板。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e8%a1%8c%e8%9c%98%e8%9b%9b3-%e7%ac%ac%e4%ba%8c%e4%bb%a3%e6%9e%b6%e6%a7%8b/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=331&action=edit)

# 飛行蜘蛛(4)-四旋翼的飛行概念
================

四旋翼是一種類似直升機的新種類飛行器，主要是利用四個無刷馬達為動力，使四軸機可以爬升，前進後退，左右移動還有原地旋轉的功能，玩起來很像直升機，加上製作出一台四軸機的難度又比直升機還要小，所以最近幾年有看見許多人開始玩，甚至還有三軸機和六軸機，以及其他更多種類的版本。

介紹飛行原理之前，先說說四軸機的飛行模式

一般的四軸機分成兩種飛行模式

1.  十字模式
2.  X字模式

如下圖所示，這是四軸機的空照圖，藍色圓圈是馬達，朝前方飛行，也就是圖片中的上方飛行

[![](http://3.bp.blogspot.com/-nU4xsiQptSY/T8nFDIbYQ6I/AAAAAAAAAH4/hPuNYD1MDyk/s1600/%25E5%258D%2581%25E5%25AD%2597.jpg) ](http://3.bp.blogspot.com/-nU4xsiQptSY/T8nFDIbYQ6I/AAAAAAAAAH4/hPuNYD1MDyk/s1600/%25E5%258D%2581%25E5%25AD%2597.jpg)

十字模式

[![](http://2.bp.blogspot.com/-DP4y5Nh9Jf0/T8nFCa8uSoI/AAAAAAAAAH0/cIEk_1F3lmc/s1600/X.jpg)](http://2.bp.blogspot.com/-DP4y5Nh9Jf0/T8nFCa8uSoI/AAAAAAAAAH0/cIEk_1F3lmc/s1600/X.jpg)

 X字模式

接下來稍微說明飛行原理，四軸機的槳分程正反兩槳，各兩隻相同的槳剛好會裝在另一支槳的對面，而相反的槳則會裝在隔壁，在飛行的時候，利用槳的轉速強弱來控制方向，飛行的狀態分成下列四種，也就是四通道所控制的四種狀態。

1.  高度
2.  前後
3.  左右
4.  旋轉

高度是用油門通道來進行的，如果只有推動油門，馬達的轉速以相同轉速同時上升，然後四軸機就能夠原地起飛。

其餘部分主要是利用馬達的轉速不同來使飛機移動和旋轉，首先我將馬達編上號碼

　　　　　　　　　　　　　　１　　　２

　　　　　　　　　　　　　　　　Ｘ

　　　　　　　　　　　　　　３　　　４

當我將1和2的速度減弱，3和4的速度提高，則飛機就會往減弱的的方向前進，利用這樣的方式我已經可以前後左右移動了。比較特別的是旋轉，當我將1和4的速度減弱，2和3的速度提高，由於1和4是順時鐘旋轉，而2和3是逆時鐘旋轉，所以四軸機會整台順時鐘旋轉。 而十字模式也類似這樣的方式來操作四軸機的移動。

下面的圖來輔助，可以更快了解

http://www.ourdev.cn/thread-959043-1-1.html

[![](http://4.bp.blogspot.com/-Qp0q01Lse-o/T8nQmxgfYmI/AAAAAAAAAII/hddT1otwVAA/s1600/ourdev_240755.jpg)](http://4.bp.blogspot.com/-Qp0q01Lse-o/T8nQmxgfYmI/AAAAAAAAAII/hddT1otwVAA/s1600/ourdev_240755.jpg)

剛剛提到通道，通道是什麼呢?

通道(channel)：

你所能夠操作的自由度數量。例如你可以控制他上下，則稱為一通道，如果可以控制上下左右則是兩通道，一般四軸機需要上下(高低)、左右傾斜、前後傾斜，順逆旋轉，因此我們需要四通道才可以操作四軸機。

話說為什麼我想要玩四軸機呢？因為我覺得目前很少看過有人玩會飛的機器人，好像大部分的機器人都是在地面上的，有看過有人做過六足機器人，兩足機器人，坦克機器人，那有沒有能夠飛的呢？

後來想想，的確，要會飛的真的很難，一般的飛機飛太快，空間要很大，所以不適合拿來作機器人，直升機又很難製作，光是所需要的經費和知識就很驚人，後來才知道有這種四軸飛行器，像是直升機一樣，但是DIY的難度又不會過高，非常適合拿來製作機器人的飛行背包，因此，就開啟了我這條四軸機之路的。雖然目前也還只是在摸索階段，但是我還是會盡量把我所知道的分享出來唷=)

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e8%a1%8c%e8%9c%98%e8%9b%9b4-%e5%9b%9b%e6%97%8b%e7%bf%bc%e7%9a%84%e9%a3%9b%e8%a1%8c%e6%a6%82%e5%bf%b5/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=344&action=edit)

# 飛行蜘蛛(5)-飛機用馬達、電子變速器
===================

之前稍微提過了四軸機基本架構，接著特別來說明一些重要零件，這篇主要介紹兩個重要零件幾乎可以等同於四軸機的手腳。

1.  無刷馬達
2.  電子變速器

購買的時候常常會看見幾個不太了解的新名詞，這邊藉由我所知道的知識來為大家解惑一下。

1.無刷馬達(無刷電機)

KV的定義

KV值表示每外加一伏特的電壓，所提升的每分鐘轉速。

例如以930KV的無刷馬達來說，當給他一伏特時，會有每分鐘930轉，如果給他兩伏特，就會有930*2 = 1860 轉/分鐘，但是在購買的時候，KV並不表示越大越好，或是越小越好，而是依照他所使用的場合不同而有不同樣的功能。

2.電子變速器(電子調速器) ESC (Electronic Speed Control)

有時又簡稱為電變，功能是將控制訊號轉為馬達用電流，以控制馬達轉速，因為飛控板的控制訊號是無法具有大電流(3A以上)來推動馬達，所以會使用電變來作為控制馬達的間接角色，舉個例子來說，控制板就像是老闆，電變是作業員，控制板(老闆)發號施令，而電變(員工)負責實際執行，讓無刷馬達開始旋轉，除此之外，電變還可以將鋰電池的電壓11.1V轉為5V，提供給飛控板使用，在選購電變上有什麼要注意呢？

一般來說電變主要分成多少A？市面上有20A、30A、40A，目前大多使用20A左右，在調整電變行程的時候要接上馬達，因為逼逼聲音是來自馬達，其上面有三條電機控制線，兩條電源線，一條杜邦的訊號線。

詳細的接線請看下面的概念圖，由鋰電池先提供電源給電子變速器，然後再轉換成適合電壓給飛控板，接著飛控板輸出訊號給電子變速器，電子變速器在依照飛控板的訊號來操作馬達。

[![](http://4.bp.blogspot.com/-LOOfZiQYkDc/T-MpPCsrcHI/AAAAAAAAAIY/RVsgF7_TAxQ/s1600/%E9%9B%BB%E5%AD%90%E8%AE%8A%E9%80%9F%E5%99%A8%E6%8E%A5%E7%B7%9A%E5%9C%96.jpg)](http://4.bp.blogspot.com/-LOOfZiQYkDc/T-MpPCsrcHI/AAAAAAAAAIY/RVsgF7_TAxQ/s1600/%E9%9B%BB%E5%AD%90%E8%AE%8A%E9%80%9F%E5%99%A8%E6%8E%A5%E7%B7%9A%E5%9C%96.jpg)

除此之外還有一個特殊名詞，BEC (Battery Eliminator Circuit) 電池分離迴路：

這是有些電子變速器會有的功能，在電池電量完全消耗完之前，為了防止馬達將所有的電力都吃掉，而導致飛控板和接收機當機，因此會先將馬達和電池的電力連接切斷，讓飛機還有機會在受控制的情況下安全的下降。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e8%a1%8c%e8%9c%98%e8%9b%9b5-%e9%a3%9b%e6%a9%9f%e7%94%a8%e9%a6%ac%e9%81%94%e3%80%81%e9%9b%bb%e5%ad%90%e8%ae%8a%e9%80%9f%e5%99%a8/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=355&action=edit)

# 飛行蜘蛛(6)-第三代架構的蜘蛛篇
=================

[![](http://1.bp.blogspot.com/-XhZOBHHA_50/ULxrzB_IewI/AAAAAAAAASA/n7_521BpUS4/s400/2012-12-03_170542.png)](http://1.bp.blogspot.com/-XhZOBHHA_50/ULxrzB_IewI/AAAAAAAAASA/n7_521BpUS4/s1600/2012-12-03_170542.png)

這是目前新的設計圖，用壓克力來製作，可以簡化許多重量

打算先將蜘蛛的行走步態完成之後，再將上面的飛行裝置裝上去

[![](http://2.bp.blogspot.com/-Dw6-a38cBxI/ULxq8DNDKJI/AAAAAAAAARc/kswO36wLTjQ/s200/2012-11-29_160612.png)](http://2.bp.blogspot.com/-Dw6-a38cBxI/ULxq8DNDKJI/AAAAAAAAARc/kswO36wLTjQ/s1600/2012-11-29_160612.png)[![](http://3.bp.blogspot.com/-mZxFV3N7MnI/ULxq-WPH3QI/AAAAAAAAAR0/BMjTO-6km38/s200/2012-11-29_160746.png)](http://3.bp.blogspot.com/-mZxFV3N7MnI/ULxq-WPH3QI/AAAAAAAAAR0/BMjTO-6km38/s1600/2012-11-29_160746.png)[![](http://4.bp.blogspot.com/-4EA1VQhdXmY/ULxq9Wnua6I/AAAAAAAAARs/M5YMPK2ythM/s200/2012-11-29_160655.png)](http://4.bp.blogspot.com/-4EA1VQhdXmY/ULxq9Wnua6I/AAAAAAAAARs/M5YMPK2ythM/s1600/2012-11-29_160655.png)[![](http://1.bp.blogspot.com/-ebb6hb9r1UY/ULxq81wnrVI/AAAAAAAAARk/qxBWBFzV31M/s200/2012-11-29_160638.png)](http://1.bp.blogspot.com/-ebb6hb9r1UY/ULxq81wnrVI/AAAAAAAAARk/qxBWBFzV31M/s1600/2012-11-29_160638.png)

完成圖

[![](http://1.bp.blogspot.com/-3qcjHKeiG38/ULyPY2frbhI/AAAAAAAAASY/RkGD_1WBC4A/s400/2012-11-27+19.23.17.jpg)](http://1.bp.blogspot.com/-3qcjHKeiG38/ULyPY2frbhI/AAAAAAAAASY/RkGD_1WBC4A/s1600/2012-11-27+19.23.17.jpg)

裡面使用的是這塊舵機控制板，將來會在裡面編寫好我的蜘蛛步態模組網站 http://www.torobot.com/usc/

[![](http://www.torobot.com/images/usc32.jpg) ](http://www.torobot.com/images/usc32.jpg)

我購買的是24CH的舵機控制板，上面5pins排母的部分可以插上藍芽控制

[![](http://2.bp.blogspot.com/-5LkYdKsTaaM/ULyQwkuz1bI/AAAAAAAAASg/9GQO2IBq56Q/s640/2012-12-03_194443.jpg)](http://2.bp.blogspot.com/-5LkYdKsTaaM/ULyQwkuz1bI/AAAAAAAAASg/9GQO2IBq56Q/s1600/2012-12-03_194443.jpg)

 不過目前也只做好了硬體部分，還沒有實際開始編寫蜘蛛的步態~~

最近總是在觀察喵咪小狗之類的走路，或許能藉此得到些神奇的靈感XDDDD

(由於專題的關係，其實也在觀察人類的走路方式，看起來很簡單的走路，其實很複雜的>””<)

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e8%a1%8c%e8%9c%98%e8%9b%9b6-%e7%ac%ac%e4%b8%89%e4%bb%a3%e6%9e%b6%e6%a7%8b%e7%9a%84%e8%9c%98%e8%9b%9b%e7%af%87/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=360&action=edit)

# 飛天蜘蛛(7)-RC接收器
=============

[![](http://3.bp.blogspot.com/-ltTiVbq7S4s/UO5afWffvAI/AAAAAAAAAaA/aoMNZYjv3wo/s400/2013-01-10+13.58.17.jpg)](http://3.bp.blogspot.com/-ltTiVbq7S4s/UO5afWffvAI/AAAAAAAAAaA/aoMNZYjv3wo/s1600/2013-01-10+13.58.17.jpg)[![](http://3.bp.blogspot.com/-bX4hQw5p0_o/UO5bGXH8aZI/AAAAAAAAAaY/1yH0qJFguRI/s400/2013-01-10+14.08.47.jpg)](http://3.bp.blogspot.com/-bX4hQw5p0_o/UO5bGXH8aZI/AAAAAAAAAaY/1yH0qJFguRI/s1600/2013-01-10+14.08.47.jpg)

為了讓蜘蛛也可以利用遙控器來控制，因此我打算利用自己DIY的Arduino來讀取RC接收器的數值，RC接收器屆時讀取到的數值應該是PWM的訊號(這點還沒有很確認，不過對於接下來的使用不影響。)

自製的Arduino的接腳圖如下

[![](http://2.bp.blogspot.com/-2kVU4gDtppY/UO5adk88q1I/AAAAAAAAAZU/GkUozjyGsQU/s640/2013-01-10+13.55.03.jpg)](http://2.bp.blogspot.com/-2kVU4gDtppY/UO5adk88q1I/AAAAAAAAAZU/GkUozjyGsQU/s1600/2013-01-10+13.55.03.jpg)

左邊的是電源模組，提供5V的電壓，右邊則是RS232模組，用來連接電腦的，上方的一條藍線+五條黃色線是RC接收機的訊號線，藍線部分則沒有接任何東西，因為我只有五個頻道。

那五條黃色線分別對應到UNO數位腳的9 10 11 12 13，在下列的程式碼利用

pulseIn(pin, HIGH)

這行來進行讀取PWM訊號HIGH的時間長度。

    void setup() {
      pinMode(9, INPUT);             
      pinMode(10, INPUT);             
      pinMode(11, INPUT);             
      pinMode(12, INPUT);            
      pinMode(13, INPUT);           
      Serial.begin(9600);                   
    }
    
    void loop() {
      int value1 = pulseIn(9, HIGH);
      int value2 = pulseIn(10, HIGH);
      int value3 = pulseIn(11, HIGH);
      int value4 = pulseIn(12, HIGH);
      int value5 = pulseIn(13, HIGH);
      value1 = value1/10 - 149;
      value2 = value2/10 - 149;
      value3 = value3/10 - 149;
      value4 = value4/10 - 149;
      value5 = value5/10 - 149;  
      Serial.print(value1);
      Serial.print("   ");
      Serial.print(value2);
      Serial.print("   ");
      Serial.print(value3);
      Serial.print("   ");
      Serial.print(value4);
      Serial.print("   ");
      Serial.print(value5);
      Serial.println("   ");
      delay(25);
    }
    

我的CH3目前顯示-41，表示搖桿是拉到底的狀態，如果往上漸漸調升，則數字會越來越大；CH5是gyro調整用的，因此只有0和1，當我撥至0的時候會顯示-52(負數)左右，當我撥至1的時候會顯示52(正數)。

[![](http://4.bp.blogspot.com/-XA0cbPmjfMc/UO5e_Foo9EI/AAAAAAAAAbk/gDtY-Df46Is/s400/2013-01-10+14.25.31.jpg)](http://4.bp.blogspot.com/-XA0cbPmjfMc/UO5e_Foo9EI/AAAAAAAAAbk/gDtY-Df46Is/s1600/2013-01-10+14.25.31.jpg)

CH3 搖桿 表示油門

[![](http://1.bp.blogspot.com/-pmhB0be3nAo/UO5e_JSt9yI/AAAAAAAAAbo/16rUxo2a1ko/s400/2013-01-10+14.25.25.jpg)](http://1.bp.blogspot.com/-pmhB0be3nAo/UO5e_JSt9yI/AAAAAAAAAbo/16rUxo2a1ko/s1600/2013-01-10+14.25.25.jpg)

CH5 Gyro 調整鈕

[![](http://4.bp.blogspot.com/-_YdZbNIdzPw/UO5d2HlVWAI/AAAAAAAAAbM/Y0naMsGbDXA/s640/2013-01-10_142033.jpg)](http://4.bp.blogspot.com/-_YdZbNIdzPw/UO5d2HlVWAI/AAAAAAAAAbM/Y0naMsGbDXA/s1600/2013-01-10_142033.jpg)

CH3 搖桿撥到最低的狀態

CH5 按鈕調整至 0 的狀態

[![](http://3.bp.blogspot.com/-tjMgHrBe71E/UO5d2LQtbKI/AAAAAAAAAbQ/OCDFdvCn_00/s640/2013-01-10_142009.jpg) ](http://3.bp.blogspot.com/-tjMgHrBe71E/UO5d2LQtbKI/AAAAAAAAAbQ/OCDFdvCn_00/s1600/2013-01-10_142009.jpg)

CH3 搖桿撥到最高的狀態

CH5 按鈕調整至 1 的狀態

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b7-rc%e6%8e%a5%e6%94%b6%e5%99%a8/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=367&action=edit)

# 飛天蜘蛛(8)-飛機機身製作
==============

飛天蜘蛛目前已經快要製作完成了，雖然還有很多不滿意的地方QWQ……..

今天先來和大家分享關於機體的製作方式，首先我的機身的部分是用鋁方管+壓克力製作而成的，鋁方管利用線鋸機切割而成，並且再加以打洞，機身最遠的兩軸馬達距離是400mm，大家比較好奇的應該是中心的壓克力板怎麼製作而成的。

我是在先前製作魚缸的機會中，使用雷射切割機順便製作出機身的部分。

[![](http://2.bp.blogspot.com/-16waRCc9VqA/UPQKFXHUkyI/AAAAAAAAAc4/vovb8u4lKds/s640/2013-01-06+17.20.09.jpg) ](http://2.bp.blogspot.com/-16waRCc9VqA/UPQKFXHUkyI/AAAAAAAAAc4/vovb8u4lKds/s1600/2013-01-06+17.20.09.jpg)

中心機身部分

![](http://1.bp.blogspot.com/-8e_SENRG-Rs/UPQNgQ-ba8I/AAAAAAAAAfM/DJfrzjxcVzg/s640/2013-01-07+21.57.33.jpg)

馬達座台部分

這兩部分的零件都是使用雷射切割機製作出來的。

以下放個小影片給大家欣賞雷射切割機的是怎麼切東西的唷。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b8-%e9%a3%9b%e6%a9%9f%e6%a9%9f%e8%ba%ab%e8%a3%bd%e4%bd%9c/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=393&action=edit)

# 飛天蜘蛛(9)-蜘蛛出現了!!!
================

首先先讓大家看一下飛天蜘蛛本來希望長怎樣

本來以為會是上面這樣

[![](http://1.bp.blogspot.com/-7WnZYzvtIlI/UPbZoJ7ZzhI/AAAAAAAAAf4/_7jYMDQ9A44/s320/2013-01-07+21.57.19.jpg)](http://1.bp.blogspot.com/-7WnZYzvtIlI/UPbZoJ7ZzhI/AAAAAAAAAf4/_7jYMDQ9A44/s1600/2013-01-07+21.57.19.jpg)

和下面那樣合體

[![](http://2.bp.blogspot.com/-GDz8Bg4dUhg/UPbZoJNEyZI/AAAAAAAAAf0/Ss91eR0prPE/s320/2012-11-27+19.23.21.jpg)](http://2.bp.blogspot.com/-GDz8Bg4dUhg/UPbZoJNEyZI/AAAAAAAAAf0/Ss91eR0prPE/s1600/2012-11-27+19.23.21.jpg)

就會是一隻會飛的蜘蛛了…..

結果實際狀況完全不是這樣……

已經使用了9g超輕伺服機之後，以為應該是不會太重了

但是問題最後不是9g伺服機的重量，而是他的力量不夠

因此無法抬起來這麼重的機身，除非馬達電池電子變速器都要換成更高檔的。

至於要換成多好的目前還不清楚，因此只好先減少腳的數目。

最後變成這樣。

[![](http://2.bp.blogspot.com/-GBSXXwMbK1c/UPbbEPPDjiI/AAAAAAAAAgc/MyNlEXAQpXA/s320/2013-01-15+17.08.55.jpg)](http://2.bp.blogspot.com/-GBSXXwMbK1c/UPbbEPPDjiI/AAAAAAAAAgc/MyNlEXAQpXA/s1600/2013-01-15+17.08.55.jpg)

剩下兩隻腳是會動的…..

最後變成只有兩隻腳會動，經過這樣多次的測試之後，突然發現真的要做出一隻本來想像的那種六足四旋翼蜘蛛，其中有許多困難點沒仔細考慮清楚，尤其是四旋翼在負重之後的操作難度又大增，本來就已經很不好控制了，加上沒有專業的去分配重量導致重量不均，只能依靠飛行時的感測器們去進行修正。

[![](http://4.bp.blogspot.com/-GC7jIJIQYs8/UPbbEKXeQyI/AAAAAAAAAgg/OYS4ML8rWzw/s640/2013-01-15+17.27.31.jpg)](http://4.bp.blogspot.com/-GC7jIJIQYs8/UPbbEKXeQyI/AAAAAAAAAgg/OYS4ML8rWzw/s1600/2013-01-15+17.27.31.jpg)

準備要起飛之前很憤怒的感覺。

飛天蜘蛛表示：怒…..被截斷四隻腳…..

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b9-%e8%9c%98%e8%9b%9b%e5%87%ba%e7%8f%be%e4%ba%86/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=401&action=edit)

# 飛天蜘蛛(10)-保麗龍機身
==============

上篇題到後來截去了兩隻腳之後，其實非常氣餒，突然發現她只剩下夾娃娃機功能了，但其實是不太可能邊飛邊夾的，這是我的技術問題（不太會操控），加上蜘蛛剩下兩隻腳實在也太氣餒了，因此決定裝上保麗龍腳(看起來稍微有點氣勢)，就開始去學校的福利社購買相關用品，買了一大片保麗龍板和一隻保麗龍的切割器，保麗龍切割器就是使用1號電池，然後會加熱前面的那根小鐵絲，利用高溫來切割保麗龍板，否則保麗龍會碎成一顆顆小球。

[![](http://2.bp.blogspot.com/-GBSXXwMbK1c/UPbbEPPDjiI/AAAAAAAAAgc/MyNlEXAQpXA/s400/2013-01-15+17.08.55.jpg)](http://2.bp.blogspot.com/-GBSXXwMbK1c/UPbbEPPDjiI/AAAAAAAAAgc/MyNlEXAQpXA/s1600/2013-01-15+17.08.55.jpg)

首先買來之後不外乎就是先開始切個大概，用鐵絲去做某部分的補強，做出想像中的腳。

[![](http://2.bp.blogspot.com/-UljZXJlcfD8/UPbeWuhHH1I/AAAAAAAAAhc/JWuNbDtUoq0/s400/2013-01-15+14.41.56.jpg)](http://2.bp.blogspot.com/-UljZXJlcfD8/UPbeWuhHH1I/AAAAAAAAAhc/JWuNbDtUoq0/s1600/2013-01-15+14.41.56.jpg)

接下來拿去掃描器上面列印~~

[![](http://2.bp.blogspot.com/-l_iEjIJPgmw/UPbeW_0mQRI/AAAAAAAAAhY/d38yPLeG6Lo/s400/2013-01-15+14.42.31.jpg)](http://2.bp.blogspot.com/-l_iEjIJPgmw/UPbeW_0mQRI/AAAAAAAAAhY/d38yPLeG6Lo/s1600/2013-01-15+14.42.31.jpg)

因為想要複製四個出來，因此需要一個紙模來對照。

[![](http://4.bp.blogspot.com/-PHOfb0Oeffo/UPbeX7OwxRI/AAAAAAAAAhg/O6_xTWZZpEQ/s400/2013-01-15+14.42.39.jpg)](http://4.bp.blogspot.com/-PHOfb0Oeffo/UPbeX7OwxRI/AAAAAAAAAhg/O6_xTWZZpEQ/s1600/2013-01-15+14.42.39.jpg)

有了紙模之後，我再用奇異筆去描繪成我真正想要的樣子，接著就開始剪下來

[![](http://2.bp.blogspot.com/-ojNZ2JHv2JA/UPbeaIy3oPI/AAAAAAAAAiI/DnHq12daALE/s400/2013-01-15+14.44.32.jpg)](http://2.bp.blogspot.com/-ojNZ2JHv2JA/UPbeaIy3oPI/AAAAAAAAAiI/DnHq12daALE/s1600/2013-01-15+14.44.32.jpg)

剪好之後，因為要黏在保麗龍板上面，因此不能用一般的膠水，而等到切好之後我又得拿下來，因此又不能夠太黏，不然會破壞表面。

[![](http://1.bp.blogspot.com/-y3XIjVXaR3k/UPbebX5WTGI/AAAAAAAAAig/PkVIq55NRH4/s400/2013-01-15+14.46.53.jpg)](http://1.bp.blogspot.com/-y3XIjVXaR3k/UPbebX5WTGI/AAAAAAAAAig/PkVIq55NRH4/s1600/2013-01-15+14.46.53.jpg)

看到了嗎？我使用的是一種特殊的黏土，他可以達到我上述想要的效果，他一般是拿來貼海報用的，是一種有黏性的黏土。

[![](http://1.bp.blogspot.com/-5sdTo1J4FB8/UPbeb_RxCzI/AAAAAAAAAik/L6BWUfwGwa8/s320/2013-01-15+14.47.55.jpg)](http://1.bp.blogspot.com/-5sdTo1J4FB8/UPbeb_RxCzI/AAAAAAAAAik/L6BWUfwGwa8/s1600/2013-01-15+14.47.55.jpg)

貼上去之後就開始準備切割囉`

[![](http://1.bp.blogspot.com/-ud7mfI-cUHY/UPbecxUCY5I/AAAAAAAAAi8/5K5HZvY--ro/s320/2013-01-15+14.51.01.jpg)](http://1.bp.blogspot.com/-ud7mfI-cUHY/UPbecxUCY5I/AAAAAAAAAi8/5K5HZvY--ro/s1600/2013-01-15+14.51.01.jpg)

完成!!!!!!

接著再將做好的腳依序裝上去試試看，效果不錯的話就把剩下三個做好裝上去，不然就是在重新回到一開始製作紙模的階段。

———————————————————————————

接著是眼睛~~

眼睛的部分就是使用很一般的保麗龍球，至於會發光，就是在裡面塞了些LED燈泡。

[![](http://4.bp.blogspot.com/-zL33piF_GtE/UPbef2LjN8I/AAAAAAAAAj0/_Fjl-ej0kQM/s320/2013-01-15+16.59.46.jpg)](http://4.bp.blogspot.com/-zL33piF_GtE/UPbef2LjN8I/AAAAAAAAAj0/_Fjl-ej0kQM/s1600/2013-01-15+16.59.46.jpg)[![](http://4.bp.blogspot.com/-bw75vMpiRJ0/UPbegvi5laI/AAAAAAAAAj8/yonZK6btyFY/s320/2013-01-15+16.59.52.jpg)](http://4.bp.blogspot.com/-bw75vMpiRJ0/UPbegvi5laI/AAAAAAAAAj8/yonZK6btyFY/s1600/2013-01-15+16.59.52.jpg)[![](http://4.bp.blogspot.com/-TZL1UQ94qVc/UPbeg68sEXI/AAAAAAAAAkM/UHA-PJpaxGU/s320/2013-01-15+17.00.03.jpg)](http://4.bp.blogspot.com/-TZL1UQ94qVc/UPbeg68sEXI/AAAAAAAAAkM/UHA-PJpaxGU/s1600/2013-01-15+17.00.03.jpg)

[![](http://2.bp.blogspot.com/-nJRLyLwFaGo/UPbeg753_gI/AAAAAAAAAkI/hk8AjakEWRI/s320/2013-01-15+17.00.18.jpg)](http://2.bp.blogspot.com/-nJRLyLwFaGo/UPbeg753_gI/AAAAAAAAAkI/hk8AjakEWRI/s1600/2013-01-15+17.00.18.jpg)[![](http://1.bp.blogspot.com/-BizJDU-OsR8/UPbef_VnRxI/AAAAAAAAAjw/AusvjMoYuqY/s320/2013-01-15+16.59.36.jpg)](http://1.bp.blogspot.com/-BizJDU-OsR8/UPbef_VnRxI/AAAAAAAAAjw/AusvjMoYuqY/s1600/2013-01-15+16.59.36.jpg)

由上面五個圖大概可以知道是怎麼製作的。

在做眼睛的過程中突然發現有一些有趣的玩法。

[![](http://3.bp.blogspot.com/-LO_l1y9IiIw/UPbed895R7I/AAAAAAAAAjQ/ZaD_-GDU5m8/s640/2013-01-15+16.13.25.jpg)](http://3.bp.blogspot.com/-LO_l1y9IiIw/UPbed895R7I/AAAAAAAAAjQ/ZaD_-GDU5m8/s1600/2013-01-15+16.13.25.jpg)

眼神呆滯

[![](http://4.bp.blogspot.com/-WHg0cw2cTyg/UPbeeoGuKVI/AAAAAAAAAjc/msSdkPgi5ak/s640/2013-01-15+16.13.46.jpg)](http://4.bp.blogspot.com/-WHg0cw2cTyg/UPbeeoGuKVI/AAAAAAAAAjc/msSdkPgi5ak/s1600/2013-01-15+16.13.46.jpg)

憤怒的波唷

[![](http://4.bp.blogspot.com/-2He_H5vhF3g/UPbeeWy9CDI/AAAAAAAAAjg/5-6FvtpduYU/s640/2013-01-15+16.13.35.jpg)](http://4.bp.blogspot.com/-2He_H5vhF3g/UPbeeWy9CDI/AAAAAAAAAjg/5-6FvtpduYU/s1600/2013-01-15+16.13.35.jpg)

哀傷的波唷

[![](http://1.bp.blogspot.com/-vsFLKf45HWU/UPbefL3E2xI/AAAAAAAAAjs/36eVYXAEEpU/s640/2013-01-15+16.13.59.jpg)](http://1.bp.blogspot.com/-vsFLKf45HWU/UPbefL3E2xI/AAAAAAAAAjs/36eVYXAEEpU/s1600/2013-01-15+16.13.59.jpg)

波唷的鈴鐺

話說眼球在戳洞的過程中，真的會有好痛的感覺……

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b10-%e4%bf%9d%e9%ba%97%e9%be%8d%e6%a9%9f%e8%ba%ab/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=412&action=edit)

# 飛天蜘蛛(11)-Arduino DIY+程式碼+2.4GHz
===============================

之前學會了自製Arduino之後一直沒有機會應用，這次就覺得飛機的伺服控制器就打算利用自己製作的Arduino來設計。

[![](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-01-1013-54-171.jpg?w=300)](http://4.bp.blogspot.com/-fj7iAFbJuRo/UPektLUe4BI/AAAAAAAAAlA/Yqq5HeA8njU/s1600/2013-01-10+13.54.17.jpg)

利用Arduino讀取遙控器的資料，接著將資料拿來控制飛天蜘蛛的腳。

這些程式碼都會放在google code上面，提供給大家下載使用

Arduino部分

RC_control：用來接收遙控器的資料

setservo：設定伺服馬達位置用

servo\_\_key\_control：主要的程式碼，可以利用接收器所得到的資料去控制伺服馬達和飛行

[![](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-01-1014-08-37.jpg)](http://2.bp.blogspot.com/-rAdzGJq9go0/UPeku7RqfFI/AAAAAAAAAlU/NEB8scEkyWc/s1600/2013-01-10+14.08.37.jpg)[![](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-01-1013-58-172.jpg)](http://4.bp.blogspot.com/-pGnUOQ1-ZX4/UPekuVLFEwI/AAAAAAAAAlM/xGM5B9U7TJs/s1600/2013-01-10+13.58.17.jpg)

左手邊的那個就是接收器，是一個小盒子，左手邊的是遙控器，是使用2.4G的傳輸模式，在使用之前當然要先做過一些基本的調整和對頻。

——————————————————————————————-

提到2.4G就順便說說相關的資料好了，可能很多人對於這些尚且不是很了解。

遙控器希望藉由我手上推動搖桿後所得到的一些電子訊號傳遞出去，再由一個小盒子接收訊號，並且轉換成我們想要的PWM資料，希望達到這樣的效果，我們就得使用「電磁波」 (Electromagnetic Wave) ，電磁波這種東西像是紅外線、紫外線和可見光等等都是所謂的電磁波，而電磁波譜中約在3KHz～300GHz等區域的電磁波被稱之為「無線電」，其波長從1mm到100Km，而一般的可見光波長則是400nm~700nm，由此可見無線電的波長相當的長，而且範圍相當的廣。

那麼為何要使用無線電呢？可以用其他光來傳訊息嗎？當然可以，紅外線也是一種傳遞訊息的方式，但是大家都知道，紅外線是有可能會被擋住的，假如隔了道牆壁，紅外線傳輸就會出現問題，可是無線電卻不一樣，他有著不容易被其他物質遮蔽的特性，因此有些天文學的觀測技術就是利用無線電訊號來觀測星體運作，也就是所謂的「電波望遠鏡」。

無線電運用範圍很廣，主要應用在於通訊方面，由於無線電很好用，大家希望能夠利用這樣的工具來遙控資料或是傳遞資料，像是我想要遙控我的飛機一樣，但是如果你用到的訊號和我一模一樣，我的飛機要聽誰的？因此發展出許多中的調變技術，一般收音機最常見的就是AM調幅（Amplitude Modulation）和FM調頻（Frequency Mpdulation），這也是以前的遙控所用的方式，你必須在你的飛機接收機上面裝一個和遙控器一樣頻率的振盪器，才可以進行遙控，不幸的是，如果你的震盪器又和別人一樣呢???這時候不就又發生一樣的悲劇了嗎？

2.4GHz的遙控器具有自動跳頻的功能，也就是說只要你之前在家先對過頻率之後，就不用擔心和別人頻道相同，他利用展頻的方式將訊號分布在不同的頻率上傳輸，因此不會因為一個頻率受到干擾而訊號整個錯亂，因此不用像以往的AM和FM為了避免雜訊而提高功率，2.4GHz其實是相當省電的。

[![](http://tabbymeow.files.wordpress.com/2013/04/2013-01-1321-20-16.jpg?w=300)](http://3.bp.blogspot.com/-VNC1kzmgh9Q/UPek0TbvB1I/AAAAAAAAAms/euRo0_Qygds/s1600/2013-01-13+21.20.16.jpg)

大致上就像是這樣接起來就可以用了。哪條線接哪個channel要仔細看過說明書才知道。

[![](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-01-1019-36-29.jpg?w=300)](http://1.bp.blogspot.com/-WdJpoXDWvVM/UPekxo9V4sI/AAAAAAAAAmA/sPkN_oqZLmM/s1600/2013-01-10+19.36.29.jpg)

和腳進行連接，並且用飛機本身的電源去去提供給Arduino。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b11-arduino-diy%e7%a8%8b%e5%bc%8f%e7%a2%bc2-4ghz/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=456&action=edit)

# 飛天蜘蛛(12)-影片出爐了
==============

\[http://www.youtube.com/watch?v=u8GVTjuA4qM\]

  
雖然最後在某個意義上面已經不算是四足蜘蛛了，但是標題同時也記錄著機器人在製作過程中不斷被修改著，因此標題並不打算改變，同時維持著這十篇一模一樣的主標題，並且在自己心中記錄著這樣製作機器人的體驗。  
這是我的google code連結，裡面有程式碼。

[http://code.google.com/p/roboard-quadrotor-spider/downloads/list](http://code.google.com/p/roboard-quadrotor-spider/downloads/list)

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b12-%e5%bd%b1%e7%89%87%e5%87%ba%e7%88%90%e4%ba%86/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=536&action=edit)

# 飛天蜘蛛(13)-RoBoard攝影機
===================

[![](http://2.bp.blogspot.com/-NhFTKnfrqKA/UUb5L3yJpmI/AAAAAAAAApk/P5aqYZXGS4E/s640/2013-03-18+16.35.54.jpg)](http://2.bp.blogspot.com/-NhFTKnfrqKA/UUb5L3yJpmI/AAAAAAAAApk/P5aqYZXGS4E/s1600/2013-03-18+16.35.54.jpg)

這次利用OpenCV寫了一個拍照小程式，當然也會附程式碼給大家，如果不會寫程式的基本上就直接執行就好了，由於RoBoard的主機板不支援新版OpenCV的某些指令，因此我直接使用OpenCV1.0去編寫RoBoard所能夠使用的程式碼，如果說大家一般的電腦也想要使用這個功能的話，我也寫好了一個讓大家在一般的電腦上也能夠執行的執行檔。

[PC_Takepictures](http://roboard-quadrotor-spider.googlecode.com/files/PC_Takepictures.rar)

這份檔案是給一般電腦使用的

[RoBoard_Takepictures](http://roboard-quadrotor-spider.googlecode.com/files/RoBoard_Takepictures.rar)

這是給RoBoard使用的，如果希望開機之後能夠自動執行的話，就將執行檔的捷徑貼到電腦的啟動資料夾下面就可以囉。

在拍攝之前記得在C槽裡面新增一個叫做picture的資料夾，所有的圖片檔案都會傳到那邊過去。

打開之後什麼都不用按下，直接會啟動拍照功能，兩秒拍下一張照片，如果希望可以手動拍照的話，利用其他方式連線進去電腦裡面(網路或是其他無線傳輸方式)，也可以利用我寫的程式來進行手動拍照，手動拍照的方式是點選Take a picture，點選進去之後按下鍵盤上面的C(表示笑一個XD)，接著就會幫你拍好一張照片囉。

[![](http://1.bp.blogspot.com/-VFtmfUmR_Bc/UUb5MUoKHRI/AAAAAAAAApw/HGf3q1Obobg/s400/2013-03-18+18.32.44.jpg)](http://1.bp.blogspot.com/-VFtmfUmR_Bc/UUb5MUoKHRI/AAAAAAAAApw/HGf3q1Obobg/s1600/2013-03-18+18.32.44.jpg)

我將WebCam裝在RoBoard上面，並且利用小顆鋰電池作為結合，以避免重量過重

[![](http://2.bp.blogspot.com/-7uyZalO2-rU/UUb5L1iIymI/AAAAAAAAApc/-pzt_U7Dl9A/s400/2013-03-18+16.32.07.jpg)](http://2.bp.blogspot.com/-7uyZalO2-rU/UUb5L1iIymI/AAAAAAAAApc/-pzt_U7Dl9A/s1600/2013-03-18+16.32.07.jpg)

出發前準備~~~

[![](http://1.bp.blogspot.com/-MzN-tFtPgu0/UUb5L0lHZBI/AAAAAAAAApg/yOzZqMSKAtc/s400/2013-03-18+16.45.54.jpg) ](http://1.bp.blogspot.com/-MzN-tFtPgu0/UUb5L0lHZBI/AAAAAAAAApg/yOzZqMSKAtc/s1600/2013-03-18+16.45.54.jpg)

 去拍照囉~~

接著教大家如何在RoBoard上面安裝攝影機和RoBoard\_Takepictures(上一代稱之為RB\_DMP2)的軟體，由於RoBoard在執行自動拍照和手動拍照的功能時，手動功能會有一點lag，所以我索性把手動拍照功能去除了，這邊來教大家的是開機之後自動拍照的功能。

1.首先將下載好的RB_DMP2放在桌面

[![](http://1.bp.blogspot.com/-yi0fhRn-46E/UUgP73g9xhI/AAAAAAAAAqE/m19f_uL6Row/s640/2013-03-19_145545.jpg)](http://1.bp.blogspot.com/-yi0fhRn-46E/UUgP73g9xhI/AAAAAAAAAqE/m19f_uL6Row/s1600/2013-03-19_145545.jpg)

2\. 將C槽打開

[![](http://3.bp.blogspot.com/-yIj44SmF79E/UUgP73FChSI/AAAAAAAAAqI/OaJBHP0vzu0/s640/2013-03-19_145600.jpg)](http://3.bp.blogspot.com/-yIj44SmF79E/UUgP73FChSI/AAAAAAAAAqI/OaJBHP0vzu0/s1600/2013-03-19_145600.jpg)

3.建立一個名為picture的資料夾

[![](http://3.bp.blogspot.com/-1O-TIy6bmlc/UUgP8d5bb_I/AAAAAAAAAqM/BpFA8oDZ0gQ/s640/2013-03-19_145611.jpg)](http://3.bp.blogspot.com/-1O-TIy6bmlc/UUgP8d5bb_I/AAAAAAAAAqM/BpFA8oDZ0gQ/s1600/2013-03-19_145611.jpg)

4.解壓縮RoBoard\_Takepictures(上一代稱之為RB\_DMP2)檔案並且打開，會發現有一個捷徑

[![](http://4.bp.blogspot.com/-9b3LWcZt-Zk/UUgP83eO58I/AAAAAAAAAqY/pmeMFC7jPFA/s640/2013-03-19_145625.jpg)](http://4.bp.blogspot.com/-9b3LWcZt-Zk/UUgP83eO58I/AAAAAAAAAqY/pmeMFC7jPFA/s1600/2013-03-19_145625.jpg)

5.執行之前請先將你的WebCam接上去

[![](http://1.bp.blogspot.com/-vfX9zdJayE4/UUgRTJtJ0EI/AAAAAAAAAro/T3jzdp5oQ0c/s640/2013-03-18+18.32.44.jpg)](http://1.bp.blogspot.com/-vfX9zdJayE4/UUgRTJtJ0EI/AAAAAAAAAro/T3jzdp5oQ0c/s1600/2013-03-18+18.32.44.jpg)

6.程式介面，按下離開則是取消拍照功能，右邊的BAR可以調整妳想要拍照的間隔，單位為毫秒，但是建議不要調整太小，RoBoard可能會有點吃不消。

[![](http://4.bp.blogspot.com/-7TPmDE4HYF0/UUgP9ETHmYI/AAAAAAAAAqg/aP3IpjwCzas/s640/2013-03-19_145642.jpg)](http://4.bp.blogspot.com/-7TPmDE4HYF0/UUgP9ETHmYI/AAAAAAAAAqg/aP3IpjwCzas/s1600/2013-03-19_145642.jpg)

7.接著再回去看剛剛你建立的C槽裡面的picture資料夾，你就會發現照片開始增加囉。

[![](http://4.bp.blogspot.com/-xasmJ-c0fnM/UUgP9Ga-4bI/AAAAAAAAAqk/FSvfzanhriM/s640/2013-03-19_145651.jpg)](http://4.bp.blogspot.com/-xasmJ-c0fnM/UUgP9Ga-4bI/AAAAAAAAAqk/FSvfzanhriM/s1600/2013-03-19_145651.jpg)

如果你想要讓RoBoard在一開機就能夠開啟程式的話，畢竟平常在使用的時候是不會接上螢幕的，先找到電腦的啟動資料夾。

[![](http://2.bp.blogspot.com/--FwTTMF35F4/UUgP9puSMMI/AAAAAAAAAq4/HHMYzn-qdBA/s640/2013-03-19_145725.jpg)](http://2.bp.blogspot.com/--FwTTMF35F4/UUgP9puSMMI/AAAAAAAAAq4/HHMYzn-qdBA/s1600/2013-03-19_145725.jpg)

將RB_DMP2裡面的捷徑複製一份到啟動資料夾裡面

[![](http://1.bp.blogspot.com/-lioRW7w2WW4/UUgP9lW6MAI/AAAAAAAAAqw/jGkp-6rrb0c/s640/2013-03-19_145736.jpg)](http://1.bp.blogspot.com/-lioRW7w2WW4/UUgP9lW6MAI/AAAAAAAAAqw/jGkp-6rrb0c/s1600/2013-03-19_145736.jpg)

大概就像是下面這樣，接著你重開機之後他就會自動開始幫你拍照囉。

[![](http://3.bp.blogspot.com/-x3W22kzeMdM/UUgP9-Yw4II/AAAAAAAAAq0/xBKI6PS3lww/s640/2013-03-19_145752.jpg)](http://3.bp.blogspot.com/-x3W22kzeMdM/UUgP9-Yw4II/AAAAAAAAAq0/xBKI6PS3lww/s1600/2013-03-19_145752.jpg)

以下是這一次的飛行紀錄=口=。。。。拍完之後的感想是，只要是會飛的裝置，基本上他一旦真正的升空之後，就要有不一定能夠回來的心理準備（我的最後是有回來），還有在室外飛機用的相機其實需要更多功能和抗光的機制在，否則飛上去之後拍的東西都是一片白白的，而且在操作飛機的過程中才了解到飛機要能夠安全的飛上去不光只是機體本身的性能，各種環境因素都得考量進去，像是風是目前裡面我覺得最重要的部分，從影片裡面可以看得到我的飛機開始往後飛，但是那其實是被吹走的，因此要操作這樣的飛機時，其實得跑到周遭沒有房子的地方才能操作，因為有大樓會影響你對風速的判定，這次飛行總共飛了三次，最後就…….

\[youtube=http://www.youtube.com/watch?v=6FTqPsNX0B0&w=320&h=266\]

目前算是不能飛的狀態了，要飛得整台全部重做了，在第三次飛行之後，上面的部分零件散架，機構部分約有三分之一損壞，Arduino電路板因為受到衝擊而導致部分線路損壞，兩隻槳也噴到不知道去哪邊了，幸好沒有撞到人或是其他車輛，剩下的RoBoard剛好因為和撞擊點差很遠而避免了這次墜機的損傷，在某種程度上來說，已經算是很幸運地墜機了，要操作它的難度搞不好還高於製作它的難度，至少對於一個沒駕照的新手而言，是這樣沒錯。

如果之後有人想試著製作四旋翼的話，要抱著他可能會摔機摔的四~五次都不會太心疼的心情下去嘗試，不然可能會難過很久一陣子了QWQ（畢竟製作許久的飛機可能就只能飛這三次）  
給大家看看幾張我空拍出來的畫面吧（有一點模糊就是了）

[![](http://2.bp.blogspot.com/-BPGs6bIf7F0/UUgepMvwPVI/AAAAAAAAAsA/fsUvraQYX0E/s320/Picture+165.jpg)](http://2.bp.blogspot.com/-BPGs6bIf7F0/UUgepMvwPVI/AAAAAAAAAsA/fsUvraQYX0E/s1600/Picture+165.jpg)

[![](http://2.bp.blogspot.com/-oyEQyjO4lCg/UUgepkujtBI/AAAAAAAAAsI/r85Y4QAvd-Q/s320/Picture+173.jpg)](http://2.bp.blogspot.com/-oyEQyjO4lCg/UUgepkujtBI/AAAAAAAAAsI/r85Y4QAvd-Q/s1600/Picture+173.jpg)

[![](http://2.bp.blogspot.com/-Z4E5rLX-BGQ/UUgeqMcxYcI/AAAAAAAAAsU/BGKOtHpCo4I/s320/Picture+186.jpg)](http://2.bp.blogspot.com/-Z4E5rLX-BGQ/UUgeqMcxYcI/AAAAAAAAAsU/BGKOtHpCo4I/s1600/Picture+186.jpg)

[![](http://3.bp.blogspot.com/-H2WSCu4MRSA/UUgeqC4cBpI/AAAAAAAAAsY/LXyu-MM2TU8/s320/Picture+180.jpg)](http://3.bp.blogspot.com/-H2WSCu4MRSA/UUgeqC4cBpI/AAAAAAAAAsY/LXyu-MM2TU8/s1600/Picture+180.jpg)

[![](http://1.bp.blogspot.com/-Rou0OZTVpK4/UUgeq4yfLcI/AAAAAAAAAsc/uT2ZlC8R-A4/s320/Picture+8.jpg)](http://1.bp.blogspot.com/-Rou0OZTVpK4/UUgeq4yfLcI/AAAAAAAAAsc/uT2ZlC8R-A4/s1600/Picture+8.jpg)

[![](http://4.bp.blogspot.com/-D9gf3BNAFW4/UUge2u9Lf_I/AAAAAAAAAsw/Tc9ciXq__NI/s320/Picture+180.jpg)](http://4.bp.blogspot.com/-D9gf3BNAFW4/UUge2u9Lf_I/AAAAAAAAAsw/Tc9ciXq__NI/s1600/Picture+180.jpg)

[![](http://1.bp.blogspot.com/-R34-HIHqjyc/UUge2tEd8wI/AAAAAAAAAs0/v5IARqQ2KQ4/s320/Picture+185.jpg)](http://1.bp.blogspot.com/-R34-HIHqjyc/UUge2tEd8wI/AAAAAAAAAs0/v5IARqQ2KQ4/s1600/Picture+185.jpg)

[![](http://4.bp.blogspot.com/-7LoA88Qt81Q/UUge2mKmv-I/AAAAAAAAAs4/8AzKNSsJX7M/s320/Picture+179.jpg)](http://4.bp.blogspot.com/-7LoA88Qt81Q/UUge2mKmv-I/AAAAAAAAAs4/8AzKNSsJX7M/s1600/Picture+179.jpg)

其實這就是所謂的LOMO風格啊!@@!!!!!!

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/%e9%a3%9b%e5%a4%a9%e8%9c%98%e8%9b%9b13-roboard%e6%94%9d%e5%bd%b1%e6%a9%9f/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=468&action=edit)


