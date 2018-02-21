---
title: diy-daq
tags: 
    - diy 
    - robot 
---

# Arduino DAQ
===========

![arduinoDAQ](http://www.tabbymeow.com/wp-content/uploads/2013/05/arduinoDAQ-1024x576.jpg)

在學習使用Processing+Arduino的連線之後，知道能利用Arduino將讀取到的訊號傳送到電腦上面顯示，或是利用電腦的訊號來控制Arduino，而之前的範例主要是用來製作小遊戲的控制器，平常在學校裡面會希望我們可以拿來製作圖表，為了達成這樣的目的只能使用昂貴的讀取器，像是NI的DAQ，雖然真正在做實驗的時候的確應該用精確的設備來進行，但是有些時候只不過是為了製作專題，沒有那麼多經費去購買一個NI的DAQ，頂多只有1000元的預算來製作一個小型的溫度控制器或是其他小專題，又希望可以讀取出簡易的圖表，因此如果利用Arduino來製作一個簡單的DAQ，那該有多好呢？  

![arduinoDAQ 2](http://www.tabbymeow.com/wp-content/uploads/2013/05/2013-05-29_142045.gif)

首先先依造電路圖配置好兩顆可變電阻，進行調整可變電阻，來改變電壓值，電壓值會在0~5V之間。接著利用Arduino的類比輸入來讀取這兩個電壓值，接著再利用RS232傳輸資料到Processing，接著Processing會將圖表顯示出來。

簡單的圖表顯示：

![arduinoDAQ 3](http://www.tabbymeow.com/wp-content/uploads/2013/05/2013-05-28_211644.gif)

Arduino：

    /**
     * 
     * Arduino DAQ for Arduino
     * by Cha-Wei Chang (NTU-BIME Lab405)
     * 
     * Arduino部分利用RS232傳輸類比資料到電腦，再利用Processing進行讀取
     * 傳輸的資料格式為"000 000 000 000 000 000n"
     *  000部分為各個類比腳位所讀取到的數字。
     *
     */
    
    void setup() {
      Serial.begin(115200);    //RS232通訊初始化，給定baudrate為115200。
    }
    void loop() {
    //先讀取類比訊號
      int analog0 = analogRead(A0);
      int analog1 = analogRead(A1);
      int analog2 = analogRead(A2);
      int analog3 = analogRead(A3);
      int analog4 = analogRead(A4);
      int analog5 = analogRead(A5);
    
    //類比訊號一筆一筆傳送出去
      Serial.print(analog0/4);
      Serial.print(" ");
      Serial.print(analog1/4);
      Serial.print(" ");
      Serial.print(analog2/4);
      Serial.print(" ");
      Serial.print(analog3/4);
      Serial.print(" ");
      Serial.print(analog4/4);
      Serial.print(" ");
      Serial.println(analog5/4);
    }
    

Processing：

    /**
     * 
     * Arduino DAQ for Processing
     * by Cha-Wei Chang (NTU-BIME Lab405)
     */
    import processing.serial.*;     //引入Serial library
    Serial myPort;                  //定義一個名為myPort的Serial
    DAQtable h1, h2;                //定義兩個DAQtable物件
    int lf = 10;        //換行符號
    String data, myString = null;
    String[] list;
    
    void setup() {
        myPort = new Serial(this, Serial.list()[1], 115200); //選擇第二個，設定baudrate為115200
        size(850, 200);              //視窗大小為200*200    
        h1 = new DAQtable(5, 50, 400, 100);        //和rect()一樣，前面兩個參數為座標，後面兩個是大小。
        h2 = new DAQtable(420, 50, 400, 100);
        //開始進行訊號的發送
        myPort.clear();
        myString = myPort.readStringUntil(lf);        //直到讀取到換行符號為止
        myString = null;
    }
    
    void draw() {
        background(0);
        while (myPort.available () > 0) {
            myString = myPort.readStringUntil(lf);
            if (myString != null) {
                list = split(myString, ' ');        //利用空白作為分割
                if (list.length == 3){
                    h1.update(int((list[0])));    //給入整數值
                    h2.update(int((list[1])));
                    println(myString);
                }
            }
        }
        h1.show();        //顯示圖表
        h2.show();
    }
    
    

DAQtable：

    /**
     * 
     * DAQtable Class
     * by Cha-Wei Chang (NTU-BIME Lab405)
     * 
     */
    class DAQtable {
        int swidth, sheight, xpos, ypos;
        int[] numbers;
        int dataCnt = 0;
        DAQtable(int xp, int yp, int sw, int sh) {
            xpos = xp;
            ypos = yp;
            swidth = sw;
            sheight = sh;
            numbers = new int[sw];
            for (int i = 0; i < sw; i++)
            numbers[i] = int(map(50, 0, 255, 5+ypos, sheight-5+ypos));
        }
        //數據更新
        void update(int data) {
            data =  int(map(255-data, 0, 255, 5+ypos, sheight-5+ypos));   
            numbers[dataCnt] = data;
            dataCnt++;
            if (dataCnt == swidth) {
            dataCnt--;
            for (int i = 0; i < swidth-1; i++)
            numbers[i] = numbers[i+1];
            }
        }
        //顯示圖表
        void show() {
            noFill();
            rect(xpos, ypos, swidth, sheight);
            for (int x = xpos; x < xpos+swidth; x++) {
                stroke(255);
                point(x, numbers[x-xpos]);
            }
        }
    }
    
    

心得與使用方式：

由Arduino負責傳送訊息，但在Processing接收一直失敗，資料總是破碎的回傳過來，這樣我根本無法對一筆資料進行處理，後來利用”收到換行符號”才一次發出訊號的這個方法做，以目前的效果來說尚且還算不錯，但是一旦我希望可以處理更多資料的時候就變得很緩慢，這是目前的主要問題，之後會再改善，由於這是我第一次寫Class，可能有些部分還有點不全，大家就勉強使用吧，將來還會繼續將電壓值、XY軸資料和標題補齊。

首先將Arduino的程式碼寫入自己的Arduino，之後不要拔掉USB，接著把Processing的程式碼打開，並且引入DAQtable這個Class就可以使用了。

這邊是唯一我覺得會有問題的地方，因為你所使用的Arduino port可能和我的不同，因此在這邊你得調找Serial.list\[1\]裡面的數字，選擇你所使用的port。

    myPort = new Serial(this, Serial.list()[1], 115200);

值得參考的網站：[Cooper Maa：透過序列通訊把 Processing 與 Arduino 連接起來](http://coopermaa2nd.blogspot.tw/2011/03/processing-arduino.html)

Posted on [May 29, 2013](http://192.168.1.233/2013/05/29/arduino-daq/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=1008&action=edit)

# Arduino DAQ-2
=============

![2013-06-12_144242](http://www.tabbymeow.com/wp-content/uploads/2013/06/2013-06-12_144242.gif)上回(請參考[Tabbymeow : Arduino DAQ](http://www.tabbymeow.com/arduino-daq/))已經能夠利用我編寫的 DAQtable來顯示電壓值，漸漸我也想要開始多寫一點其他的功能，像是可以顯示XLabel和標題，希望之後也可以完成YLabel的部分，只是目前還不清楚應該怎麼做，以下提供新的程式碼給大家參考。

這次更新的部份新增了XLabel和電壓標籤，而title雖然可以顯示，但是還沒有完成可以從外面輸入所想要的字樣，希望漸漸可以完成更多的功能，讓之後想要當簡單示波器的人可以更方便去使用他。

更新的部分只有Class，其他部份不需要更新。

DAQtable Class

    /**
     * 
     * DAQtable Class
     * by Cha-Wei Chang (NTU-BIME Lab405)
     * 
     */
    class DAQtable {
      int swidth, sheight, xpos, ypos;
      int[] numbers;
      int dataCnt = 0;  
      boolean axisLabelEnable = true, titleEnable = true; 
    
      DAQtable(int xp, int yp, int sw, int sh) {
        xpos = xp;
        ypos = yp;
        swidth = sw;
        sheight = sh;
        numbers = new int[sw];
        for (int i = 0; i < sw; i++)
          numbers[i] = int(map(256, 0, 511, 5+ypos, sheight-5+ypos));
      }
      //數據更新
      void update(int data) {
        data =  int(map(256-data, 0, 511, 5+ypos, sheight-5+ypos));   
        numbers[dataCnt] = data;
        dataCnt++;
        if (dataCnt == swidth) {
          dataCnt--;
          for (int i = 0; i < swidth-1; i++)
            numbers[i] = numbers[i+1];
        }
      }
      //顯示圖表
      void show() {
        noFill();
        rect(xpos, ypos, swidth, sheight);
        for (int x = xpos; x < xpos+swidth; x++) {
          stroke(255);
          point(x, numbers[x-xpos]);
          if (x>xpos) {
            line(x, numbers[x-xpos], x-1, numbers[x-xpos-1]);
          }
        }
        if (axisLabelEnable)
          xlabel();
        if (titleEnable)
          text("title", xpos+swidth/2, ypos-5);
      }
    
      void showXlabel() {
        axisLabelEnable = true;
      }
      private void noXlabel() {
        axisLabelEnable = false;
      }
    
       void xlabel() {
        line(xpos, ypos+sheight/2, xpos-20, ypos+sheight/2);//zero
        line(xpos+swidth, ypos+sheight/2, xpos+swidth+20, ypos+sheight/2);//zeor
        line(xpos, ypos+sheight-5, xpos-20, ypos+sheight-5);//minus five
        line(xpos+swidth, ypos+sheight-5, xpos+swidth+20, ypos+sheight-5);//minus five
        line(xpos, ypos+5, xpos-20, ypos+5);// five
        line(xpos+swidth, ypos+5, xpos+swidth+20, ypos+5);// five
        line(xpos, ypos+sheight/4*3-5, xpos-10, ypos+sheight/4*3-5);//minus 2.5
        line(xpos+swidth, ypos+sheight/4*3-5, xpos+swidth+10, ypos+sheight/4*3-5);//minus 2.5
        line(xpos, ypos+sheight/4+5, xpos-10, ypos+sheight/4+5);// 2.5
        line(xpos+swidth, ypos+sheight/4+5, xpos+swidth+10, ypos+sheight/4+5);// 2.5
        text("5", xpos-15, ypos + 5);
        text("5", xpos+swidth+10, ypos + 5);
        text("0", xpos-15, ypos+sheight/2);
        text("0", xpos+swidth+10, ypos+sheight/2);
        text("-5", xpos-15, ypos+sheight-5);
        text("-5", xpos+swidth+10, ypos+sheight-5);
      }
    }
    
    

除此之外，我還真的拿這個arduino_DAQ去量測電容的充放電，並且附上和NI的DAQ比較圖片。

![2013-06-09_201358](http://www.tabbymeow.com/wp-content/uploads/2013/06/2013-06-09_201358.gif)

這是我的Arduino_DAQ

![2013-06-09_201352](http://www.tabbymeow.com/wp-content/uploads/2013/06/2013-06-09_201352.gif)

這是NI的DAQ並且使用labview所製作出的效果

我覺得目前的結果應該很適合初學的玩家去使用，之後我也會拿這個arduino_DAQ去製作各種專題吧。

Posted on [June 12, 2013](http://192.168.1.233/2013/06/12/arduino-daq-2/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=1023&action=edit)

