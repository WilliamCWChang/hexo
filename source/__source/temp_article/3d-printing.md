---
title: 3d-printing
tags: machine
---

快速成型機
快速成型(Rapid prototyping, RP)：是一種快速產生模型或零件的技術。

利用電腦資料作為設計圖，以堆積材料來製作實體。
成型過程無須使用模具。
歷史： 始於1970年代，直到1980年代末才逐漸出現了成熟的製造裝置。 過程：

3D繪圖軟體製作CAD模型。電腦輔助設計軟體如Pro/E、SolidWorks、Unigraphics、AutoCAD，或是透過其他方式如雷射掃描、 電腦斷層掃描，得到點雲端資料
快速成型處理軟體，進行離散資料和分層處理，主要是STL格式檔案格式
處理過的運動資料給予機器，進而製造模型。
將模型經過後處理才算完成。
種類：

固化立體造型（SLA）（stereolithography，SLA）
在1987年，Chuck Hull發明的Stereolithography(立體光刻工藝)被授予了專利。其原理是利用紫外雷射光對於光敏樹脂照射，使其進行聚合反應，特點是有較高的精度和較好的表面質量，能製造形狀特別複雜（如空心零件）和特別精細（如工藝品、首飾等）的零件。

分層實體製造（laminated object manufacturing，LOM）
層片疊加製造工藝是將單面塗有熱溶膠（在被加熱狀態下可產生粘性）的箔材（紙、陶瓷箔、金屬箔等）透過熱輥加熱粘接在一起，位於上方的雷射器按照CAD分層模型所獲資料，用雷射束將箔材切割成所制零件的內外輪廓，然後新的一層箔材再疊加在上面，透過熱壓裝置和下面已切割層粘合在一起，雷射束再次切割，在每一層進行切割和粘合的過程，直至整個零件模型製作完成。

選擇性雷射燒結（SLS）（selective laser sintering，SLS）
在1980年代中期，SLS被在美國德州大學奧斯汀分校的卡爾Deckard博士開發出來並獲得專利，項目由DARPA贊助的[5]。1979年，類似過程由RF Housholder得到專利，但沒有被商業化。 這種工藝也是以雷射器為能量源，透過紅外雷射束使塑料、蠟、陶瓷、金屬或其複合物的粉末均勻地燒結在加工平面上。在工作台上均勻鋪上一層很薄（亞毫米級）的粉未作為原料，雷射束在電腦的控制下，透過掃描器以一定的速度和能量密度按分層面的二維資料掃描。經過雷射束掃描後，相應位置的粉末就燒結成一定厚度的實體片層，未掃描的地方仍然保持鬆散的粉末狀。這一層掃描完畢，隨後需要對下一層進行掃描。先根據物體截層厚度而升降工作台，鋪粉滾筒再次將粉末鋪平，可以開始新一層的掃描。如此反覆，直至掃描完所有層面。去掉多餘粉末，並經過打磨、烘乾等適當的後處理，即可獲得零件。目前應用此工藝時，以蠟粉末及塑料粉末作為原料較多，而用金屬粉或陶瓷粉進行粘接或燒結的工藝尚未獲得實用。

混合沉積造型（FDM）(Fused Deposition Modeling，FDM)
在1980年代，熱溶解積壓成形(Fused Deposition Modeling，FDM)技術由S. Scott Crump開發成功，並在1990年代商業化。 使用FDM工藝生成模型過程的示意圖 1.融化的塑料從噴嘴噴出 2.原材料 3.可移動的工作台 1993年美國Stratasys公司開發出了第一台基於熔融沉積造型的裝置。將CAD模型分為一層層極薄的截面，生成控制FDM噴嘴移動軌跡的二維幾何訊息。FDM加熱頭把熱熔性材料（ABS樹脂、尼龍、蠟等）加熱到臨界狀態，呈現半流體性質，在電腦控制下，沿CAD確定的二維幾何訊息運動軌跡，噴頭將半流動狀態的材料擠壓出來，凝固形成輪廓形狀的薄層。當一層完畢後，透過垂直升降系統降下新形成層，進行固化。這樣層層堆積粘結，自下而上形成一個零件的3D實體。   FDM工藝的關鍵是保持材料的半流動性。這些材料並沒有固定的熔點，需要精確控制其溫度。

