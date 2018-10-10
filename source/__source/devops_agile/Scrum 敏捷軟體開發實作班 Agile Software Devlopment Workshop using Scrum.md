---
title: Scrum 敏捷軟體開發實作班 Agile Software Devlopment Workshop using Scrum
date: 2018-07-31 18:30:00
tags:
    - agile
---

Scrum 敏捷軟體開發實作班 Agile Software Devlopment Workshop using Scrum

# 講師介紹
* David Ko
* [David Ko的學習之旅]
* [AgileCommunity]
* [Scrum Community in Taiwan]


# 敏捷觀念introduction
## 敏捷開發?
|開發|方法|
|:--|:-:|
|瀑布式開發Waterfall |CMMI   |
|敏捷式開發Agile     |Scrum  |

## 敏捷宣言
[敏捷軟體開發宣言](http://agilemanifesto.org)
> 個人與互動 重於 流程與工具   
  可用的軟體 重於 詳盡的文件   
  與客戶合作 重於 合約協商    
   回應變化 重於 遵循計劃
   
* 想要強調的重點
    * 有效溝通，盡可能避免文件式傳遞訊息
    * 不要半成品，能驗收的軟體才是進度測量的依據
    * 維持穩定且有節奏的步調開發，而非一鼓作氣(後期沒力)
    * 團隊能在活動進行過程中，自我組織並定期自省

* 心得：
> agile開發並非按照標準化流程可以實現，需要團隊內按照原則來發想，但因為並沒有詳細規定實作方式，所以每個人所想像的畫面不一，需要透過溝通來避免該問題發生。避免發生[貨物崇拜]的問題


# Scrum 介紹
{%youtube 502ILHjX9EE %}
## Scrum 是什麼?
* [可參考WIKI說明](https://www.wikiwand.com/zh-tw/Scrum#/%E9%B8%A1%E7%BB%84%E7%9A%84%E6%88%90%E5%91%98)
* ![](http://agilebrick.com/images/agile-process-1.png)

### Scrum 三個重點
* 透明度
    * 團隊狀態 - 站立會議
    * 工作進度 - 燃燒圖
    * 優先順序 - 規劃會議
    * 風險問題 - 站立和回顧會議
* 不斷審查
* 不斷調適

### Scrum 優點
* 快速回饋
* 測試提前開始
* 提早面對問題
* 快速反應新需求
* 最後交付結果接近想像


### Scrum 343
* 3種角色
    * Scrum教練
    * 產品負責人
    * 團隊
  
* 4個會議
    * 發布規劃會議(課程中另有提到)
    * 衝刺規畫會議
    * 需求照料會議(課程中另有提到)
    * 每日站立會議
    * 衝刺審查會議
    * 衝刺回顧會議 
  
* 3項產出
    * 產品待辦清單(產品需求清單Product backlog)
    * 衝刺待辦清單(循環需求清單sprint backlog)
    * 燃盡表


## 檢查清單
* [Nokia Test](https://www.scruminc.com/official-scrumbutt-test-otherwise-known/)
* Crisp's Scrum Checklist
* Boris Gloger's Scrum Checklist

# Scrum 角色
## Scrum Master
* 責任
    * 確保大家正在執行的是正確的Scrum
    * 提出建議，而非指令
* 需要做的事情
    * 輔導建立高效能scrum團隊
    * 協助建立流程
    * 幫團隊提出想法和建議，但不解決(是Team member需要自行處理)
* 不該做
    * 協助管理專案
    * 導入工程實踐(CI, TDD)
    * 負責sprint進度
    * 承諾產品完成
## Product Owner
* 責任
    * 根據ROI(Return On Investment)定義需求的
        * 內容
        * 優先序
        * 發布時間
    * 提供高階驗收標準
    * 闡述願景
    * 維護產品需求清單
* 需要做的事情
    * 澄清需求
    * 為產品成敗負責
    * 了解競爭對手和客戶需求
    * 參加站立會議
    * 維護product backlog
    * 隨時能解決Team member的產品需求疑惑
* 不該做
    * 決定sprint應該完成的工作數量

## Team Member
* 責任
    * 交付
    * 評估
    * 承諾
* 需要做的事情
    * 改善流程
    * 決定task的優先序
    * 承諾達成sprint目標
    * 維護sprint backlog
    * 團隊自己做測試
    * 更新task board和燃燒圖
* 團隊特色
    * 人數約7±2人
    * 共同責任，共同開發
    * 一個好的團隊想要贏得比賽，而不是只是讓比賽結束

# Scrum 需求清單
## 產品需求清單 product backlog
* 全面性－大概要做什麼的清單
* 根據ROI產生優先序
* 可持續更新
* 分成功能性和非功能性
* 多個需求來源，需要在此處整理成一份優先序名單
    * 產品功能
    * Bug
    * 技術債 tech debt
* 如何分優先序?(用猜的?)
    * 團隊投票
    * User Story(可以讓大家都了解用途，更加深入討論使用)
### User Story
* User Story 3C:
    * Card
        * 以使用者立場寫出使用場景
    * Conversation
        * 和PO討論後，整理出故事細節
        * 可以探討不同使用者的想像
    * Confirmation
        * 確保如何驗收
* 如何切割User Story?
    * 按照操作步驟
    * 商業規則
    * 優先建立基礎架構
    * 從簡單做起，複雜的部分可以切割成簡單的步驟
    * by data
    * 非功能需求
    * CURD:（Create）、更新（Update）、读取（Retrieve）和删除（Delete）操作。
    * 如果遇到複雜Scenarios，需要切割成小story
* 切割方法的網路資源
    * [How to Split a User Story](http://agileforall.com/resources/how-to-split-a-user-story/)
    * [Splitting user stories -- the hamburger method](https://gojko.net/2012/01/23/splitting-user-stories-the-hamburger-method/)
    * [Twenty Ways to Split Stories](https://xp123.com/articles/twenty-ways-to-split-stories/)
    
![](https://agileforall.com/wp-content/uploads/2018/02/Story-Splitting-Flowchart.png)

### 什麼是User Story Mapping?
* User Story 在 Mapping 後，會得到**時間關聯**，有助於先設計MVP
    * User Story
        * 優先順序
    * User Story Mapping
        * 優先順序(重要的功能先做)
        * 關聯性(使用者操作過程完整)

![](https://goo.gl/4E6HjB)



## 循環需求清單 sprint backlog
* 如何得到sprint backlog
    1. 從product backlog中依照順序挑選story
    2. 將story拆解成task
    3. 評估task的複雜度和所需要的人力
    4. 提出本次sprint想要處理的數量清單(sprint backlog)
* 一份好的sprint backlog?
    * 每個團員都需要加入討論
    * 每個團員都知道"需求"是什麼
    * 每個團員都明確知道"功能做完"的定義
    * 不要只有計算寫程式的時間，還有整合、環境建置、測試
    * 不要事先指派誰做什麼
    * 不要長時間討論(時間不固定)，容易不專心
    * 站立會議時，即是對sprint backlog提出增減的最佳時機機


# Scrum 會議
## 發布規劃會議(課程中另有提到)
* 目標
    * 決定發布目標
    * 決定story的優先順序
    * 粗估完成story的人力時間
    * 決定什麼時間點要發布
* 重點
    * 不要花時間討論細節(會後討論)
    * 會議前
        * PO已經先預排好story順序
        * 先有spec說明會，RD可以先細想過技術問題
* 步驟
    1. 決定滿足條件
        * 固定時程
            * 團隊速度 x 循環數(time) = 總時間
        * 固定功能
            * 團隊速度 x 循環數(time) = 完成story數
    2. 評估stor 
    3. 決定sprint長度
        * PO多頻繁更新需求?
        * 至少再發布前，能平均有4~5次
        * 基本消費額：能承受多少規劃會議?
        * 建議先固定一個長度，之後再修正也可
    4. 評估團隊速度
    5. 排出story的優先順序
* 估算
    * 原則
        * 找出相對值
        * 從小的開始比較
    * 方法
        * Poker(1,2,3,5,8,13,20,40)
        * Affinity Estimation
        * Relative Estimation

## 衝刺規畫會議
* 心得:
這邊做的事情和發布規劃會議很像，發布規劃會議做的事情比較像是在為衝刺規畫會議做準備，而這邊是實際上的Team Member在製作sprint backlog的過程

* 重點
    * 開始sprint後的第一天
    * 不能更變說好要做的事情
    * 明確確認目標、目前人力
    * PO 如何影響故事被包含進去
        * 重排優先順序
        * 改變單一故事的範圍
        * 拆解故事
    * 團隊如何決定故事要不要在本次處理?
        * 憑感覺
        * 依據各種科學數據來驗證





## 需求照料會議(課程中另有提到)
* 需求不明確的時候，可另外召開說明用
## 每日站立會議
* 雞組和豬組
* 三個問題
    * 昨天做什麼？
    * 今天做什麼？
    * 遇到什麼問題？
* 固定時間、固定地點，最好在工作版前面。
* 壞味道
    * 只向領導報告
    * 遲到罰錢
    * 觀察者(雞組)中斷會議
    * 問題沒人提出

{%youtube B3htbxIkzzM %}

{%youtube tyN-3IrftGY %}


## 衝刺審查會議(Demo Day)
* 不要沒準備或是過度準備
* 部分做完的功能不算是做完
* 不要對於別人的回饋很抗拒
* PO決定是否接受demo結果
* 非功能性需求可用文件報告

## 衝刺回顧會議 
* sprint結束時召開
* 目的在於持續改善
* 務必提出上次會議結果的現狀，避免問題一提再提
* 重點
    * 詢問 not 宣導
    * 對話 not 爭辯
    * 了解 not 防衛
* 多問為什麼
* 決定未來改善事項，不要太多，最多兩項
* 方法
    * Good, Could have been better, Improvment
    * SKS: Stop/keep/start
    * 帆船法
    * fishbone
    * 4L
    * lean cafe
    * world cafe
    * ORID

# Scrum 追蹤和量測的方法
* 燃燒圖
* DoD(Definition of done)
* 工作版如何建立

# Scrum 小筆記
* Scrum 是管理的framework
* 如果單一專案人數太少，那建議不要使用。
* 希望人員在單版本循環中不要快速輪調，不然大家會有很長的適應期。

# 有趣小文章
* [為什麼 Scrum 敏捷方法在亞洲行不通？階級文化和 cost-down 心態殺死效率]
* [The Difference Between Agile, Lean and Lean Startup]
    * Agile tests the product against users. 
    * Lean Startup tests the product against the market. 
    * The key concern of Agile is to avoid creating a product that doesn’t work. 
    * The key concern of Lean Startup is to avoid creating a product that people don’t need. 
* [Why Isn’t Agile Working?]
* [快速認識Scrum的三四三口訣]






# Reference

* 免費電子書 
    * [Scrum and XP from the Trenches](https://goo.gl/16Jyq6)
* 建議閱讀
    * [Scrum懶人包](https://goo.gl/iifHGv)
* 學習連結
    * https://www.scruminc.com/
    * http://agileforall.com/
    * [Scrum理论与实践的轻量级指南第2.0版](http://scrumprimer.org/primers/zh-cn_scrumprimer20.pdf)
    * [Scrum理论与实践的轻量级指南第2.0版 不同譯者](http://scrumprimer.org/primers/zh-tw_scrumprimer20.pdf)
    * [A Lightweight Guide to the Theory and Practice of Scrum
Version 2.0](http://scrumprimer.org/scrumprimer20.pdf)  
    * [scrumguides](https://www.scrumguides.org/docs/scrumguide/v2017/2017-Scrum-Guide-Chinese-Traditional.pdf)

* Cain HC Chen(諶宏軍)<CainHC.Chen@moxa.com>提供的[牆上照片](https://drive.google.com/drive/folders/1xc8r4zC8aoKJcA0End5P_qWOjecoQWon)



* 業界實戰經驗
    * lean from the trenches
    * Scrum and XP from the trenches
* Scrum 經典書籍
    * [Essential Scrum中文版：敏捷開發經典]
    * [Succeeding with Agile: Software Development Using Scrum (Paperback)]
* 長官快速入門
    * [告別瀑布，擁抱Scrum：解析微軟與Adobe如何在30天內開發出新軟體]
    * [SCRUM：用一半的時間做兩倍的事]
* 工程人員必看
    * [Continuous Delivery中文版：利用自動化的建置、測試與部署完美創造出可信賴的軟體發佈]
    * [Specification by Example 中文版：團隊如何交付正確的軟體]
    * [The Art of Unit Testing: with examples in C#, 2/e (Paperback)]
* CMMI v.s. Agile
    * [The Software Project Manager's Bridge to Agility]
    * [Integrating CMMI and Agile Development: Case Studies and Proven Techniques for Faster Performance Improvement (SEI Series in Software Engineering)]
    * [Agile Contracts: Creating and Managing Successful Projects with Scrum 1st Edition]
* Facilitate
    * [誰說我們不能一起做決定Facilitator's Guide to Participatory Decision-Making]
    * [學問：100種提問力創造200倍企業力]
    * [引導者的工具箱 ──帶動會議、小組、讀書會，不怯場更不冷場！]




[David Ko的學習之旅]:http://kojenchieh.pixnet.net/blog
[AgileCommunity]:https://www.facebook.com/AgileCommunity.tw/
[Scrum Community in Taiwan]:https://goo.gl/QHF9ZR
[貨物崇拜]:https://goo.gl/d7m9cc
[Essential Scrum中文版：敏捷開發經典]:http://www.books.com.tw/products/0010716911
[Succeeding with Agile: Software Development Using Scrum (Paperback)]:https://www.tenlong.com.tw/products/9780321579362
[告別瀑布，擁抱Scrum：解析微軟與Adobe如何在30天內開發出新軟體]: http://www.books.com.tw/products/0010647604
[SCRUM：用一半的時間做兩倍的事]:http://www.books.com.tw/products/0010673295
[Continuous Delivery中文版：利用自動化的建置、測試與部署完美創造出可信賴的軟體發佈]:http://www.books.com.tw/products/0010653820
[Specification by Example 中文版：團隊如何交付正確的軟體]:http://www.books.com.tw/products/0010644283
[The Art of Unit Testing: with examples in C#, 2/e (Paperback) ]:https://www.tenlong.com.tw/products/9781617290893
[The Software Project Manager's Bridge to Agility]:https://www.tenlong.com.tw/products/9780321502759
[Integrating CMMI and Agile Development: Case Studies and Proven Techniques for Faster Performance Improvement (SEI Series in Software Engineering)]:https://www.amazon.com/Integrating-CMMI-Agile-Development-Performance/dp/0321714105
[Agile Contracts: Creating and Managing Successful Projects with Scrum 1st Edition]:https://www.amazon.com/Agile-Contracts-Creating-Managing-Successful/dp/1118630947
[誰說我們不能一起做決定Facilitator's Guide to Participatory Decision-Making]:http://www.eslite.com/product.aspx?pgid=1001187001748080
[學問：100種提問力創造200倍企業力]:http://www.books.com.tw/products/0010463047
[引導者的工具箱 ──帶動會議、小組、讀書會，不怯場更不冷場！]:http://www.books.com.tw/products/0010420449
[為什麼 Scrum 敏捷方法在亞洲行不通？階級文化和 cost-down 心態殺死效率]:https://goo.gl/GEut3a
[The Difference Between Agile, Lean and Lean Startup]:https://goo.gl/mka8Xq
[Why Isn’t Agile Working?]:https://hackernoon.com/why-isnt-agile-working-d7127af1c552

[快速認識Scrum的三四三口訣]:https://www.ithome.com.tw/node/68213
