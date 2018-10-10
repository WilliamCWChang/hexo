---
title: Python Challenge
tags: coding
---

* [挑戰網站](http://www.pythonchallenge.com/)
* 其他人的解答
    * http://garethrees.org/2007/05/07/python-challenge/
    * https://www.gitbook.com/book/hackingnote/the-python-challenge-solutions/details


---

# Level 0
http://www.pythonchallenge.com/pc/def/0.html

```python=
print(2**38)
```
then return 274877906944.

change the url to

http://www.pythonchallenge.com/pc/def/274877906944.html

---

# Level 1
http://www.pythonchallenge.com/pc/def/map.html

I see the pink string below the picture.

可能是什麼神奇編碼？
觀察一下
K->M, O->Q, E->G
KLM OPQ EFG
原來是跳兩格轉換
ABC A->C 

寫code來處理這段

```python=
import string
input = string.ascii_lowercase[:]
output = string.ascii_lowercase[2:] + 'ab'
change_table = str.maketrans(input, output)
data = "g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj."
print(data.translate(change_table))
```
得到下列的話
```shell=
i hope you didnt translate it by hand. thats what computers are for. doing it in by hand is inefficient and that's why this text is so long. using string.maketrans() is recommended. now apply on the url.
```
表示我們的URL比照辦理
也就是MAP這三個字也比照處理，會得到ocr。將本來的map換成ocr這就是下一關的網址



---

# Level 2
http://www.pythonchallenge.com/pc/def/ocr.html

這關的關鍵在html的page source

page source內裡面有一堆亂碼，把亂碼全部清除，就會看到關鍵字

```python=
import requests
import string
r = requests.get('http://www.pythonchallenge.com/pc/def/ocr.html')
data = r.text

check = '!@#$%^&*()_+[]{}->< \n'
for char in data:
    if char not in check:
        print(char,end='')
```

return 
```shell=
htmlheadtitleocr/titlelinkrel="stylesheet"type="text/css"href="../style.css"/headbodycenterimgsrc="ocr.jpg"brfontcolor="c03000"recognizethecharacters.maybetheyareinthebook,brbutMAYBEtheyareinthepagesource./centerbrbrbrfontsize="1"color="gold"Generaltips:liUsethehints.Theyarehelpful,mostofthetimes./liliInvestigatethedatagiventoyou./liliAvoidlookingforspoilers./librForums:ahref="http://www.pythonchallenge.com/forums"/PythonChallengeForums/a,readbeforeyoupost.brIRC:irc.freenode.netpythonchallengebrbrToseethesolutionstothepreviouslevel,replacepcwithpcc,i.e.goto:http://www.pythonchallenge.com/pcc/def/ocr.html/body/htmlfindrarecharactersinthemessbelow:

equality
```
得到下一關的關鍵字equality


---

# Level 3
http://www.pythonchallenge.com/pc/def/equality.html

```python=
import requests
import re
r = requests.get('http://www.pythonchallenge.com/pc/def/equality.html')
data = r.text
output = "".join(re.findall("[^A-Z]+[A-Z]{3}([a-z])[A-Z]{3}[^A-Z]+", data))
print(output)
```

得到關鍵字linkedlist

---

# Level 4
http://www.pythonchallenge.com/pc/def/linkedlist.html
發現他想要用PHP
http://www.pythonchallenge.com/pc/def/linkedlist.php
可以，很可以。

點進去圖片之後，發現有數字可以來更換網址。

換了幾次之後發現她可能超多，需要用python來做這部分。

```python=
import requests
import re
number = '12345'
while True:
    r = requests.get("http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=" + number)
    data = r.text
    if "and the next nothing is " not in data:
        print(data)
    number = re.sub("[^0-9]", "", data)
```

```shell=
Yes. Divide by two and keep going.
peak.html
```

---

# Level 5
http://www.pythonchallenge.com/pc/def/peak.html

```python=
import pickle
from urllib.request import urlopen
data = pickle.load(urlopen("http://www.pythonchallenge.com/pc/def/banner.p"))
for line in data:
    for char_tuple in line:
        print(char_tuple[0]*char_tuple[1], end='')
    print('\n')
```

retrun channel


---

# Level 6
http://www.pythonchallenge.com/pc/def/channel.html

一開始看到拉練zip

http://www.pythonchallenge.com/pc/def/zip.html

錯了

改成

http://www.pythonchallenge.com/pc/def/channel.zip

下載了一包奇怪的東西，先來解壓縮

看到一堆文字檔案，先看看有無規律，發現一個readme.txt

```shell=
welcome to my zipped list.

hint1: start from 90052
hint2: answer is inside the zip
```

很好，應該事先讀取檔案，然後從90052開始讀取到答案吧。
拿之前的Level4來修改

```python=
import re

path = '.\\channel\\'
number = '90052'
while True:
    f = open(path + number + '.txt', 'r')
    data = f.read()
    f.close()
    number = re.sub("[^0-9]", "", data)
    print(number)
    if number == "":
        break
print(data)
```
在46145噴出錯誤，表示找不到下一個number，並回傳這行給我。

```shell=
Collect the comments.。
```

ZIP 貌似可以看到一些 comment?


```python=
from zipfile import ZipFile
import re

f = ZipFile("./channel.zip")
number = '90052'
data = f.read(number + ".txt")


while True:
    data = f.read(number + ".txt")
    comment = f.getinfo(number + ".txt").comment
    number = re.sub("[^0-9]", "", data)
    print(comment, end='')
```

return this

```shell=
****************************************************************
****************************************************************
**                                                            **
**   OO    OO    XX      YYYY    GG    GG  EEEEEE NN      NN  **
**   OO    OO  XXXXXX   YYYYYY   GG   GG   EEEEEE  NN    NN   **
**   OO    OO XXX  XXX YYY   YY  GG GG     EE       NN  NN    **
**   OOOOOOOO XX    XX YY        GGG       EEEEE     NNNN     **
**   OOOOOOOO XX    XX YY        GGG       EEEEE      NN      **
**   OO    OO XXX  XXX YYY   YY  GG GG     EE         NN      **
**   OO    OO  XXXXXX   YYYYYY   GG   GG   EEEEEE     NN      **
**   OO    OO    XX      YYYY    GG    GG  EEEEEE     NN      **
**                                                            **
****************************************************************
 **************************************************************
```
先用hockey，發現不對。
http://www.pythonchallenge.com/pc/def/hockey.html
it's in the air. look at the letters.

被開了一個小玩笑。仔細看看，發現裡面還有字
oxygen


---

# Level 7
http://www.pythonchallenge.com/pc/def/oxygen.html

```python=
from PIL import Image
img = Image.open("oxygen.png")
row = [img.getpixel((col, img.height / 2))[0] for col in range(img.width)]
data = [str(unichr(char)) for char in row[::7]]
print("".join(data))

level_keyword = [105, 110, 116, 101, 103, 114, 105, 116, 121]
level_keyword = [str(unichr(char)) for char in level_keyword]
print("".join(level_keyword))
```
```shell=
smart guy, you made it. the next level is [105, 110, 116, 101, 103, 114, 105, 116, 121]pe_
integrity
```

get keywords: integrity



---

# Level 8
http://www.pythonchallenge.com/pc/def/integrity.html

```python=
import bz2

un = 'BZh91AY&SYA\xaf\x82\r\x00\x00\x01\x01\x80\x02\xc0\x02\x00 \x00!\x9ah3M\x07<]\xc9\x14\xe1BA\x06\xbe\x084'
pw = 'BZh91AY&SY\x94$|\x0e\x00\x00\x00\x81\x00\x03$ \x00!\x9ah3M\x13<]\xc9\x14\xe1BBP\x91\xf08'

print(bz2.decompress(un))
print(bz2.decompress(pw))
```
return
Username: huge
Password: file

---

# Level 9
http://www.pythonchallenge.com/pc/return/good.html

嘗試用看看來畫
[PIL.ImageDraw.Draw.polygon(xy, fill=None, outline=None)](http://pillow.readthedocs.io/en/3.1.x/reference/ImageDraw.html#PIL.ImageDraw.PIL.ImageDraw.Draw.polygon)


```python=
first = [146,399,163,403,170,393,169,391,166,386,170,381,170,371,170,355,169,346,167,335,170,329,170,320,170,
310,171,301,173,290,178,289,182,287,188,286,190,286,192,291,194,296,195,305,194,307,191,312,190,316,
190,321,192,331,193,338,196,341,197,346,199,352,198,360,197,366,197,373,196,380,197,383,196,387,192,
389,191,392,190,396,189,400,194,401,201,402,208,403,213,402,216,401,219,397,219,393,216,390,215,385,
215,379,213,373,213,365,212,360,210,353,210,347,212,338,213,329,214,319,215,311,215,306,216,296,218,
290,221,283,225,282,233,284,238,287,243,290,250,291,255,294,261,293,265,291,271,291,273,289,278,287,
279,285,281,280,284,278,284,276,287,277,289,283,291,286,294,291,296,295,299,300,301,304,304,320,305,
327,306,332,307,341,306,349,303,354,301,364,301,371,297,375,292,384,291,386,302,393,324,391,333,387,
328,375,329,367,329,353,330,341,331,328,336,319,338,310,341,304,341,285,341,278,343,269,344,262,346,
259,346,251,349,259,349,264,349,273,349,280,349,288,349,295,349,298,354,293,356,286,354,279,352,268,
352,257,351,249,350,234,351,211,352,197,354,185,353,171,351,154,348,147,342,137,339,132,330,122,327,
120,314,116,304,117,293,118,284,118,281,122,275,128,265,129,257,131,244,133,239,134,228,136,221,137,
214,138,209,135,201,132,192,130,184,131,175,129,170,131,159,134,157,134,160,130,170,125,176,114,176,
102,173,103,172,108,171,111,163,115,156,116,149,117,142,116,136,115,129,115,124,115,120,115,115,117,
113,120,109,122,102,122,100,121,95,121,89,115,87,110,82,109,84,118,89,123,93,129,100,130,108,132,110,
133,110,136,107,138,105,140,95,138,86,141,79,149,77,155,81,162,90,165,97,167,99,171,109,171,107,161,
111,156,113,170,115,185,118,208,117,223,121,239,128,251,133,259,136,266,139,276,143,290,148,310,151,
332,155,348,156,353,153,366,149,379,147,394,146,399]

second = [156,141,165,135,169,131,176,130,187,134,191,140,191,146,186,150,179,155,175,157,168,157,163,157,159,
157,158,164,159,175,159,181,157,191,154,197,153,205,153,210,152,212,147,215,146,218,143,220,132,220,
125,217,119,209,116,196,115,185,114,172,114,167,112,161,109,165,107,170,99,171,97,167,89,164,81,162,
77,155,81,148,87,140,96,138,105,141,110,136,111,126,113,129,118,117,128,114,137,115,146,114,155,115,
158,121,157,128,156,134,157,136,156,136]

from PIL import Image,ImageDraw
im = Image.new('RGB', (500,500))
draw = ImageDraw.Draw(im)
draw.polygon(first, fill='white')
draw.polygon(second, fill='white')
im.show()
```

原來是一頭牛，未看先猜bull

沒錯，答對了


---

# Level 10
http://www.pythonchallenge.com/pc/return/bull.html

觀察網頁
```shell=
a = [1, 11, 21, 1211, 111221, 
```

上網查詢看看。原來叫做[外觀數列](https://zh.wikipedia.org/wiki/%E5%A4%96%E8%A7%80%E6%95%B8%E5%88%97)

建議參考[groupby](https://docs.python.org/2/library/itertools.html#itertools.groupby)，這個好用，未來如果想要做一些機率或是排列組合，根本大推。


```python=
from itertools import groupby
def look_and_say(num):
    output = []
    a = [list(g) for k, g in groupby(num)]
    for char in a:
        num_data = str(len(char)) + char[0]
        output.append(num_data)
    return "".join(output)

number = '1'
for i in range(1, 31):
    number = look_and_say(number)
    print('[' + str(i) + ']' + str(len(number)))
```
因為他要找a[30]，len(a[30]) = ?
ans=5808

---

# Level 11
http://www.pythonchallenge.com/pc/return/5808.html

看看title，不錯不錯odd even???

```python=
import cv2
import numpy as np
img = cv2.imread('cave.jpg', 0)
width = img.shape[0]
height = img.shape[1]
even = np.zeros((width, height), np.uint8)
odd = np.zeros((width, height), np.uint8)
for row in range(height):
    for col in range(width):
        if (row + col) % 2 == 1:
            odd[col, row] = img[col, row]
        else:
            even[col, row] = img[col, row]
even = cv2.equalizeHist(even)
res = np.hstack((img, even, odd))  # stacking images side-by-side
cv2.imshow('', res)
cv2.imwrite('res.png', res)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
這關有許多想法無法言語阿，其實我覺得重點在於會不會影像處理，如果一開始就對影像做equalizeHist，又稱之為直方圖等化。其實答案就出來了，不過因為希望做even和odd，我還是分成兩個步驟來做了。先弄出even和odd，然後對even在做一次equalizeHist，答案就是evil!!

![](https://i.imgur.com/4hQDdZY.png)


---

# Level 12
http://www.pythonchallenge.com/pc/return/evil.html


檢查中間的圖片
http://www.pythonchallenge.com/pc/return/evil1.jpg

有1就有2，不可能沒有3，直到5之後就真的無法，也沒繼續嘗試了。
http://www.pythonchallenge.com/pc/return/evil2.jpg
http://www.pythonchallenge.com/pc/return/evil3.jpg
http://www.pythonchallenge.com/pc/return/evil4.jpg

發現evil4.jpg在下載下來之後是檔案損毀，所以修改檔案名稱為，evil4.txt，然後再來看內容。


```shell=
Bert is evil! go back!
```

看到這邊我還拿Bert和back去當關鍵字，看來不是

然後我還把evil2和3拿去imageJ檢查有沒有問題。

注意到有一張照片寫著不是jpg，而是gfx，沒看過。

輸入URL之後開始下載一個檔案。
http://www.pythonchallenge.com/pc/return/evil2.gfx

我打算用python來讀取這個檔案，但馬上遇到麻煩

---

偷看別人的解答，原來牌發五堆，表示我的資料要分成五份。

```python=
filepath = '.\evil2.gfx'
with open(filepath, 'rb') as f:
    contents = f.read()

for i in range(5):
    open('%d.jpg' % i ,'wb').write(contents[i::5])

```

得到五張圖片。後面的ity不需要就得到了disproportional

---
# Level 13
http://www.pythonchallenge.com/pc/return/disproportional.html

中間的5可以按下去，然後前往該頁面http://www.pythonchallenge.com/pc/phonebook.php

可能要我們嘗試讀取XML?

evil 前面還有一個remote的tag，真是令人疑惑

交互查詢之後得到XML-RPC這個關鍵字。

剛好最近在接觸robot framework，所以剛好知道這個東西。
https://github.com/robotframework/RemoteInterface


努力在python裡面看看要怎麼用。
https://docs.python.org/3/library/xmlrpc.client.html#xmlrpc.client.ServerProxy.system.listMethods
* 主要有這三個方法可以用
    * ServerProxy.system.listMethods()
    * ServerProxy.system.methodSignature(name)
    * ServerProxy.system.methodHelp(name)

先用listMethod()得到我有什麼method之後再來看看另外兩個

```python=
import xmlrpc.client

proxy = xmlrpc.client.ServerProxy("http://www.pythonchallenge.com/pc/phonebook.php")
print(proxy.system.listMethods())
print(proxy.system.methodHelp('phone')) # the explanation is clear
print(proxy.system.methodSignature('phone')) # give string and return string

# call evil but return error
print(proxy.phone('evil'))
```

但是得到

```shell=
He is not the evil
```

so who's the evil?????


前一回合好像有類似的記憶？

```shell=
Bert is evil! go back!
```

那我打給 Bert好了？

```shell=
>>> print(proxy.phone('Bert'))
555-ITALY
```

這個看來是關鍵字 555-ITALY，重複嘗試幾次後才知道答案。

後來查詢之後，555表示虛構電話號碼，所以都是假的@@
![](https://goo.gl/eJkjXN)
https://en.wikipedia.org/wiki/555_(telephone_number)




# Level 14
http://www.pythonchallenge.com/pc/return/italy.html

看到這東西我在想義大利有什麼螺旋的東西嗎？

查查看意大利麵包，結果什麼都沒有@@

還是只是暗示我螺旋而已？

還有那個wire.png看起來超詭異10000*1超長的圖片。

未看先猜他可能是一個字串或是我要自己組成圖片。

還有下面這個讓我很在意。

```htmlembedded=
<!-- remember: 100*100 = (100+99+99+98) + (...  -->
```

該不會是100 99 99 98表示四個邊@@...

這code怎麼寫...

我先隨便將圖片變成100*100後。

```python=
filepath = 'wire.png'
import cv2
import numpy as np
img = cv2.imread(filepath, 0)
real = np.zeros((100, 100), np.uint8)

for index in range(0,10000):
    y = int(index/100)
    x = index%100
    real[y][x] = img[0][index]

cv2.imshow('', real)
cv2.imwrite('res.png', real)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![](https://i.imgur.com/ODqba9c.png)

得到關鍵字囉，不過點進去後發現應該不對

http://www.pythonchallenge.com/pc/return/bit.html
```shell=
you took the wrong curve.
```


後來大概知道是螺旋狀，所以嘗試了幾種方式。
Method1
```python=
def layer_y(index):
    layer = 0
    num = [i for i in range(99,0,-2)]
    while index-sum(num[:layer+1])*4>=0:
        layer = layer + 1
    return layer

def layer_x(index, t):
    layer = 0
    num = [i for i in range(99,0,-2)]
    # print(index)
    while index-sum(num[:layer+1])*4>=0:
        layer = layer + 1
    # print(layer)

    check = (index-sum(num[:layer])*4)//(num[layer])
    # print(check)
    if check == t:
        return (index-sum(num[:layer])*4)%(num[layer]) + layer
    else:
        return None

        #      (loss data)/99 or 97 = 0~396 + shift 

filepath = 'wire.png'

import cv2
import numpy as np
img = cv2.imread(filepath, 0)
width = img.shape[0]
height = img.shape[1]
output_img1 = np.zeros((100, 100), np.uint8)
output_img2 = np.zeros((100, 100), np.uint8)
output_img3 = np.zeros((100, 100), np.uint8)
output_img4 = np.zeros((100, 100), np.uint8)

for index in range(0,10000):
    y = layer_y(index)
    x = layer_x(index, 0)
    if x != None:
        output_img1[y][x] = img[0][index]

    x = layer_x(index, 1)
    if x != None:
        output_img2[y][x] = img[0][index]

    x = layer_x(index, 2)
    if x != None:
        output_img3[y][x] = img[0][index]

    x = layer_x(index, 3)
    if x != None:
        output_img4[y][x] = img[0][index]

# print()


M2 = cv2.getRotationMatrix2D((50,50),270,1.0)
output_img2 = cv2.warpAffine(output_img2,M2,(100,100))

M3 = cv2.getRotationMatrix2D((50,50),180,1.0)
output_img3 = cv2.warpAffine(output_img3,M3,(100,100))

M4 = cv2.getRotationMatrix2D((50,50),90,1.0)
output_img4 = cv2.warpAffine(output_img4,M4,(100,100))

out = output_img1+output_img2+output_img3+output_img4


res = np.hstack((output_img1, output_img2, output_img3, output_img4))  # stacking images side-by-side
cv2.imshow('', out)
cv2.imwrite('res.png', out)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
代碼很長，但效果不優。


Method2
```python=
filepath = 'wire.png'
import cv2
import numpy as np

img = cv2.imread(filepath, 0)
fake = np.zeros((100, 100), np.uint8)
real = np.zeros((100, 100), np.uint8)
x = 0 
y = 0
dir = 0
dir_x = [+1,0,-1,0]
dir_y = [0,+1,0,-1]
# x+1 y
# x y+1
# x-1 y
# x y-1

for index in range(0,10000):
    if fake[y][x] == 0:
        fake[y][x] = 255
        real[y][x] = img[0][index]
    next_x = x + dir_x[dir]
    next_y = y + dir_y[dir]
    if next_x>99 or next_x<0 or next_y<0 or next_y>99 or fake[next_y][next_x] == 255:
        dir = (dir+1)%4
    x = x + dir_x[dir]
    y = y + dir_y[dir]
    # print(index,x,y,fake[y][x])

cv2.imshow('', real)
cv2.imwrite('res.png', real)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![](https://i.imgur.com/zGOftkl.png)

看來答案很清楚了。


http://www.pythonchallenge.com/pc/return/cat.html


---

# Level 15

http://www.pythonchallenge.com/pc/return/uzi.html

得到一份月曆，上面寫著1XX6年。

這是我兩個提示。
* he ain't the youngest, he is the second
* todo: buy flowers for tomorrow

觀察月曆後發現，二月有29號，所以目前有四個線索。

* 該年為1XX6年
* 該年二月有29號，當天為星期日
* 第二個年輕的年份
* 1/26的明天看來有什麼事情發生？


```python
import datetime

for year in range(1006, 1997, 10):
    try:
        weekday = datetime.datetime(year, 2, 29).weekday()
        if weekday == 6:
            print(year, weekday)
    except ValueError:
        pass
```

1756/1/27 是什麼日子？
沃夫岡·阿瑪迪斯·莫札特（德語：Wolfgang Amadeus Mozart，1756年1月27日－1791年12月5日），出生於奧地利薩爾斯堡，逝世於維也納，是歐洲最偉大的古典主義音樂作曲家之一，他也是一位共濟會成員。


---

# Level 16
http://www.pythonchallenge.com/pc/return/mozart.html

```shell=
<title>let me get this straight</title>
```

看來需要對齊什麼？先來把紫色的對齊。但發現opencv不能直接處理gif。所以我只好使用小畫家先轉換成PNG，再來處理

```python=
import cv2
import numpy as np

img = cv2.imread('mozart.png')
width = img.shape[1]
height = img.shape[0]
img_ans = np.zeros((int(height), int(width), 3), np.uint8)

for row in range(height):
    for col in range(width):
        if img[row][col][0] > 230 and img[row][col][1] < 10 and img[row][col][2] > 230 and img[row][col - 1][1] > 200:
            print(row, col)
            img_ans[row] = np.roll(img[row][:], -col * 3)
            break

cv2.imshow('', img_ans)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

得到答案romance
![](https://i.imgur.com/fxUZDS4.png)

---

# Level 17
http://www.pythonchallenge.com/pc/return/romance.html

看到這張圖的瞬間，我只覺得是不是要看Cookie(網站在您瀏覽網頁時儲存在您的電腦上的資料。)，是不是要切一半?????

沒想太多，先輸入餅乾??
http://www.pythonchallenge.com/pc/return/cookies.html

得到一句話 "yummy! chocolate chips."

http://www.pythonchallenge.com/pc/return/chocolate.html

do you want to eat or to play?

我要吃!!!!

http://www.pythonchallenge.com/pc/return/eat.html

404 Not Found

不給吃...

http://www.pythonchallenge.com/pc/return/play.html

then go back and play.

所以我要play cookies?

回頭看了好久，找找其他線索，圖片中左下角貌似是Level 4的圖片，進去之後來找找訊息

1. 先從cookies找，發現有東西，裡面帶有you+should+have+followed+busynothing...
2. Yes. Divide by two and keep going. <--曾經在Level出現過的字串

反正我先從Level 4 的程式來玩看看

因為level4玩的時候，都是數字，所以應該是將該數字除了2?

稍微修改Level 4 的code，來讀取這句話的網址。
Yes. Divide by two and keep going. <-- 16044

16044/2 = 8022

套用在原本Level4的code

http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=8022

修改初始值來執行，結果竟然丟垃圾給我...

程式輸入為8268363579

There maybe misleading numbers in the 
text. One example is 82683. Look only for the next nothing and the next nothing is 63579

修改初始值為63579來執行。

最後找到peak.html

我覺得我過程整個錯了，再看看nothing??busynothing!!

修改一下網址
?busynothing=8022

http://www.pythonchallenge.com/pc/def/linkedlist.php?busynothing=83051

出現了that's it.

我來檢查一下cookies!!

%90

這貌似是某種encode
https://www.eso.org/~ndelmott/url_encode.html

不管，我再丟進去跑!!

...感覺沒結果，可能結論是錯的。

回頭從

?busynothing=12345執行，得到下一個應該是44827

一樣最後得到83051

可能是對的嗎？

所以我去檢查到that's it.以前頁面的cookie，發現大有玄機。原來每一頁都有Cookie

BZh91AY%26SY%94%3A%E2I%00%00%21%19%80P%81%11%00%AFg%9E%A0+%00hE%3DM%B5%23%D0%D4%D1%E2%8D%06%A9%FA%26S%D4%D3%21%A1%EAi7h%9B%9A%2B%BF%60%22%C5WX%E1%ADL%80%E8V%3C%C6%A8%DBH%2632%18%A8x%01%08%21%8DS%0B%C8%AF%96KO%CA2%B0%F1%BD%1Du%A0%86%05%92s%B0%92%C4Bc%F1w%24S%85%09%09C%AE%24%90

最後字串還是出不來，沒顯示，上網查找之後才知道還要bz2，這關的作者會不會太搞剛?

```python=
import requests
import urllib
import re

word_list = []
check_str = "and the next busynothing is"
number = '12345'
print("Start", "Get number")

while True:
    r = requests.get(
        "http://www.pythonchallenge.com/pc/def/linkedlist.php?busynothing=" + number)
    data = r.text
    word_list.append(r.cookies['info'])
    if "and the next busynothing is " not in data:
        print(data)
        break
    number = re.sub("[^0-9]", "", data[data.find(check_str):])

print(word_list)

url_str = ''.join(word_list)
a = urllib.unquote_plus(url_str)

print(a.decode('bz2'))

```

最後給我這句話
is it the 26th already? call his father and inform him that "the flowers are on their way". he'll understand.

因為前面有mozart的1/27生日，看來是同一件事情，打給他爸爸?

查詢之後應該叫做 Leopold Mozart

http://www.pythonchallenge.com/pc/return/Leopold.html

依照前面打電話的方式level 13，只是打給
```python=
import xmlrpc.client

proxy = xmlrpc.client.ServerProxy("http://www.pythonchallenge.com/pc/phonebook.php")
print(proxy.system.listMethods())
print(proxy.system.methodHelp('phone')) # the explanation is clear
print(proxy.system.methodSignature('phone')) # give string and return string

# call evil but return error
print(proxy.phone('Leopold'))
```

得到這個555-VIOLIN

http://www.pythonchallenge.com/pc/return/violin.html

no! i mean yes! but ../stuff/violin.php.

http://www.pythonchallenge.com/pc/stuff/violin.php

...我白天用還差點嚇死人....

不要突然一張臉可以嗎？

看到title 

it's me. what do you want?

我想要下一關!!!

不對，打給他爸之後還要和她說花的事情。

```python=
import requests
url = 'http://www.pythonchallenge.com/pc/stuff/violin.php'
cookies = dict(info='the+flowers+are+on+their+way')
r = requests.get(url, cookies=cookies)
print(r.text)
```

把要info裡面帶我要的訊息加入cookie

```htmlmixed=
<html>
<head>
  <title>it's me. what do you want?</title>
  <link rel="stylesheet" type="text/css" href="../style.css">
</head>
<body>
    <br><br>
    <center><font color="gold">
    <img src="leopold.jpg" border="0"/>
<br><br>
oh well, don't you dare to forget the balloons.</font>
</body>
</html>
```

原來是balloons

---

# Level 18
http://www.pythonchallenge.com/pc/return/balloons.html

