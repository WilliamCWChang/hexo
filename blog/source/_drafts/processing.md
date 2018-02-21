---
title: processing
tags: coding
---

# Processing中文化(1)-Basics-Arrays-Array
====================================

Basics-Arrays-array

中文化的程式碼

    /**
     * 陣列
     * 
     * 陣列是由一連串的資料所組成，陣列裡面的每一個資料都有索引數值(index)來
     * 代表他在陣列中的位置。陣列的索引值，也就是它的位置，是由數字0開始
     * 編號，因此第一個資料的位置是0，第二個資料的位置是1，其次依此類推。
     * 在這個範例裡面，我們設立一個名為coswave的陣列，並且將cos(餘弦)函數輸
     * 入進去，並且將資料以三種不同的方式在圖片中顯示。
     * 
     * 
     * 翻譯者：RobotRabbit 張家瑋 2013.3.11
     */
    
    float[] coswave; 
    
    void setup() {
      size(640, 360); // width(寬)=640 height(高)=360 
      coswave = new float[width]; //定義coswave為一維640個空間的矩陣
      for (int i = 0; i < width; i++) {
        float amount = map(i, 0, width, 0, PI);
        coswave[i] = abs(cos(amount));
      }
      background(255); //設定背景顏色為白色
      noLoop();  //繪圖部分只執行一次
    }
    
    void draw() {
    //第一張圖片
      int y1 = 0;
      int y2 = height/3;
      for (int i = 0; i < width; i+=2) {
        stroke(coswave[i]*255);    //stroke(值) = 灰階, stroke(值, 值, 值) = 彩色
        line(i, y1, i, y2);        //line(x1,y1,x2,y2) 表示從(x1,y1)畫一條直線到(x2,y2)
      }
    //第二張圖片
      y1 = y2;
      y2 = y1 + y1;
      for (int i = 0; i < width; i+=2) {
        stroke(coswave[i]*255 / 4);
        line(i, y1, i, y2);
      }
    //第三張圖片
      y1 = y2;
      y2 = height;
      for (int i = 0; i < width; i+=2) {
        stroke(255 - coswave[i]*255);
        line(i, y1, i, y2);
      }
    }
    
    

執行結果：

