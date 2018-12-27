---
title: devops2017
date: 2018-07-27 11:01:25
categories:
tags:
---




DevOps實施的二大法寶：細微性和解耦 by 徐磊


# 以SDN與NFV為核心建構NetDevOps
## by 羅孟彥


333管理與工程間的銜接點：版控

先將版控建置才會有CI 跟 CD 後來才將文化改進




chef 、puttet 、ansible、vargrant、saltstack <= V.S. => Docker

ALM 軟體生命周期管理（Application Lifecycle Management）

![](http://arock.blob.core.windows.net/blogdata201709/05-191126-70678510-be45-4111-af5e-d0b8798ccd2a.png)

![](https://devmynd-production-uploads.s3.amazonaws.com/uploads/photos/0f511762-2fdd-4c6b-adc5-2316b4ae9ddb.png)

高德拉特博士

五步驟聚焦法
Five Focusing Steps
五步驟聚焦法
辨識 -> 挖掘 -> 服從 -> 突破 -> 重來


限制理論 / 約束理論 / TOC 制約法
Theory of Constraintion, ToC


完成的定義
在 DevOps中「完成的真正定義並非開發部份完成了編碼，而是只有在程式碼經過充分測試並按設計在生產中運行時，程式碼才算完成。」
 鳳凰項目


### 什麼是浪費？
- 庫存、半成品、累積在系統中的存貨
- 非增值的活動


### 真正的浪費
- 每個人時時刻刻在工作的工作
- 非瓶頸資源有鬆弛時間，才有餘裕關注整個系統。


docker, scp, rpm,


## 怎麼規劃自動部署
- 專案開始就要準備 CD

**溝通** 很重要。
多與各種角色溝通，了解 CD 需求。
~~圖例的說明文字不夠大，連第二排都看不太清楚。:(~~
- 用 gitlab hook 串 CD, push 後馬上做。

## 我怎麼知道自動部署成功
 - 科學化的數據證明，不能靠感覺
 - 需求分析
   - 比對，檢查程式碼
     - Hash code 不一樣
     - hash code 要存哪？
     - 範例：存在 DNS 的 TXT record。
     - https://gitlab.com/haway/fh2dns
   - 小型簡單的系統

----

1. 符合 CD 的專案，應該要可以從設定檔進行環境上的切換！例如 `config.php`。

用 Go 語言所打造的 Drone 輕量級容器持續交付平台


Prometheus

部署工具的進展
foreman
puppet

TDD

Uni-test with auto-testing
Daily build

初期架構
WetSite
Database
Redis



# 需求 問題
進度不可預期的原因在於"貪心"
有問題發生，才會有需求產生。
把問題處理掉，便能產生價值。
處理問題的方式有兩種，一種是分析問題，一種是處理掉問問題的人，選擇何種方式取決於需求帶來的價值。
因此需求的價值怎麼評估?來自需求有多肯定?
不要去追逐沒有價值且變動性高的需求，這往往導致過多的時間浪費。




契約式 高內聚 低耦合 服務化架構





品質重要的原因取決於需求本身，

CMMI - Funmction List




# PM 金三角，成本已經算好，品質還沒發生問題之前不重要。
時間
品質
成本

![](https://i.imgur.com/9qWGc1G.jpg)

Terraform - Everything is Code

![](https://i.imgur.com/5vh04t3.jpg)
https://i.imgur.com/5vh04t3.jpg


討論 閉門造車


Trunk-Based Development(TBD)