3D印刷工藝（3DP、TDP）
3D印刷工藝（3DP） 採用3DP技術的RepRap以聚乳酸為原料生成一個雙曲面 3D印刷工藝，也稱為3D列印。1989年，美國麻省理工學院的Emanuel M. Sachs和John S. Haggerty等在美國申請了3D印刷技術的專利，之後Emanuel M. Sachs和John S. Haggerty又多次對該技術進行完善，形成了今天的3D印刷快速成型工藝。 透過這個工藝，在每一層粘結完畢後，成型缸下降一個距離（等於層厚），供粉缸上升一段高度，推出多餘粉末，並被鋪粉輥推到成型缸，鋪平並被壓實。噴頭在電腦控制下，按照下一個截面的二維幾何訊息進行運動，有選擇地噴射粘結劑，最終構成層面。原理和印表機非常相似，即為3D列印這一名稱的由來。鋪粉輥鋪粉時多餘的粉末被粉末收集裝置收集。如此周而復始地送粉、鋪粉和噴射粘結劑，最終完成一個3D粉體的粘結，從而生產製品。 3DP工藝與SLS工藝都是將粉末材料選擇性地粘結成為一個整體。其最大的不同之處在於3DP工藝不用將粉末材料熔融，而是透過噴嘴本身會噴出粘合劑，將這些材料粘合在一起。

掩模固化法（SGC）
 

噴粒法（BPM）
1995年在麻省理工學院創造了「3D列印」術語，當時的畢業生Jim Bredt和Tim Anderson修改了噴墨印表機方案，變為把約束溶劑擠壓到粉末床，而不是把墨水擠壓在紙張上的方案。該專利隨之而來的是現代的3D列印企業Z公司（Bredt和Anderson創立）和ExOne公司 數位光處理（DLP） 熔絲製造（Fused Filament Fabrication，FFF） 融化壓模（Melted and Extrusion Modeling，MEM） 分層實體製造（laminated object manufacturing，LOM） 電子束熔化成型（Electron beam melting，EBM） 選擇性熱燒結（Selective heat sintering，SHS） 粉末層噴頭3D列印（en:Powder bed and inkjet head 3d printing，PP) 直接金屬雷射燒結（Direct metal laser sintering，DMLS）

# RP(1)-層狀實體製造(Laminated Object Manufacturing, LOM)
=================================================