[![2013-03-11_185251](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_185251.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_185251.gif)

前言：

想說自己既然都要看了，就順便整理一下資料也方便大家快速學習，基本上processing裡面的程式碼和英文都算是很淺顯易懂了，但是想必中文化多一些應該可以更引起大家對於使用processing的熱情吧。

正題：

這篇程式碼的目的在於說明什麼是矩陣，並且以圖像化來表示，以最單純的黑白來說，電腦裡面將黑色和白色定義成0和255，也就是說黑色就是0，表示沒有任何光線，白色255表示光線最多，而0~255之間所有的數字各自表示著各種亮度，越靠近255表示光線越亮越靠近白色，反之亦然。

我們可以從程式碼跑出來的結果來看，它分成三大段區塊，他是以cos函數作為顏色的基礎去繪圖的，可由我下方的before圖片來看，他首先利用map這個函數將視窗寬度(width)內插到0~pi，因此出現了before這張圖片，但是根據前述的定義，我們只有0~255有定義顏色，因此不能夠有負號，他再利用絕對值函數abs()將其轉換成after1的這張圖片，這也是Processing所跑出來的第一張圖片，接著他將亮度全部除以四，因此亮度全部下降，可以看得出來after2的數值最大只有到0.25，屆時呈上255之後的數字自然都下降了四倍，最後我們可以看到黑白反轉的現象，由after3可知黑白效果調換。

[![array](http://www.tabbymeow.com/wp-content/uploads/2013/04/array.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/array.jpg)

除此之外，大家一定對於有些函數依然有問題，我在這邊提供一些我認為會用得到的函數解釋連結。

[Array 的宣告](http://processing.org/reference/Array.html)  
[http://processing.org/reference/Array.html](http://processing.org/reference/Array.html)

[stroke](http://processing.org/reference/stroke_.html)  
[http://processing.org/reference/stroke_.html](http://processing.org/reference/stroke_.html)

[map](http://processing.org/reference/map_.html)  
[http://processing.org/reference/map_.html](http://processing.org/reference/map_.html)

Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/processing%e4%b8%ad%e6%96%87%e5%8c%96-basics-arrays-array/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=103&action=edit)

# Processing中文化(2)-Basics-Arrays-Array2D
======================================

Basics-Arrays-Array2D

中文化的程式碼

    /**
     * 二維矩陣
     * 
     * 在這邊示範如何定義一個二維矩陣，數值在2維矩陣具有兩個索引值來表示空
     * 間，2維矩陣對於圖片的儲存是相當有用的，在這個範例裡面，每個點的顏色
     * 將會和圖片中心距離有所關聯。
     * 
     * 翻譯者：RobotRabbit 張家瑋 2013.3.11
     */
    
    float[][] distances;
    float maxDistance;
    int spacer; //點與點之間的距離。
    
    void setup() {
      size(640, 360);
      maxDistance = dist(width/2, height/2, width, height);      // dist(x1,y1,x2,y2) 的值是指 (x1,y1)到(x2,y2)的距離
      distances = new float[width][height];      // 定義distance這個二維矩陣
      // 對圖片上每個點都存入一個0~255之間的數字，距離中心點越遠其數字越大
      for (int y = 0; y < height; y++) {
        for (int x = 0; x < width; x++) {
          float distance = dist(width/2, height/2, x, y);
          distances[x][y] = distance/maxDistance * 255;
        }
      }
      spacer = 10; // 每個白點距離10個像素
      noLoop();  // 執行一次並停止畫圖
    }
    
    void draw() {
      background(0);
      //這個迴圈之內跳過許多陣列裡面的數值，因此所畫出來圖片中的點點少於矩陣的資料
      //如果你更改spacer的數值，來調整圖片中點點的密度，越小密度越高。
      for (int y = 0; y < height; y += spacer) {
        for (int x = 0; x < width; x += spacer) {
          stroke(distances[x][y]);
          point(x + spacer/2, y + spacer/2); 
          // 上列你可以改成point(x, y);，乍看之下沒有什麼改變，但是點點顯示的位置不同了
        }
      }
    }
    

結果：

[![2013-03-11_204300](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_204300.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_204300.gif)

你可以試著修改 background(0); 變成 background(255);，調整背景值會有不同的效果。

[![2013-03-11_204414](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_2044141.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_2044141.jpg)

你可以試著修改 spacer 這個數值的大小，像是他本來是 spacer = 10; 我將其修改成spacer = 1;之後所得到的效果就相當不錯，他將會把整個圖片變得很柔和。

[![2013-03-11_204332](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_204332.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-11_204332.gif)

Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/processing%e4%b8%ad%e6%96%87%e5%8c%96-basics-arrays-array2d/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=119&action=edit)

# Processing中文化(3)-Module、類別與物件
=============================

在Basics-Arrays-ArrayObjects之前先來這份教學文件，否則到後面會有些地方看不太懂。

這篇章裡面會開始提到Class的應用，由於我目前也不算是很熟悉這Class的使用方式，所以才想開始寫點Pocessing的中文化，順便提升自己程式碼的應用能力，如果在解釋的過程中有些問題的話也麻煩各位協助協助我，好讓這份中文化的資料能夠更加完整。

因為在Basics-Arrays-ArrayObjects會開始使用Module這個Class，那什麼是Class呢？Class中文名稱叫做類別，提到了類別那就得說Object物件物件是一個”東西”，而那個”東西”有些特質，我們可以利用那些特質卻做某些事情。類別是描述”東西”特質的方法，也就是描述他是一個怎麼怎麼樣的東西。口語化的方式來說，我有一台腳踏車，腳踏車是一個物件，我可以利用它省力地去上學，類別則是描述腳踏車是什麼？腳踏車有兩個輪子，並且利用齒輪和鍊條所帶動的一種交通工具。

防止自己的文章有描述不清楚的情況發生，以下是關於類別和物件的參考網站，歡迎大家參考討論

http://dns2.asia.edu.tw/~wzyang/slides/Java/Chen/SE7ch07.pdf

http://blog.miniasp.com/post/2009/08/27/OOP-Basis-What-is-class-and-object.aspx

http://openhome.cc/Gossip/JavaGossip-V1/ClassABC.htm

以下這份是Basics-Arrays-ArrayObjects裡面的一個Class

    class Module {
      int xOffset;
      int yOffset;
      float x, y;
      int unit;
      int xDirection = 1;
      int yDirection = 1;
      float speed; 
    
      // Contructor
      Module(int xOffsetTemp, int yOffsetTemp, int xTemp, int yTemp, float speedTemp, int tempUnit) {
        xOffset = xOffsetTemp;
        yOffset = yOffsetTemp;
        x = xTemp;
        y = yTemp;
        speed = speedTemp;
        unit = tempUnit;
      }
    
    

從這邊開始使用class來定義Module這個物件，class具有屬性(Property)和「方法」(Method)，屬性就是前面說的他的性質，而我們可以利用它擁有的方法來進行我們要的功能，例如腳踏車可以騎，”騎車”這樣的動作可以稱之為方法。

我們來看看他有什麼性質好了，

      int xOffset;
      int yOffset;
      float x, y;
      int unit;
      int xDirection = 1;
      int yDirection = 1;
      float speed; 
    
      // 建構子(或稱之建構方法 ,Contructor)
      Module(int xOffsetTemp, int yOffsetTemp, int xTemp, int yTemp, float speedTemp, int tempUnit) {
        xOffset = xOffsetTemp;
        yOffset = yOffsetTemp;
        x = xTemp;
        y = yTemp;
        speed = speedTemp;
        unit = tempUnit;
      }
    

從建構子裡面發現會在一開始建立Module的時候，給予下列幾個屬性。

1\. x和y：與相對原點的距離

2\. xOffset和yOffset：相對原點和絕對原點的位移量

3\. speed：點的移動速度

4\. unit：點的移動距離被限制在0~unit之間

接著來看看Module的方法

      // 更新變數的方法
      void update() {
        x = x + (speed * xDirection);
        if (x >= unit || x <= 0) {
          xDirection *= -1;
          x = x + (1 * xDirection);
          y = y + (1 * yDirection);
        }
        if (y >= unit || y <= 0) {
          yDirection *= -1;
          y = y + (1 * yDirection);
        }
      }
    
      // 繪畫物件的方法
      void draw() {
        fill(255);
        ellipse(xOffset + x, yOffset + y, 6, 6);
      }
    

他總共有兩種方法，一個是更新變數的方法和繪畫物件的方法，一個方法裡面所寫的是點的移動方式，第二個而是物件繪圖的方式。

接著要怎麼使用這個Class呢？你必須將這個Class的pde檔案和自己所要編寫的sketch放在一起。

[![2013-03-27_175701](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-27_1757011.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-27_1757011.gif)

接著我寫了一個小程式來顯示Module的各個數值。

    Module[] mods; //使用名為Module的Class
    int unit = 20;
    void setup()
    {
      size(640, 360);
      noStroke();
      mods = new Module[2];
      mods[0] = new Module(1, 2, 3, 4, 5, 6);
      mods[1] = new Module(7, 8, 9, 10, 11, 12);
      noLoop();
    }
    
    void draw()
    {
      background(0);
      println("Program Start");
      println("mods = ");
      println(mods);
      print("mods[0] = ");
      println(mods[0]);
      print("mods[0].xDirection = ");
      println(mods[0].xDirection);
      print("mods[0].yDirection = ");
      println(mods[0].yDirection);
      print("mods[0].xOffset = ");
      println(mods[0].xOffset);
      print("mods[0].yOffset = ");
      println(mods[0].yOffset);
      print("mods[0].x = ");
      println(mods[0].x);
      print("mods[0].y = ");
      println(mods[0].y);
      print("mods[0].speed = ");
      println(mods[0].speed);
      print("mods[0].unit = ");
      println(mods[0].unit);
    
    }
    

這是輸出的結果  
Program Start

mods =

\[0\] ArrayObject$Module@136a1a1

\[1\] ArrayObject$Module@1ad6b4b

mods\[0\] = ArrayObject$Module@136a1a1

mods\[0\].xDirection = 1

mods\[0\].yDirection = 1

mods\[0\].xOffset = 1

mods\[0\].yOffset = 2

mods\[0\].x = 3.0

mods\[0\].y = 4.0

mods\[0\].speed = 5.0

mods\[0\].unit = 6

從程式碼來看，我定義了mods這個物件矩陣，裡面儲存了mods\[0\]和mod\[1\]，而我後來利用建構子定義了mod\[0\]裡面的屬性，因此可以看見我所呼叫那些屬性資料裡面，出現了我定義了資料。

Posted on [April 6, 2013](http://192.168.1.233/2013/04/06/processing%e4%b8%ad%e6%96%87%e5%8c%963-module%e3%80%81%e9%a1%9e%e5%88%a5%e8%88%87%e7%89%a9%e4%bb%b6/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=168&action=edit)

# Processing中文化(4)-Basics-Arrays-ArrayObjects
===========================================

Basics-Arrays-ArrayObjects

本篇請參照Pocessing中文化(3)-Module、類別與物件服用

中文化的程式碼

    /**
     * 物件矩陣
     * 
     * 示範如何定義自行編寫的物件矩陣
     */
    
    int unit = 40;  //建立每個點物件的距離
    int count;
    Module[] mods; //使用名為Module的類別(Class)
    
    void setup() {
      size(640, 360);  //建立視窗並且給定視窗大小值
      noStroke(); //去除邊線
      int wideCount = width / unit;   //  640/40 = 16
      int highCount = height / unit;  //  360/40 = 9 
      count = wideCount * highCount;  //此數量為空間中的點數量  ，16*9 = 144 個點 
      mods = new Module[count];  //mods為一個矩陣物件，可視為由144個點物件所組成的物件矩陣(Array Objects) 
    
      int index = 0;
      for (int y = 0; y < highCount; y++) {
        for (int x = 0; x < wideCount; x++) {
          mods[index++] = new Module(x*unit, y*unit, unit/2, unit/2, random(0.05, 0.8)*50, unit);
          //Module(int xOffsetTemp, int yOffsetTemp, int xTemp, int yTemp, float speedTemp, int tempUnit)
          //利用Module建構子對於每個屬性進行定義。
        }
      }
    }
    
    void draw() {
      background(0);
      for (int i = 0; i < count; i++) {
        mods[i].update();   //更新mods物件矩陣裡面各個資料的屬性
        mods[i].draw();     //對mods物件矩陣裡面各個資料繪圖
      }
    }
    
    

[![2013-03-27_192555](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-27_1925551.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-03-27_1925551.gif)

這個程式最主要的目的是讓大家知道該如何創造出物件矩陣，因為在圖片中的每一個點點都是分別獨立的點點，他們最初一開始的位置、速度和邊界都可以被分別定義，如果我們總是使用以前的定義資料的方式，那麼在這邊的144個點點我們將要個別定義他的位置(原點的位移和與相對原點的位移量共四個)、速度和邊界，那麼將要花費144*6 = 864個定義，這種作法不僅不實際，在修改的過程中也會造成許多問題和麻煩，因此Pocessing讓我們在Basic的章節裡面盡早學會怎麼使用物件矩陣的定義方式。

而程式執行之後的結果是，圖片中間的每個點的移動速度都不同，並且會在我們選定的範圍內移動，呈現「弓」字形的移動方式不斷往下移動，最後再折返回去。

Posted on [April 7, 2013](http://192.168.1.233/2013/04/07/processing%e4%b8%ad%e6%96%87%e5%8c%964-basics-arrays-arrayobjects/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=172&action=edit)

# Processing中文化(5)-Processing怎麼用?
===============================

我也沒有買那本Processing handbook，所以算是自行猜測書中的講解囉，大家有空就看看吧。

[![2013-04-08_151421](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_151421.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_151421.gif)

    line(10, 80, 30, 40);  // 左邊的線
    line(20, 80, 40, 40);
    line(30, 80, 50, 40);  // 中間的線
    line(40, 80, 60, 40);
    line(50, 80, 70, 40);  // 右邊的線
    

line是我們的畫線指令，該如何畫上線條呢？

根據Processing官方網站上面的資料 [line()](http://www.processing.org/reference/line_.html)，line(x1, y1, x2, y2)的指令長這樣，因此我們需要給定兩個點，Processsing 就會在圖片上面顯示一條線，也就是在(x1,y1)和(x2,y2)之間拉上一條線。

![2013-04-08_152608](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_152608.gif)

接著如果我希望換個風格呢???勢必得調整＂背景顏色＂和＂線條顏色與粗度＂了。

    background(0); // 設定為黑色背景
    stroke(255); // 設定線條為白色
    strokeWeight(5); // 線條寬度為 5 pixels
    smooth(); // 光滑邊緣
    line(10, 80, 30, 40); // 左邊的線
    line(20, 80, 40, 40);
    line(30, 80, 50, 40); // 中間的線
    line(40, 80, 60, 40);
    line(50, 80, 70, 40); // 右邊的線
    

這邊介紹了新的四個指令。

*   [background()](http://processing.org/reference/background_.html)
*   [stroke()](http://processing.org/reference/stroke_.html)
*   [strokeWeight()](http://processing.org/reference/strokeWeight_.html)
*   [smooth()](http://processing.org/reference/smooth_.html)

background表示的就是背景；stroke表示的是線，而裡面所放置的參數值稱之為亮度，最大值是255，最小值是0，因此不用特別說明就可以知道，沒有亮度就是黑色，最亮就是白色了，strokeWeight表示的是線的寬度，平常預設值是1，smooth則是光滑邊緣的效果，他預設是打開的，因此將smooth註解掉並看不出來有什麼影響，因此你可以將其換成

*   [noSmooth()](http://processing.org/reference/noSmooth_.html)

那麼smoooth的功能就會被取消掉。

[![2013-04-08_160526](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_160526.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_160526.gif)

反過頭來想看看，如果說我想要平移這些線條，那麼我不就得將這五條線重新給座標嗎？這樣其實一點也不方便!!

所以除了直接用常數給定座標的方式之外，我們可以用變數的方式來給定座標。

    int x = 5; // 設定橫坐標的相對原點X
    int y = 60; // 設定縱座標的相對原點Y
    line(x, y, x+20, y-40); // Draws line from [5,60] to [25,20]
    line(x+10, y, x+30, y-40); // 畫線從[15,60] 到 [35,20]
    line(x+20, y, x+40, y-40); // 畫線從[25,60] 到 [45,20]
    line(x+30, y, x+50, y-40); // 畫線從[35,60] 到 [55,20]
    line(x+40, y, x+60, y-40); // 畫線從[45,60] 到 [65,20]
    

從這邊我們來看看，我們先設定一個橫坐標和縱座標的相對原點，接著再將線條以這個相對原點(x,y)去進行畫線，將來我們想要移動這些線條的時候就顯得方便多了。

[![2013-04-08_161215](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_161215.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_161215.gif)

你看吧，我只是將x改成20，y改成100，就可以直接移動圖片，這樣的程式寫作方式將會帶給我們相當多的便利性。

剛剛提到說，如果可以輕鬆移動圖片？那麼我乾脆來畫動畫好了？動畫其實不是真正東西在動，那是一種利用人眼的錯覺來達成的效果，也就是當畫面的更換速度超過人眼可以辨識的速度時，我們就會誤以為他們在動，也就是利用你一秒鐘看到很多張圖片的過程中，將每張圖片都稍微做小動作的偏移，你就會以為那張圖片在動，那麼我只要更改我剛剛說的相對座標，每次都只修改一點點，那麼你就會覺得線在移動了~~

[![動畫](http://www.tabbymeow.com/wp-content/uploads/2013/04/e58b95e795ab.png?w=519)](http://www.tabbymeow.com/wp-content/uploads/2013/04/e58b95e795ab.png)

    int x = 0; // 設定橫坐標的相對原點
    int y = 55; // 設定縱坐標的相對原點
    
    void setup() {
      size(100, 100); //設定圖框大小100 X 100 pixels
    }
    
    void draw() {
      background(204);
      line(x, y, x+20, y-40); // 左線
      line(x+10, y, x+30, y-40); // 中線
      line(x+20, y, x+40, y-40); // 右線
      x = x + 1; // 每次執行到這行的話x+1
      if (x > 100) { 如果x>100，讓x指定為-40
        x = -40; 
      }
    }
    

一樣利用我們剛剛所說的設定相對縱橫坐標原點，不過接下來突然出現一個之前沒有看過的＂格式＂。

*   [void setup()](http://processing.org/reference/setup_.html)
*   [void draw()](http://processing.org/reference/draw_.html)

在下面的大括號{}裡面寫程式，基本上在這個階段你可以直接認為setup就是只會執行一次的程式，而draw就會不斷地執行，也就是你可以畫動畫的地方。

在setup()的部分，我們利用[size()](http://processing.org/reference/size_.html)來設定圖框大小，他的預設值是100×100，單位是pixels，他通常會是第一行程式碼，因為我們總要知道圖畫紙多大張之後才開始畫畫阿。

除了能夠做動畫，我希望我還能夠用我的外部裝置來控制，可以嗎？？？？？例如想要用滑鼠和圖片做些什麼之類的。

Processing可以做到!!!

    void setup() {
      size(100, 100);
    }
    
    void draw() {
      background(204);
      // 設定x為滑鼠的座標值x
      float x = mouseX;
      // 設定y為滑鼠的座標值y
      float y = mouseY;
      line(x, y, x+20, y-40);
      line(x+10, y, x+30, y-40);
      line(x+20, y, x+40, y-40);
    }
    

這樣就行了!!

其實我們的滑鼠在視窗中移動，可以視為一個點在一個和視窗一樣大的二維空間中移動

[![圖片2](http://www.tabbymeow.com/wp-content/uploads/2013/04/e59c96e789872.jpg?w=300)](http://www.tabbymeow.com/wp-content/uploads/2013/04/e59c96e789872.jpg)

因此利用[mouseX](http://processing.org/reference/mouseX.html)和[mouseY](http://processing.org/reference/mouseY.html)這兩個變數，它裡面存有滑鼠的座標值(X,Y)，我們就能夠讓圖片隨著滑鼠而移動。

[![2013-04-08_165204](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_165204.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_165204.gif)

除了最一開始說的利用變數的方式來移動圖片的位置外，如果我畫好了一張圖(可能是小草)，我希望可以做出有很多小草的感覺，那我不是得又開始複製貼上複製貼上？(雖然這樣也不是不行…..)

我們得開始學會利用＂函式＂，也就是我先將我的圖片寫進去函式裡面，接著只要呼叫他出來就好，呼叫他就會出現小草，這樣多棒啊!!!

    void setup() {
      size(100, 100);
      noLoop();
    }
    
    void draw() {
      diagonals(40, 90);//圖一
      diagonals(60, 62);//圖二
      diagonals(20, 40);//圖三
    }
    
    void diagonals(int x, int y) {
      line(x, y, x+20, y-40);
      line(x+10, y, x+30, y-40);
      line(x+20, y, x+40, y-40);
    }
    

這邊出現diagonals這個＂函式＂，我們只要在裡面編寫好我們想要畫的圖片，再利用參數給資料就能夠將圖一、圖二和圖三很方便地畫出來囉，此外，函式不一定都要命名為diagonals，你可以命名為你喜歡的任何字，但是不能使用Processing已經拿去使用的關鍵字就對了。

除此之外這邊出現新的指令。

*   [noLoop();](http://processing.org/reference/noLoop_.html)

也就是停止畫圖的意思，平常的繪圖中如果沒有使用noLoop()，那麼draw()就會一直繪圖下去。

接下來算是結合以上的超級應用了!!!

    int num = 20;
    int[] dx = new int[num]; // 宣告和創造一個矩陣
    int[] dy = new int[num]; // 宣告和創造一個矩陣
    
    void setup() {
      size(100, 100);
      for (int i=0; i<num; i++) {
        dx[i] = i*5;
        dy[i] = 12 + (i*6);
      }
    }
    
    void draw() {
      background(204);
      for (int i=0; i<num; i++) {
        dx[i] = dx[i] + 1;
        if (dx[i] > 100) { 
          dx[i] = -100; 
        }
        diagonals(dx[i], dy[i]);
      }
    }
    
    //diagonals函式
    void diagonals(int x, int y) {
      line(x, y, x+20, y-40);
      line(x+10, y, x+30, y-40);
      line(x+20, y, x+40, y-40);
    }
    

比較特別的是下面這個，下面這個是Processing宣告矩陣的方式，

    int[] dx = new int[num]; // 宣告和創造一個矩陣
    int[] dy = new int[num]; // 宣告和創造一個矩陣
    

矩陣是一連串相同型態的資料所組成，因此在需要大量呼叫資料的情況時，可以利用矩陣加上for迴圈重複進行操作。

詳細情況可以參考我的Processing中文化(1)-Basics-Arrays-Array

[![2013-04-08_170316](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_170316.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-08_170316.gif)

    Diagonals da, db;
    
    void setup() {
      size(100, 100);
      smooth();
      // Inputs: x, y, speed, thick, gray
      da = new Diagonals(0, 80, 1, 2, 0);
      db = new Diagonals(0, 55, 2, 6, 255);
    }
    
    void draw() {
      background(204);
      da.update();
      db.update();
    }
    
    class Diagonals {
      int x, y, speed, thick, gray;
    
      Diagonals(int xpos, int ypos, int s, int t, int g) {
        x = xpos;
        y = ypos;
        speed = s;
        thick = t;
        gray = g;
      }
      void update() {
        strokeWeight(thick);
        stroke(gray);
        line(x, y, x+20, y-40);
        line(x+10, y, x+30, y-40);
        line(x+20, y, x+40, y-40);
        x = x + speed;
        if (x > 100) {
          x = -100;
        }
      }
    }
    

在最後一部份使用了Class，可以參考Processing中文化(3)-Module、類別與物件。

    class Diagonals {
      int x, y, speed, thick, gray;
    
      Diagonals(int xpos, int ypos, int s, int t, int g) {
        x = xpos;
        y = ypos;
        speed = s;
        thick = t;
        gray = g;
      }
      void update() {
        strokeWeight(thick);
        stroke(gray);
        line(x, y, x+20, y-40);
        line(x+10, y, x+30, y-40);
        line(x+20, y, x+40, y-40);
        x = x + speed;
        if (x > 100) {
          x = -100;
        }
      }
    }
    

在這邊特別說明它裡面的結構，首先在Diagonals這個class裡面，class是由data和method所組成，一般來說Class的字首會大寫”Diagonals”，像是前面的函式就沒有大寫，當然這是一種方便我們之後辨認的程式寫作手法。

      Diagonals(int xpos, int ypos, int s, int t, int g) {
        x = xpos;
        y = ypos;
        speed = s;
        thick = t;
        gray = g;
      }
    

在建構子部分設定了五個data。

      void update() {
        strokeWeight(thick);
        stroke(gray);
        line(x, y, x+20, y-40);
        line(x+10, y, x+30, y-40);
        line(x+20, y, x+40, y-40);
        x = x + speed;
        if (x > 100) {
          x = -100;
        }
      }
    

而updata()這是Diagonals的method，在這裡面寫上關於該怎麼操作Diagonals的Class所建構出來的物件。

Posted on [April 8, 2013](http://192.168.1.233/2013/04/08/processing%e4%b8%ad%e6%96%87%e5%8c%965-processing%e6%80%8e%e9%ba%bc%e7%94%a8/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=521&action=edit)

# Processing中文化(6)-基本繪圖
=====================

[![2013-04-11_172321](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_172321-1024x795.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_172321.gif)

我們先來說說所謂的視窗，也就是電腦影像的一個重要概念，你現在所看見的視窗是由許多＂小方格＂組成，仔細看看你電腦的桌面，很接近看的時候你會發現我說的沒錯，但是這樣可能很傷眼睛，因此我用小畫家幫你放大圖片。

[![2013-04-11_172337](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_172337-1024x714.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_172337.gif)

有沒有發現他開始呈現顆粒了呢？

[![圖片1](http://www.tabbymeow.com/wp-content/uploads/2013/04/圖片1-1024x711.jpg)](http://www.tabbymeow.com/wp-content/uploads/2013/04/圖片1.jpg)

放到這麼大就可以清清楚楚看到，剩餘32.3GB這行字裡面的＂剩＂完全變成由小格子所組成的圖片了，而這一小格就是我們稱之為的像素，又稱之為畫素，英文名稱為Pixel，其名稱是由pix(picture) + el(element)所組成，表示＂圖片元素＂，因此我們可以說，電腦上面的任何一個影像，都是由pixel所組成的。

[![2013-04-11_173629](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_173629.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_173629.gif)

*    [size(寬, 高)](http://processing.org/reference/size_.html) // 視窗大小

通常是第一個出現的指令，在一般的格式中會放在void setup裡面，在Processing的預設是100*100pixels，另用這行指令視窗大小，之後所有的圖案都會在裡面顯示，當然，如果你將圖片畫在視窗之外，他就不會顯示了。

[![2013-04-11_174606](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_174606.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_174606.gif)

*    [point(x,y) //點](http://www.processing.org/reference/point_.html)

先前說視窗都是由小方格所組成，也能夠假想成由點所組成。接著我們利用下面的程式碼進行顯示，由出現的結果可以知道原點在左上角，x指的是橫座標，越右邊數值越大，y是縱座標，越下面數值越大。

//Point `point(2, 1);
point(2, 51);
point(2, 52);
point(2, 53);
point(2, 54);
point(2, 55);
point(2, 56);
point(2, 57);
point(2, 58);
point(2, 59);` 

除此之外，我們也發現了一條線，而他也是由點組成，為了更方便畫線條，我們必須使用下列的指令。

[![2013-04-11_175949](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_175949.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_175949.gif)

*   [line(x1,y1,x2,y2) //線](http://www.processing.org/reference/line_.html)

//Line `line(10, 30, 90, 80);`

你所需要的只是給定一個起點(x1,y1)和終點(x2,y2)，接著他將會把之間所需要點補齊，這就是線條的使用方式。

由點組成線，由線組成面，因此接下來介紹形狀的使用方式。

[![2013-04-11_180227](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_180227.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_180227.gif)

*   [ triangle(x1,y1,x2,y2,x3,y3)//三角形由三點組成](http://processing.org/reference/triangle_.html)

三角形由三點所組成，因此你給予三點的數值就能夠自動產生一個三角形。

//三角形 `//三角形指令
triangle(60, 10, 25, 60, 75, 65);
//三條線條連線
line(60, 30, 25, 80);
line(25, 80, 75, 85);
line(75, 85, 60, 30);` 

[![2013-04-11_180934](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_180934.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_180934.gif)

*   [rect(x1,y1,width,height) //方形](http://www.processing.org/reference/rect_.html)

他是以方形左上角為起始點(x1,y1)，往右下角拉出一個方形，他有調整圓角的功能。

[![2013-04-11_193936](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_193936.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_193936.gif)

*   rect(x1, y1, width, height, 圓角半徑)
*   rect(x1, y1, width, height, 上左圓角, 上右圓角, 下右圓角, 下左圓角)

    
    rect(10, 10, 80, 80);    // 沒有圓角
    rect(20, 20, 60, 60,20); // 半徑20的圓角

*   [qu](http://processing.org/reference/quad_.html)[ad(x1,y1,x2,y2,x3,y3,x4,y4) //任意四邊形](http://processing.org/reference/quad_.html)

quad()則是Quadrilateral的縮寫，表示四邊形，不同於方形，需要指定四個點來進行四邊形的繪圖。

![2013-04-11_194958](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_194958.gif)

*   [ellipse(x1,y1,width,height)//橢圓形(x1,y1)表示圓心](http://processing.org/reference/ellipse_.html)

橢圓形也可以拿來製作圓形，只要在他的寬和高的數值設定一樣即可，而橢圓形所表示的x1和y1則是圓心位置。

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

接下來是比較進階的部分。  
[![2013-04-11_211318](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_211318.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_211318.gif)

    
    rect(10, 10, 50, 50);
    fill(204); // 淡灰
    rect(20, 20, 50, 50);
    fill(153); // 中灰
     rect(30, 30, 50, 50);
    fill(102); // 深灰
    rect(40, 40, 50, 50);

*   [fill(gary) //塗色](http://processing.org/reference/fill_.html)

簡單來說，只要調整fill(gray)裡面的gray參數即可調整圖案內面積的顏色，如同背景一樣，數值越大越接近白色，最大值255，gray的預設值是白色。

[![2013-04-11_212541](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_212541.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_212541.gif)

*   [fill(gray,alpha) //塗色(透明效果)](http://processing.org/reference/fill_.html)

    
    background(0);
    fill(255, 220);//不透明度220
     rect(15, 15, 50, 50);//不透明度220
     rect(35, 35, 50, 50);//不透明度220 

fill()指令新出現alpha數值，他所表示的意義是不透明度(opacity)，數值從0~255，數值越大越不透明，在這邊的程式碼除了讓大家知道不透明度之外，順帶一提，當你使用像是fill()這種調整圖形細節的指令時，是更改整個環境的設定，因此之後的每一個rect()所顯示出來的都會受到影響，像是以上的程式碼的第三和第四行的rect()都會以不透明度220來顯示。

[![2013-04-11_213156](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_213156.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_213156.gif)

有fill()塗色指令就會有noFill()不塗色指令，當出現noFill()指令，就會不將中間的部分塗色。

*   [ noFill() //不塗色指令](http://processing.org/reference/noFill_.html)

[![2013-04-11_212128](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_212128.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_212128.gif)

    
    background(0);
    rect(10, 10, 50, 50);
    stroke(102); // 深灰
    rect(20, 20, 50, 50);
    stroke(153); // 中灰
     rect(30, 30, 50, 50);
    stroke(204); // 淡灰 
    rect(40, 40, 50, 50);
    

*   [stroke(gray)](http://processing.org/reference/stroke_.html)

這部分要注意的是方框的線條，和fill一樣，調整stroke(gray)裡面的gray參數即可調整圖案內面積的顏色，如同背景一樣，數值越大越接近白色，最大值255，gray的預設值是白色。

*   [noStroke()//邊框不塗色。](http://processing.org/reference/noStroke_.html)

[![2013-04-11_214803](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_214803.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_214803.gif)

    
    smooth();
    strokeWeight(12);
    strokeCap(ROUND);
    line(20, 30, 80, 30); // 第一條線
    strokeCap(SQUARE);
    line(20, 50, 80, 50); // 第二條線
     strokeCap(PROJECT);
    line(20, 70, 80, 70); // 第三條線 
    
    

*   [strokeWeight(數值)//調整線條粗細](http://processing.org/reference/strokeWeight_.html)  
    

可以調整線條粗細，這在前一篇有提過。

*   [strokeCap(參數);//調整兩頭形狀](http://processing.org/reference/strokeCap_.html)

參數有三種選擇ROUND(圓頭)、SQUARE(方頭)、PROJECT(投影補滿)

[![2013-04-11_214853](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_214853.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_214853.gif)

    
    smooth();
    strokeWeight(12);
    strokeJoin(BEVEL);
    rect(12, 33, 15, 33); // 左邊
    strokeJoin(MITER);
    rect(42, 33, 15, 33); // 中間
     strokeJoin(ROUND);
    rect(72, 33, 15, 33); // 右邊 
    
    

*   [ strokeJoin() //調整圖案角落形狀](http://processing.org/reference/strokeJoin_.html)

參數有三種選擇BEVEL(斜角)、MITER(直角)、ROUND(圓頭)

[![2013-04-11_214117](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_214117.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_214117.gif)

平滑效果，平滑效果的目的是為了讓圖案看起來不要那麼銳利，之前有說過其實每張圖片都是由許多的小點所組成，因此邊緣的部分看起來沒有想像中的圓滑，因此利用smooth()能夠將邊緣修飾。

    
    smooth();
    ellipse(30, 48, 36, 36);
    noSmooth();
    ellipse(70, 48, 36, 36);
    

*   [smooth() //啟動平滑(預設開啟)](http://processing.org/reference/smooth_.html)
*   [noSmooth() //關閉平滑](http://processing.org/reference/noSmooth_.html)

先前所說的橢圓形和方形，他們另外還有繪圖模式可以調整。

[![2013-04-11_220134](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_220134.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-11_220134.gif)

    
    smooth();
    noStroke();
    fill(126);
    ellipseMode(RADIUS); 
    ellipse(33, 33, 60, 60); // 灰
    fill(255);
    ellipseMode(CORNER);
    ellipse(33, 33, 60, 60); // 白
    fill(0);
    ellipseMode(CORNERS);
    ellipse(33, 33, 60, 60); // 黑
    

*   [ellipseMode()](http://processing.org/reference/ellipseMode_.html)

參數有四種選擇，使用之後個別有不同的繪圖方式。

*   CENTER(中心)(預設值)

ellipse(x,y,width,height)，第一和第二參數表示圓心位置，第三和第四表示圖案的寬和高。

*   RADIUS(半徑)

ellipse(x,y,width,height)，第一和第二參數表示圓心位置，第三和第四表示圖案寬和高的一半。

*   CORNER(角落)

ellipse(x,y,width,height)，第一和第二參數表示左上角的位置，第三和第四表示圖案的寬和高。

*   CORNERS(雙點)

ellipse(x1,y1,x2,y2)，利用兩個座標定義出圓形的大小和位置。

[![2013-04-12_151038](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-12_151038.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-12_151038.gif)

    noStroke();
    rectMode(RADIUS);
    fill(126);
    rect(33, 33, 60, 60); // 灰
    rectMode(CORNER);
    fill(255);
    rect(33, 33, 60, 60); // 白
    rectMode(CORNERS);
    fill(0);
    rect(33, 33, 60, 60); // 黑
    
    

*   [rectMode()](http://processing.org/reference/rectMode_.html)

參數有四種選擇，使用之後個別有不同的繪圖方式。

*   CENTER(中心)(預設值)

rect(x,y,width,height)，第一和第二參數表示圓心位置，第三和第四表示圖案的寬和高。

*   RADIUS(半徑)

rect(x,y,width,height)，第一和第二參數表示圓心位置，第三和第四表示圖案寬和高的一半。

*   CORNER(角落)

rect(x,y,width,height)，第一和第二參數表示左上角的位置，第三和第四表示圖案的寬和高。

*   CORNERS(雙點)

rect(x1,y1,x2,y2)，利用兩個座標定義出圓形的大小和位置。

Posted on [April 11, 2013](http://192.168.1.233/2013/04/11/processing%e4%b8%ad%e6%96%87%e5%8c%966-%e5%9f%ba%e6%9c%ac%e7%b9%aa%e5%9c%96/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=568&action=edit)


# Processing中文化(7)-貝茲曲線
=====================

![](http://upload.wikimedia.org/wikipedia/commons/d/d0/Bezier_curve.svg)

貝茲曲線，又稱之貝賽爾曲線（Bézier曲線），是電腦圖形學中相當重要的參數曲線。

*   1959年，由Paul de Casteljau運用de Casteljau演算法所開發，
*   1962年，由法國工程師皮埃爾•貝茲（Pierre Bézier）所廣泛發表，應用在汽車設計。

Processing 所使用的bezier()方程式是一個三次貝茲曲線，由四個參數構成。在bezier()裡面依序給上P0~P3的座標資料，其中P0和P3稱之為錨點(anchor point)，P1和P2稱之為控制點(control point)，也就是固定P0和P3這兩個點，並且利用P1和P2去進行曲線形狀的控制，在使用方面你可以當作他是一種繪畫曲線的一種工具即可。

*   [bezier(x1, y1, x2, y2, x3, y3, x4, y4)](http://processing.org/reference/bezier_.html)

[![2013-04-15_142900](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-15_142900.gif)](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-15_142900.gif)

    bezier(32, 20, 80, 5, 80, 75, 30, 75);
    line(32, 20, 80, 5);
    ellipse(80, 5, 4, 4);//控制點
    line(80, 75, 30, 75);
    ellipse(80, 75, 4, 4);//控制點
    

![2013-04-15_142906](http://www.tabbymeow.com/wp-content/uploads/2013/04/2013-04-15_142906.gif)

    bezier(85, 20, 40, 10, 60, 90, 15, 80);
    line(85, 20, 40, 10);
    ellipse(40, 10, 4, 4);//控制點
    line(60, 90, 15, 80);
    ellipse(60, 90, 4, 4);//控制點
    

如上圖兩個程式碼所顯示的，呈現彎曲狀的部分就是貝茲曲線，關於理論的部分可以參考下圖。

![](http://upload.wikimedia.org/wikipedia/commons/f/ff/Bezier_3_big.gif)

資料來源：http://zh.wikipedia.org/wiki/File:Bezier\_3\_big.gif

這邊做簡單的介紹，首先我們會看見P0到P1之間出現一個綠點，而那個綠點會在T=0~1之間從P0＂等速度＂移動至P1點，另外兩個綠點也是如此，形成三個移動綠點之後，並依序連成兩條綠線，再依造剛剛的步驟形成藍點和藍線，最終在藍線上面的黑點也是等速度從藍線的起點＂等速度＂移動到最後的終點，在這樣的過程中，黑點所形成的軌跡就是＂貝茲曲線＂

參考資料：[貝茲曲線Wiki](http://zh.wikipedia.org/wiki/%E8%B2%9D%E8%8C%B2%E6%9B%B2%E7%B7%9A)

Posted on [April 15, 2013](http://192.168.1.233/2013/04/15/processing%e4%b8%ad%e6%96%87%e5%8c%967-%e8%b2%9d%e8%8c%b2%e6%9b%b2%e7%b7%9a/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=668&action=edit)

