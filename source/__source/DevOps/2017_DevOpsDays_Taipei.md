---
title: DevOpsDays Taipei 2017
date: 2018-07-27 11:01:25
categories:
tags:
    - course
---

9 / 04 - 9 / 06 台灣大學社會科學院大樓



## What's DevOpsdays?
DevOpsdays是全球性的技術系列盛會，由各地城市組織，主要探討
* Dev - 軟體開發
* Ops - IT維運



## 9/4 MON - 開放空間

* 1983 Harrison Owen
* 咖啡休息時間
* 雙腳法則
* 新聞牆投票



## 開放空間 Open Space

* 四大原則
    * whoever come is the right people.
    * whenever it starts is the right time.
    * Whatever happen is the only thing that could have.
    * When it's over，it's over.



## 9/5 TUE
* DevOps to Agile 敏捷轉型經驗(William Yeh) 
* 怎麼讓老闆願意接受敏捷？(91) 
* 持續改善：找出流程中的瓶頸與浪費(Erica Liu) 
* 微服務場景下的Serverless架構實踐(無敵西瓜)
* 百倍速交付-談主幹開發(Bryan Liu)
* DevOps在企業導入的文化衝擊與實踐方案(David Dong)
* Terraform - Everything is Code(Smalltown)
* 如何與 Git 優雅地在樹上唱歌(Kewang)



## 9/6 WED
* 開啟DevOps之路的系統思維(Ruddy)
* DevOps，使持續交付成為可能(喬梁)
* 網站上線了，然後呢？(陳鋒逸)
* DevOps實施的二大法寶：細微性和解耦(徐磊)
* DevOps的核心理念和實踐(Martin)
* 用 Go 語言所打造的 Drone 輕量級容器持續交付平台(Appleboy)
* CD 前的煩惱，如何蓋掉你的程式碼(HaWay)
* Prometheus: monitoring and alerting with an open source solution(Clsung)



## Agenda
* 導入 - 如何說服與讓人接受
* 概念 - 發現問題和尋找理論
* 工具 - 幫住自我實現的工具



## 當天談到的東西？

`git`, `實例化需求`, `Agile`, `Code Style`, `CD`, `結對編程`, `code review`, `CI`, `unit test`, `整合測試`, `不可變架構Immutable infrastructure `, `Infrastruture as Code`, `Terraform`, `Puppet`, `Docker`, `Bash`, `Automation`, `自動展延`, `高可用性`, `Elastic Search`, `Fluentd`, `Kibana`, `Cloud Watch`, `MOnit`, `dashboard`, `ChatOps`, `Notification`, `Operation`, `Retrospective`, `Canary deployment`, `A/B testing`, `Centralized logging`, `Monitoring & proﬁling`, `6步提交法`, `契约式 `, `高内聚低耦合`, `服务化架构`



## 由來

* The Incredible True Story of How DevOps Got Its Name
* 2009/06/23
* O’Reilly Velocity
* “10+ Deploys per Day Dev and Ops Cooperation at Flickr”



## 個人看法
1. 因應市場變化快速 + 精實創業流行(MVP)
1. 為了提高競爭力，需要創新且更多的功能
1. 提高code的產生速度 (Agile)
1. 為了維護品質，測試和發布的時間隨之增加 (CI/CD)



# DEVOPS!

為了因應市場快速變化，且在不降低品質的前提下，所得出的一種合作方式。