\[http://www.youtube.com/watch?v=6C7bjzIW610\]

![](http://www.msoe.edu/academics/research_centers/graphics/lom_process.gif)

資料來源：http://www.msoe.edu/academics/research\_centers/reu/solid\_freeform_fabrication.shtml

層狀實體製造(Laminated Object Manufacturing, LOM)，材料是聚乙烯所做成的捲筒，像是飲料店所用的杯口封膜機一樣將材料運送至平台上面，接著施以高溫和壓力在上一層的材料上面，讓上下兩層的材料緊密結合，利用二氧化碳雷射切出3D實物橫切面，經由這樣的過程之後會產生我們所要的實體和所不需要的支撐物，這裡的支撐物稱之為cubes，這樣的支撐物能夠協助模型在製作過程中，不會因為外力而導致實物的偏移，完成之後得先拆除cubes(decubed)，大部分的支撐物只需要輕鬆搖晃就能夠拆除，但是有時候卻得需要靠拔除器來拆除比較複雜的部份，當拆除所有的支撐物之後，得進行拋光和上漆以增加美觀和強度。

Posted on [April 14, 2013](http://192.168.1.233/2013/04/14/rp1-%e5%b1%a4%e7%8b%80%e5%af%a6%e9%ab%94%e8%a3%bd%e9%80%a0laminated-object-manufacturing-lom/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=628&action=edit)

# RP(2)-混合沉積造型(Fused Deposition Modeling, FDM)
============================================

\[http://www.youtube.com/watch?v=UUYtu6D8mpM\]

*   1980年代，FDM技術由S. Scott Crump所開發
*   1990年，FDM商業化。

利用FDM技術的3D printer 在製作模型時，是將熱塑化材料（ABS樹脂、尼龍、蠟等）加熱至半流體狀態，接著利用電腦計算出移動路徑，將輸出的牙膏狀材料一層一層製作成3D立體實體，因此FDM的關鍵是如何保持材料的半流動性，因為此類熱塑性材料並無一定的熔點，因此如何控制加熱頭的溫度是其技術重點。

FDM一般來說會使用兩種材料，一個是用來製作模型本體使用，另外一種是支撐用，材料是熱塑化材料所製成的細絲，移動機構將細絲加入加熱頭，並利用3軸的移動平台執行電腦的路徑規劃，常見的做法是XY軸進行2維的平面移動，每完成一次2D切面，再移動Z軸進行下一層的列印，進而完成整體的3D printer，一旦完成了3D模型之後，使用者必須剝除支撐用的材料或是利用溶劑將其溶解，才算是完成一個零件。

FDM的優點在於他很乾淨且容易使用，熱塑性材料能夠暴露在高溫、化性、潮濕和乾燥的環境，以及承受機械的應力，加上可溶解的支撐材料，可以讓我們製作複雜的幾何圖形和難以用CNC加工的孔洞。

目前比較著名的有這兩家公司：

*   [Makerbot](http://www.makerbot.com/)

http://www.youtube.com/watch?v=V_UUK-1DNW0

*   [Cubify](http://cubify.com/cube/)

http://www.youtube.com/watch?v=Osu5MC2PtMI

Posted on [April 16, 2013](http://192.168.1.233/2013/04/16/rp2-%e6%b7%b7%e5%90%88%e6%b2%89%e7%a9%8d%e9%80%a0%e5%9e%8bfused-deposition-modeling-fdm/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=682&action=edit)

# RP(2)-混合沉積造型(Fused Deposition Modeling, FDM)
============================================

\[http://www.youtube.com/watch?v=UUYtu6D8mpM\]

*   1980年代，FDM技術由S. Scott Crump所開發
*   1990年，FDM商業化。

利用FDM技術的3D printer 在製作模型時，是將熱塑化材料（ABS樹脂、尼龍、蠟等）加熱至半流體狀態，接著利用電腦計算出移動路徑，將輸出的牙膏狀材料一層一層製作成3D立體實體，因此FDM的關鍵是如何保持材料的半流動性，因為此類熱塑性材料並無一定的熔點，因此如何控制加熱頭的溫度是其技術重點。

FDM一般來說會使用兩種材料，一個是用來製作模型本體使用，另外一種是支撐用，材料是熱塑化材料所製成的細絲，移動機構將細絲加入加熱頭，並利用3軸的移動平台執行電腦的路徑規劃，常見的做法是XY軸進行2維的平面移動，每完成一次2D切面，再移動Z軸進行下一層的列印，進而完成整體的3D printer，一旦完成了3D模型之後，使用者必須剝除支撐用的材料或是利用溶劑將其溶解，才算是完成一個零件。

FDM的優點在於他很乾淨且容易使用，熱塑性材料能夠暴露在高溫、化性、潮濕和乾燥的環境，以及承受機械的應力，加上可溶解的支撐材料，可以讓我們製作複雜的幾何圖形和難以用CNC加工的孔洞。

目前比較著名的有這兩家公司：

*   [Makerbot](http://www.makerbot.com/)

\[http://www.youtube.com/watch?v=V_UUK-1DNW0\]

*   [Cubify](http://cubify.com/cube/)

\[http://www.youtube.com/watch?v=Osu5MC2PtMI\]

Posted on [April 16, 2013](http://192.168.1.233/2013/04/16/rp2-%e6%b7%b7%e5%90%88%e6%b2%89%e7%a9%8d%e9%80%a0%e5%9e%8bfused-deposition-modeling-fdm/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=682&action=edit)

# RP(3)-選擇性雷射燒結(Selective Laser Sintering, SLS)
=============================================

\[http://www.youtube.com/watch?v=wD9-QEo-qDk\]

[![](http://upload.wikimedia.org/wikipedia/commons/thumb/3/33/Selective_laser_melting_system_schematic.jpg/800px-Selective_laser_melting_system_schematic.jpg)](http://upload.wikimedia.org/wikipedia/commons/3/33/Selective_laser_melting_system_schematic.jpg)

*   在1980年代中期，由美國德州大學奧斯汀分校(University of Texas at Austin)的Dr. Carl Deckard和學術顧問Dr. Joe Beaman所開發並獲得專利，項目由DARPA贊助的。
*   Dr. Carl Deckard和Dr. Joe Beaman開設DTM公司，使SLS商業化。
*   1979年，類似過程由RF Housholder得到專利，但沒有被商業化。
*   DTM公司現今已經被3D systems公司所收購。

SLS是一種加成式的製造技術，利用高強度的雷射光(例如：二氧化碳雷射)去熔化小部分的材料粉末(例如：塑膠、金屬、陶瓷和玻璃)，使其均勻燒結在加工平台上方，完成一層之後加工平台會下降一層，再鋪上一層很薄的粉末層，電腦控制雷射光束再重複剛剛先前步驟，在新的粉末層對於需要的部分熔化燒結，而沒有經過雷射掃描的部分依然呈現粉狀，最後將其去除多餘的粉末，並經過打磨和烘乾等等後處理步驟，即可得到最終成品。

\[http://www.youtube.com/watch?v=cRE-PzI6uZA\]

Posted on [April 16, 2013](http://192.168.1.233/2013/04/16/rp3-%e9%81%b8%e6%93%87%e6%80%a7%e9%9b%b7%e5%b0%84%e7%87%92%e7%b5%90selective-laser-sintering-sls/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=689&action=edit)

# RP(4)-選擇性雷射燒結(Stereolithography, SLA)
=====================================

\[http://www.youtube.com/watch?v=_9m5gEtow88\]

*   1984年的第一台快速成型機即是使用了SLA技術，目前以SLA的運用最為廣泛。

![](http://proto3000.com/assets/uploads/Images/Stereolithography_apparatus.jpg)

參考資料：http://proto3000.com/

利用UV雷射光照射在光敏樹脂上，使其進行固化，完成一平面之後，再將高度下降，未被照射的樹脂將會維持液態，依照這樣的模式不斷製作多層，最終完成一實體後拿去UV光下進行最終固化過程。使用SLA的優點在於其具有較高的精度和較好的表面，且強度較高。缺點在於價格較昂貴，製作成本高，光敏樹脂對環境有汙染，且容易使皮膚過敏。

[Formlabs](http://formlabs.com/)這家公司就是使用SLA的技術來製作DIY用的3D-Printer，這是他在[KICKSTART的介紹](http://www.kickstarter.com/projects/formlabs/form-1-an-affordable-professional-3d-printer)

\[http://www.youtube.com/watch?v=PZrMRYWFORY\]

他的方式和一般的SLA有些不同，是由底下照射UV雷射光來成型，最主要的優點在於不需要一個巨大的樹脂槽，以避免樹脂的浪費(畢竟家用版本是不需要用這麼大量。)

Posted on [April 24, 2013](http://192.168.1.233/2013/04/24/rp4-%e9%81%b8%e6%93%87%e6%80%a7%e9%9b%b7%e5%b0%84%e7%87%92%e7%b5%90selective-laser-sintering-sla/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=695&action=edit)

# RP(5)-多噴頭塑型(Multi-Jet Modeling, MJM)
====================================

\[http://www.youtube.com/watch?v=Sx2AvY2Qsa8\]

Multi-Jet Modeling技術可以同時噴撒兩種材料，其原理像是噴墨式印表機，先將液態的材料噴灑在平台上面，有些利用冷卻的方式固化或是利用光敏樹脂並加以UV雷射光固化。

[Cresilas公司對於MJM有特別的介紹](http://www.cresilas.fr/modelage-a-jets-multiples/impression-3d-multi-materiaux/)

Posted on [April 24, 2013](http://192.168.1.233/2013/04/24/rp5-%e5%a4%9a%e5%99%b4%e9%a0%ad%e5%a1%91%e5%9e%8bmulti-jet-modeling-mjm/)Author [WilliamChang](http://192.168.1.233/author/williamchang/)Categories [Uncategorized](http://192.168.1.233/category/uncategorized/) [Edit](http://192.168.1.233/wp-admin/post.php?post=725&action=edit)

