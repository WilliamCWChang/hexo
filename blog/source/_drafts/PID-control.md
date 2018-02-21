---
title: PID-control
tags: machine
---

# PID控制理論(1)-基本介紹
===============

[![384009_3810124224093_732240060_n](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)

這幾天系上學長介紹了一篇不錯的入門級教學文章給我，是有關機器人的PID控制理論，這篇文章的作者是J. Sluka。

下面是原文網址

[http://www.inpharmix.com/jps/PID\_Controller\_For\_Lego\_Mindstorms_Robots.html](http://www.inpharmix.com/jps/PID_Controller_For_Lego_Mindstorms_Robots.html)

看完了之後覺得受益良多，因此趕快PO上來和大家來分享一下，接下來的部分我會截取重點的部分翻譯和補充一些注解。

PID控制理論是一種常見的技術，使用範圍很廣，例如車輛、機器人，甚至是火箭的控制，而完整的PID控制理論以數學的角度來看是相當複雜，但是在實際操作方面卻是相當簡單，相對容易使用而且可以得到出乎意料之外的好效果。

J. Sluka是使用樂高玩具所組成的兩輪機器車來作PID控制理論的介紹，但是實際上PID理論的使用範圍很廣，接下來介紹的調適方式並非只能夠使用在樂高 機器人上面，但是為了要使大家容易了解，J. Sluka將會使用一個實體機器車來說明，PID控制理論對於已經學會微積分的夥伴們，是非常好理解的，但是J. Sluka這份文件是給國小到國中的小孩們也能夠簡單學會使用PID，因此假如你根本沒有任何微積分的基礎，其實也是可以閱讀這份文件的，真的非常簡單易 懂。

為了要學會PID控制理論，還是建議直接去找來一台可寫程式的機器車 來現場操練，我第一次玩單晶片的時候就是製作出一台8051紅 外線自走車，當時我的自走車走得相當不順利，要是早點知道有這份文件的話，想必功力會更上一層樓，這裡大致介紹需要的硬體設備，一台具有可程式控制的機器 車必須要有三個主要的零件，一、移動平台；二、控制組；三、感測器，在這篇文章裡面，移動平台所需要的馬達是能夠控制正反轉和速度快慢的，而控制組以目前 的DIY玩家們來說會是Arduino、AVR或是8051比較常見，感測器的部分這邊是使用紅外線接收器，有些人會自己搭配電路，自行作出適合使用的紅 外線模組，或是可以直接去網路上購賣適合使用的模組也可以。

[![Basic_bot.](http://www.inpharmix.com/jps/_images/Basic_bot.gif "Basic_bot.")](http://www.inpharmix.com/jps/_images/Basic_bot.gif)

如上圖，上面是一台兩輪機器車的是意圖，A是這台機器車的左輪，C是 右輪，中間那個灰色邊框有紅色小圓圈的就是我剛剛所說的紅外線感測器，而這台車的功能就是循跡，說白話點就是沿著黑線前進，為什麼機器車有辦法做到沿著黑 線走？這是第一次接觸機器人玩具的每個夥伴們常問的問題，機器車怎麼知道那是黑線？而我們要怎麼用程式告訴他們，雖然這和PID控制沒有太大的關連，但是 趁這個機會解釋一下原理，也恰好讓尚未玩過機器車的夥伴們了解為什麼我們需要PID控制理論。

首先在擁有 一個機器 車平台之後，我們會使用紅外線感測器去觀察黑線，通常一個紅外線模組都會有接收器和發射器，藉由發射器發出穩定的紅外線光源，照射在不同的顏色平面上會有 不同的反射量，以上課時老師曾經說過黑色的吸收效果好，白色的反射效果好，因此接收器在觀察黑色的時候會得到較少的紅外線反射量，藉由這樣的方式，機器車 可以分辨現在她所看見的東西有多黑或是有多白，因此控制馬達的正反轉和轉速來達成沿著黑線行走。

紅外線 自走車可以使用一顆紅外線模組就達成巡機自走車的目的，當然也可以為了更精確和更快速而使用更多顆的紅外線模組，但是這份PID控制理論的文件裡面，限制 我們只能夠使用一顆紅外線模組來達成目標，但即使只有使用一顆紅外線模組，只要使用PID控制理論，也能夠讓機器車有相當不錯的效果去達成循跡的目的，當 然到了之後我們可以使用更多的紅外線模組，但是當我們一顆就能夠利用PID做到順暢的行走，那麼使用更多的時候不就更厲害了嗎？

先把你的平台準備好，接著下一篇開始會繼續介紹這份 PID控制理論唷。

Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/pid%e6%8e%a7%e5%88%b6%e7%90%86%e8%ab%96-%e5%9f%ba%e6%9c%ac%e4%bb%8b%e7%b4%b9/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=84&action=edit)

# PID控制理論(2)-P control
====================

[![384009_3810124224093_732240060_n](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)

作者J. Sluka

[http://www.inpharmix.com/jps/PID\_Controller\_For\_Lego\_Mindstorms_Robots.html](http://www.inpharmix.com/jps/PID_Controller_For_Lego_Mindstorms_Robots.html)

準備好了上前一篇所說的機器人平台之後。

接著就準備開始控制了，但是我們還不會這麼快就進入PID控制，我們會先使用一個最簡單的控制方式，也就是”非黑即白”的控制方式，首先我們的紅外線模組，可以藉由讀取到不同比例的紅外線反射量來判別是否為黑線，如圖片一，我用數字來舉例，當紅外線感測器放在完全黑色的線上面，感測器讀取到40，而當放在完全白色的地毯上的時候，感測器讀取到50，而當我有一半看到黑色，有一半看到白色的時候則會讀取到45，因為讀取進來的紅外線反射量恰好是白色反射和黑色反射的平均值。

![](http://3.bp.blogspot.com/-0hZGO-WN9is/UBDOB4UqAmI/AAAAAAAAAI4/RV9_uXuSdd0/s1600/redline.gif)

圖一

經過簡單的測量知道，當數字越接近40則表示車子越靠右黑線區域)，當數字越大越接近50時，則表示車子越靠近左(白線區域)，而當車子偏左時，得下指令給車子向右邊走，反之亦然，這邊使用簡單的二分法來決定偏左或是偏右，就是剛剛的黑白平均值(50+40)/2 = 45，這個數值我們稱為offset，當紅外線小於45則我要讓車子左轉，大於的時候要右轉，如圖二。

 ![light_number_line](http://www.inpharmix.com/jps/_images/light_number_line.gif "light_number_line")

圖二

由於是為了沿著黑線前進，關於馬達該下什麼樣的指令，不同的馬達有不同的方式，這邊使用馬達的動力百分比來表示轉速，作者J. Sluka說道，當使用這種方式走直線的時候盡可能讓車子走的不要太快，要走的溫柔一點，否則會有衝出去黑線的情況常常發生(或許看到這邊的時候，各位的車子早就衝出去好幾次了也說不定。

車 子要直走很簡單，只要讓馬達都往前旋轉即可，但是要轉彎怎麼辦？兩輪平台又和我們一般的車子不同，沒有方向盤這種東西，可以去帶動轉向機構。說的沒錯，然 而這樣的機器車平台，比較像是坦克車，只有兩條履帶，但是卻能夠前後左右甚至原地旋轉，以向左轉為例，將右邊的輪子給予50%power，左邊則是給予20%power，此刻車子就會慢慢向左邊前進，或是右邊給30%，左邊給0%，車子就會轉左邊靠近，但不太會往前，後者就是相對於前著更溫柔的走法，更不容易跑出去黑線之外。

其 實走黑線車的最基本架構就是這樣，這就是一台循跡自走車了，但是當你坐好的時候你會感覺十分的氣餒，因為雖然會沿著黑線走，但是實在走的不是很好，總是抖 來抖去的，而且常常還是會跑出去，甚至他在直線的部分其實也未曾走過真正的直走，那何不再多另外弄出一個判別區段是直走呢？沒錯，從這邊開始就是準備和PID接軌的第一步，在此之前全部都是概念和簡單的實作方式，如下圖三，中間多出一塊區域判別走，只有在真的Error很多的時候開始左轉或是右轉，多了這項判別，你將會發現車子的抖動變小了，至少會有一些時候真正開始走直線了。

![light_number_line_2](http://www.inpharmix.com/jps/_images/light_number_line_2.gif "light_number_line_2")

圖三

此刻，你會突然發現，既然三個判別區比兩個好，那個分成四個、五個、六個……不就會越來越好嗎？沒錯，這就是PID的P(Proportion(al))。

 PID_Proportional部分

 ![light_number_line_3](http://www.inpharmix.com/jps/_images/light_number_line_3.gif "light_number_line_3")

圖四

最初使用了2-Level Line Follower 的方式來控制，後來又用了3-Level Line Follower，而效果有越來越好的趨勢，因此接著要讓這個Level變得盡可能越大越好，如圖四來說，Turn表示右邊輪子的圈數減去左邊輪子旋轉的 圈數，而這個Trun在之後將會提供給馬達作為指令參考用，Turn越大則表示右邊的速度得比左邊更快，當這個Level越分越多，漸漸地，你將會發現本 來應該是階梯狀的圖案，漸漸會變成一條有斜率的斜直線。

 斜率公式：y = m * x +b

在數學上面一般會用這樣的方程式來表示一條斜直線， 然後為了讓事情看起來簡單點，將圖四的最右邊那張轉換成新的XY軸。

 ![light_number_line_4](http://www.inpharmix.com/jps/_images/light_number_line_4.gif "light_number_line_4")

圖五

我們將本來的40~50減去他們的平均值45，則變成-5~5，而轉換成這樣之後，我們將X軸的數值稱為ERROR，也就是誤差量，Y軸的部分將設定成轉速差百分比(100% = 1)，因此剛剛的斜率公式變成

y = m * x   or  Turn =  m * error

而 m的計算方式就是(Y軸每單位變化)/(X軸每單位變化)，以上面的例子來說

m = ( -1  –  1 ) / ( 5  –  -5 ) =  – 0.2

 m是一個很重要的 比例常數(proportionality constant)，之後將感測器所讀取到的的資料轉換成error之後就可以藉由這個比例常數將error直接轉換成Turn，這是一件很重要的事情， 而這個m在PID控制理論裡面有一個特別的名字，稱為K，是constant的簡稱，在之後我們還會有另外兩個K也會加進來這個PID控制裡面，K這個數 值是一個轉換值，可以讓輸入進來的數據轉換成Turn。

在PID裡面還有一 件關於P很重要的事情，就是P的範圍大小(proportional range) ，就是線性範圍，在這邊的範例來說，紅外線感測器的proportional range 是40~50，而馬達我們是假設從-100~100，而從proportional range 這個議題中，衍生出兩項重點。

 1.proportional range 越大越好，從剛剛的2-Level和3-Level那邊可以知道，如果可以讓proportional range 越大，則表示我們可以有越多種的速度變化，假如現在車子稍微遠離黑線，他可以稍微修正回來，假如非常嚴重遠離黑線，他就會相對應地強烈的修正回來，因此能 夠有越多變化的話，就能夠讓車子適應更多種的變化(就不怕很彎的轉彎了)。

2.如果超出了proportional range ，那車子會怎麼辦？大致上車子走的方向不會錯，但是計算出來的Turn就不一定正確了，因此我們必須限制車子不要超出proportional range 。

Turn???!!!!! 剛剛就是為了這個Turn弄了半天，但他到底要麼實際應用在車子上面？我現在經過紅外線感測器並且經過一連串的運算取得了Turn，那麼他要怎麼轉成馬達 用的Power%?首先先定義一個新名詞，Tp (Target Power Level) 目標馬力，簡單來說，這個就是直走的時候的速度，接下來將一顆馬達的速度設定為 Tp + Turn 和另外一顆設定為 Tp – Turn，因為有時候馬達再設定正反轉的時候會有相反的狀況發生，如果出現這樣的情況，把 Tp ± Turn的正負號倒過來試試看。

 在進去程式碼之前，先計算我們剛剛說的斜率，也就是K，在這邊的K是表示proportiona，因此稱之為Kp，為了測試我們先粗估error和馬達的Power，當error從0~-5的時候，希望馬達可以從50%~10%。

```
Kp = ( 50 –  0 ) / ( 0 – -5 ) = 10
```

下面的Pseudo Code是來自作者J. Sluka，Pseudo Code for a P-controller(原作者在Kp那邊輸入1000到了後來除100的用意是為了使用浮點樹的關係)

```
Kp = 10                              //Initialize our three variables
offset = 45
Tp = 50
Loop forever
LightValue = read light sensor     //what is the current light reading?
error = LightValue - offset        //calculate the error by subtracting the offset
Turn = Kp * error                 
//the "P term", how much we want to change the motors' power

powerA = Tp + Turn                //the power level for the A motor
powerC = Tp - Turn                //the power level for the C motor
MOTOR A direction=forward power=powerA     
//issue the command with the new power level in a MOTOR block
MOTOR C direction=forward power=powerC     
//same for the other motor but using the other power level

end loop forever                    
//done with this loop, go back to the beginning and do it again
```

由上面可以知道有兩個可調變數和一個常數是關鍵。

offset常數是需要藉由模組編寫過的資料來的或是自行編寫程式製作出來的。

Kp和Tp這兩個可 調變數是需要經過多次的錯誤嘗試才能夠測量出來的，Kp決定當車子偏離軌道時，所修正回來的強度，Tp則是車子在直線行走的速度，在不同的場合所需要的 Kp和Tp是不相同的 ，當路徑大多是直線的時候，Tp可以調大一點，Kp可以小一些，反之，當遇到很多大轉彎，則需要Tp小一點，Kp大一點。

最後總結一下

P control 有幾個重點

1.輸入的動態範圍要大點比較好，以本例子來說，也就是紅外線40~50的這個範圍要大一點，能看得越多，因為輸入的動態範圍就直接影響到Error的範圍，這將決定我們能夠有多少的辨識條件。

2.輸出的動態範圍也得大一點，不然即使有了很大的輸入動態範圍，結果馬達卻只能夠作正反轉的輸出，那麼就一切都免談了，又回到之前說的2-Level的模式，所以說輸入輸入的動態範圍要盡可能的大，但是這兩者還是要能夠互相匹配才能夠互相發揮良好的作用。

3. 接著這是之前都沒提過的部分，程式的所在地，控制板，它的系統運作速度不能夠太慢，否則當車子都跑出去後他才說趕快回來，那也是白白浪費了P control 的強大效益了。

大家先試玩看看吧~~加油!!!!!!下一篇就會開始寫  I control進來囉

Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/pid%e6%8e%a7%e5%88%b6%e7%90%86%e8%ab%962-p-control/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=85&action=edit)

# PID控制理論(3)-I control
====================

[![384009_3810124224093_732240060_n](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)

作者J. Sluka  
[http://www.inpharmix.com/jps/PID\_Controller\_For\_Lego\_Mindstorms_Robots.html](http://www.inpharmix.com/jps/PID_Controller_For_Lego_Mindstorms_Robots.html)總算到了下一篇了，由於最近大學系上有其他機器人的相關活動，就一直沒空來好好寫這一篇  I control，害大家PID只學了一半，不過雖然只有P control，想必效果已經十分的好了，再加上 I control 一定會更厲害的。如果說 P 表示當下發生的錯誤，那麼 I 就可以說是過去的錯誤， 人們除了藉由當下發生的錯誤學到經驗，假如可以藉由歷史的事件來修正錯誤，想必更能夠讓自身走上所謂的正道吧。

I = Integral

integral 表示積分的意思，如果學過微積分的話很容易理解這是什麼，但是作者J. Sluka 最初的本意是希望可以讓沒有學過微積分的孩子們也可以輕鬆理解，因此這邊使用很直覺的方式來說明什麼是 I control。

最簡單的積分，就是將每次的錯誤加起來，利用下圖舉例說明。

![](http://2.bp.blogspot.com/-YQMob80AGBs/UCpolxIwBjI/AAAAAAAAAMg/m5rghFq6QAI/s1600/2012-08-14_230159.jpg)

在這裡我取得五個數值，分別為-1,-4,5,3,-2，然後我把他們全部加起來就是所謂的 I control的誤差，(-1) + (-4) + 5 + 3 + (-2) = 1 ，就是這個算出來的 1 。

用程式語言的方式來表示：

integral = integral + error

這樣表示我們將每一次的誤差量都記錄在integral這個變數裡面，藉由這個integral來作為PI control的判斷。

下列是一個最基本的PI control 的式子

Turn = Kp*(error) + Ki*(integral)

如同 P control 一樣，error 會乘上一個 Kp值 ，而 integral 也會乘上一個 Ki。

而 究竟為什麼需要integral值呢？他帶來什麼樣的效果？假如我們的車子使用P control已經很靠近了黑白線的交錯區，但是還是有一點點的些微誤差，例如error總是1，那麼我們的integral就會不斷的增加，進而增加 Turn 的數量，那麼我們就可以在把這樣的微小誤差給修正回來，integral就是為了這樣的目的而加進來的。

剛 剛才說integral是為了微小誤差而存在的，但是事情總是優點缺點共存，他可以記起來以前所有的錯誤，同時表示微小的誤差將會大大的影響我們的 Turn，即使我們早就走在正確的黑白交錯區了，還是會受到之前的影響而開始走偏，因此作者就說 The integral has a memory like an elephant，Integral 的記憶力像隻大象一樣好，但是我們有時候希望他健忘點，可以稍微忘記以前做錯的事情，甚至讓他漸漸地淡忘掉，這樣才不會許久之前的錯誤一直影響到現在的結 果，但是!!!!!?????我們要如何讓這隻大象健忘點？在程式方面有個簡單好用的方式。

integral = (2/3)*integral + error

在integral的前面乘上一個小於1的分數，這樣一來之前的記憶就會不斷地變小，就可以稍微減輕剛剛說的那種效應的產生囉，當然，相對的得犧牲本來的integral的反應速度了。

下面的 Pseudo Code是來自作者J. Sluka  

```
Kp = 1000                            ! REMEMBER we are using Kp*100 so this is really 10 !
Ki = 100                             ! REMEMBER we are using Ki*100 so this is really 1 !
offset = 45                          ! Initialize the variables
Tp = 50
integral = 0                         ! the place where we will store our integral
Loop forever
   LightValue = read light sensor    ! what is the current light reading?
   error = LightValue - offset       ! calculate the error by subtracting the offset
   integral = integral + error       ! our new integral term
   Turn = Kp\*error + Ki\*integral     ! the "P term" and the "I term"
   Turn = Turn/100                   ! REMEMBER to undo the affect of the factor of 100 in Kp !
   powerA = Tp + Turn                ! the power level for the A motor
   powerC = Tp - Turn                ! the power level for the C motor
   MOTOR A direction=forward power=powerA  ! actually issue the command in a MOTOR block
   MOTOR C direction=forward power=powerC  ! actually issue the command in a MOTOR block
 end loop forever                    ! done with this loop, go back to the beginning and do it again.
```


Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/pid%e6%8e%a7%e5%88%b6%e7%90%86%e8%ab%963-i-control/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=86&action=edit)

# PID控制理論(4)-D control
====================

[![384009_3810124224093_732240060_n](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)

作者J. Sluka  
[http://www.inpharmix.com/jps/PID\_Controller\_For\_Lego\_Mindstorms_Robots.html](http://www.inpharmix.com/jps/PID_Controller_For_Lego_Mindstorms_Robots.html)

P如果表示現在的錯誤，I則表示過去的錯誤

那麼D則是表示未來的錯誤!!??沒錯~~這就是我們接下來要說的

D = derivative

他就是微分，利用微分的方式，可以預測數值接下來的發展  
例如以前國中的時候不是學過加速度或是速度嗎？  
物體的位移函數利用微分可以求得速度和加速度  
而利用速度或是加速度我們就能夠知道物體將會怎麼移動對吧?~

不過目前是基於大家不能理解微分的情況下，因此這邊來說明一下什麼是微分???

微分可以看清楚趨勢，也就是未來會發生什麼事情

舉例來說

題目一!!

1 2 3 4 5 6 7 8 下一個數字是多少 ?????

依照這樣的趨勢來說，你會覺得是9吧@@!!!!!!!!

(希望你也這麼覺得，不然說不下去了)

因為依照+1的這個趨勢發展著，所以自然而然會覺得下一個數字是9

如何利用微分來知道這樣的+1怎麼來的呢？

趨勢＝(現在的偏差值) －(過去的偏差值)

如同剛剛的12345678一樣

8-7 = 1

換個題目來試試看吧

題目二

第一個數值 2

第二個數值 5

依造這樣的數據我們來猜猜第三個數值為何??

5-2 = 3

因此他們是依造每次+3的規則來累加的，所以第三個數值則是第二個數值+3，也就是8，這是題目二的答案。

在題目二提到一個關鍵的事情，在知道”趨勢”之後，要如何預測下一組答案？

也就是將    未來的偏差值＝趨勢＋現在的偏差值

我們將此D用PID控制裡面的稱呼方式來說的話，稱之為Kd

從此之後我們完成了PID控制了(QWQ總算完成了)

馬達旋轉量(Turn) = Kp * (現在的偏差量) + Ki * (過去的偏差量) + Kd * (未來的偏差量)

Kd這個變數是怎麼在我們控制的過程中發揮功能呢？  
在趨勢越來越糟糕的時候（趨勢的數值離0很遠），也就是例如車子嚴重往線外跑出去的時候Kd的數值會變很大，以此去將車子修正回來，如果趨勢越來越好的時候（也就是說趨勢接近0的時候），車子應該要停止修正錯誤，否則就會導致過度修正。

下面的 Pseudo Code是來自作者J. Sluka

    Kp = 1000                             ! REMEMBER we are using Kp*100 so this is really 10 !
    Ki = 100                              ! REMEMBER we are using Ki*100 so this is really 1 !
    Kd = 10000                            ! REMEMBER we are using Kd*100 so this is really 100!
    offset = 45                           ! Initialize the variables
    Tp = 50 
    integral = 0                          ! the place where we will store our integral
    lastError = 0                         ! the place where we will store the last error value
    derivative = 0                        ! the place where we will store the derivative
    Loop forever
       LightValue = read light sensor     ! what is the current light reading?
       error = LightValue - offset        ! calculate the error by subtracting the offset
       integral = integral + error        ! calculate the integral 
       derivative = error - lastError     ! calculate the derivative
       Turn = Kp*error + Ki*integral + Kd*derivative  ! the "P term" the "I term" and the "D term"
     Turn = Turn/100                      ! REMEMBER to undo the affect of the factor of 100 in Kp, Ki and Kd!
       powerA = Tp + Turn                 ! the power level for the A motor
       powerC = Tp - Turn                 ! the power level for the C motor
       MOTOR A direction=forward power=PowerA   ! actually issue the command in a MOTOR block
       MOTOR C direction=forward power=PowerC   ! same for the other motor but using the other power level
       lastError = error                  ! save the current error so it can be the lastError next time around
    end loop forever                      ! done with loop, go back and do it again.
    

Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/pid%e6%8e%a7%e5%88%b6%e7%90%86%e8%ab%964-d-control/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=87&action=edit)

# PID控制理論(5)-調整PID參數

[![384009_3810124224093_732240060_n](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/384009_3810124224093_732240060_n.jpg)

作者J. Sluka  
[http://www.inpharmix.com/jps/PID\_Controller\_For\_Lego\_Mindstorms_Robots.html](http://www.inpharmix.com/jps/PID_Controller_For_Lego_Mindstorms_Robots.html)

前面幾篇說了這麼多了，但是說歸說，做歸做，數學理論雖然重要，但是這邊為了讓每個人都能夠使用PID，所以不需要很複雜的計算(不需要學完微積分、工程數學和自動控制)，即可製作出PID控制的小車唷。

其實如何調整的方式很多，最後作者J. Sluka 他決定使用Ziegler–Nichols Method，來調整PID的每個參數。請各位夥伴依照下列步驟進行。

1.請先將Ki和Kd的數值調整成0，這樣系統就變成單純的P控制。

2.Kp值就先抓個合理的數值填寫進去。(因為我們等等就要來trial and error)

那什麼是合理的數值？…….

下面舉兩個例子

*    假如我給馬達100單位的訊號，馬達將會轉到最大值的話，而我的偏差量範圍為±5單位，那就100/5 = 20，這個20就是我的Kp值。

*   你就隨便給個1~100的單位，看看會發生什麼事情XP（錯誤嘗試法最高奧義）

3. 把你的機器人啟動，這邊以他是一台循跡自走車的觀點來說明，假如他不能沿著線行走，遇到轉彎會有來不及彎過來的情形，也就是說他想要修正卻來不及修正，這 時提高你的Kp值，反之，你的車子有很狂野的修正，也就是他根本在轉彎的時候狂轉彎，在直走的時候一不小心碰到黑線也在狂轉彎，那麼就表示Kp直太高了， 請調低一點，而最後要調整成它會沿著線走，並且明顯地S行走法，那就表示你成功了，此刻的Kp又稱之為Kc（critical gain）。

4. 你的小車車會在那邊不斷的S行走法而不脫離軌道時，接下來你得開始測量一項數據，也就是他一次S行走法的時間，又稱之為Pc，以作者J. Sluka他的小車來說，這個數值是0.5秒一個週期。

5.接下來計算你的程式多久跑一個週期，也就是說，每隔多久時間他會調整一次Turn這個數值？例如你可以設定你的程式碼跑10000次，並且在迴圈外的前後夾兩行顯示時間的指令，這樣一來只要將前後兩個時間相減，並且除去10000之後即會得到程式執行一次的時間。

 6.接著只要依造下表去進行Kp、Ki和Kd的計算並且帶入到你的機器人裡面。

Ziegler–Nichols method giving K’ values  
(loop times considered to be constant and equal to dT)

| Control Type |   Kp   |     Ki’     |      Kd’     |
|:------------:|:------:|:-----------:|:------------:|
|       P      | 0.50Kc |      0      |       0      |
|      PI      | 0.45Kc | 1.2KpdT/ Pc |       0      |
|      PID     | 0.60Kc |  2KpdT / Pc | KpPc / (8dT) |

如果你只想要P控制，就使用P control type，如果你只需要PI控制，那就選擇PI control type，當然在這邊先試試看PID control type囉。(這邊的Ki’和Kd’表示著他們已經包含進去dT的時間，也就是每次取樣的時間有被計算進去，也因此他們不是實際的Ki和Kd值，不過不用擔心，我們不需要管這個，還是依先前說的那個公式帶進去即可唷。)

公式如下：

馬達旋轉量(Turn) = Kp * (現在的偏差量) + Ki * (過去的偏差量) + Kd * (未來的偏差量)

7.啟動你的小車吧，看看他會怎麼奔跑!!

8.當一切順利的時候，就可以調高你的車子平均跑速(也就是你走直線的速度)，再接著跑回去第一步驟依序嘗試下來，不斷的嘗試結果就會是一台勇猛的跑車囉。

以上八步驟就完成PID的調變囉~~~

——————————-

作者後來有分享一下微調每個參數會有什麼樣的後果，這邊僅列出表格，剩下的大家就自己參考囉。

提高變數的影響

| 變數 | 上升時間 | 過衝時間 | 穩定時間 | 不穩定誤差 |
|:----:|:--------:|:--------:|:--------:|------------|
|  Kp  |   下降   |   上升   |  小變化  | 下降       |
|  Ki  |   下降   |   上升   |   上升   | 消除       |
|  Kd  |  小變化  |   下降   |   下降   | 無         |

上升時間：車子改變偏差量速度

過衝時間：車輛超線的時間量

穩定時間：遇到大變化時回復所需時間量

不穩定誤差：車子處於有誤差量卻沒有修復回來的時間

參考資料

Ziegler–Nichols Method

[http://en.wikipedia.org/wiki/Ziegler%E2%80%93Nichols_method](http://en.wikipedia.org/wiki/Ziegler%E2%80%93Nichols_method)