![](https://cdn-images-1.medium.com/max/1600/1*TNJ7Rpr5G1OJHtKH-IBEFw.png)



## 如何達到DevOps? 三步工作法!

![The DevOps Three Ways](https://i.imgur.com/SR5MNhu.png)



## 系統思維 

### 軟體產品的全貌 = Dev + Ops
* 薩提爾Satir - 冰山理論 
* 看見問題全貌，避免進入線性思維



## 實行 Dev + Ops 從敏捷開始
* 2001 SCRUM，對付*需求多變*的開發作業
* 2001 敏捷Agile，針對「專案開發」
* 2012 精益創業Lean Startup (Minimum Viable Product)
* 2010 Kanban 消除浪費
* ???? System Thinking「第五項修練」
* 2012 The DevOps Three Ways by Gene Kim



## 概念 - 約束理論 Theory of constraints (TOC) 

* Eliyahu M. Goldratt 高德拉特 於 1984年 提出TOC
    * 「目標」(The Goal)
    * 「關鍵鏈」(Critical Chain)
* 每個系統的績效， 是受制於非常少數的 constraint 因素。



## 概念 - TOC 5 Step
Example 童子軍的小胖子賀比
1. 找到賀比 Identify 
2. 了解賀比 Exploit 
3. 接納賀比 Subordinate 
4. 提升賀比 Elevate 
5. 下個賀比 Prevent Inertial 



## DevOps is about CAMS

![](http://www.jedi.be/blog/2012/05/12/codifying-devops-area-practices/devops-areas-cams.png)



## DevOps is about CALMS

* *C*ulture
* *A*utomation -> CI/CD
* *L*ean -> MVP
* *M*easurement -> Show the improvement 
* *S*haring -> Dashborad 



## 看板文化

### 在對的時間，做對的事，而且一定要*被看見*。

* 看板能找到瓶頸來限制複雜度 TOC
* 幫助成員找領先指標
* 計分板了解情況



![William Yeh的看板文化](https://image.slidesharecdn.com/devopstoagile-170904025428/95/devops-to-agile-from-devops-to-agile-transformation-experience-of-gogolook-87-638.jpg?cb=1505049281)



## 價值優先序

怎麼讓老闆願意接受敏捷？感知市場變化 ，提升賺錢效率！

![PM iron triangle](http://intersog.com/wp-content/uploads/2016/06/Screen-Shot-2016-06-02-at-4.23.58-PM.png)



## CI/CD

* Continuous Integration
* Continuous Delivery
* Continuous Deployment

![](https://i1.read01.com/uploads/0E5vUB7539.jpg)



## 你做的是測試嗎？
- 預期會發生的行為 → **驗證** → 機器
    - 例如：登入
- 找出意料外的行為 → **測試** → 人
    - 找出預期之外
- 讓驗證自動化



## 持續整合 - 六步提交法

![](https://image.slidesharecdn.com/random-110723092658-phpapp01/95/-12-728.jpg?cb=1311413344)



## [Trunk Based Development](http://nedwu13.blogspot.tw/2014/01/tbd-what-is-trunk-based-development.html)


## [Feature Toggles](https://martinfowler.com/articles/feature-toggles.html)



## Tools Introduction 1

* Automation
    * Jenkins, TeamCity, Travis
* Configuration Management
    * Chef, Puppet, Ansible
* Compute Virtualization
    * VMware, Vagrant, Docker, AWS, OpenStack
* Data Virtualization
    * Delphix, OpenZFS, Flocker



## Tools Introduction 2

Elasticsearch, Logstash, Kibana, Kubernetes, Docker, Ansible, Prometheus, Terraform, Puppet, foreman



![Tools](http://www.jamesbowman.me/post/cdlandscape/ContinuousDeliveryToolLandscape.jpeg)



# 不錯的投影片
http://s.itho.me/devopsdays/2017/sessions/0906-202/0906.202-2%20%E5%A6%82%E4%BD%95%E6%9C%89%E6%95%88%E7%AA%81%E7%A0%B4DevOps%E8%BD%AC%E5%9E%8B%E7%9A%84%E4%B8%B4%E7%95%8C%E7%82%B9%20-%20%E5%BC%B5%E6%A8%82.pdf



## Book 1

* Git for Teams!!!!
* 目標：簡單有效的嘗試管理
* 看版方法：科技企業漸進變革成功之道
* 第五項修鍊
* 薩提爾
* 鳳凰項目-沙盤工作坊
* ansible for devops
* effective DEVOPS



## Book 2

* 微服務架構與實踐
* 持續交付︰發布可靠軟件的系統方法
* The DevOps 2.0 Toolkit
* the machine that changed the world
* DevOps Handbook
* 軟件開發本質論



# 心得

在連續兩天的課程中，學習許多DevOps觀念和了解社群的發展現況。"敏捷開發"起源是來自近年來的APP新創，為了快速反應市場變化而加速開發過程，當開發過程加速後，接著產品上線速度瓶頸來到了運維單位。雖然敏捷開發對於公司而言，現階段的實用面不高，但其發展的技術，測試自動化、持續整合，卻是對軟體品質提升有相當程度的助益。因為在產品數量上升的過程中，缺乏自動化的管理和部屬測試，可能導致人為失誤，甚至需要更多的溝通成本。個人認為或許不需要一時急著大量導入來改變，但如能從現有DevOps中找到適合的概念和工具，應能提升個人和部門的管理效率。