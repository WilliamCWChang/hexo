---
title: security_model
date: 2018-08-22 12:00:00
tags:
    - course
---

# BLP安全模型（Bell-Lapadula security model ）

Bell-lapadula是20世紀70年代，美國軍方提出的用於解決分時系統的信息安全和保密問題，該模型主要用於防止保密信息被未授權的主體訪問。
使用Bell-lapadula模型的系統會對系統的用戶（主體）和數據（客體）做相應的安全標記，因此這種系統又被稱為多級安全系統，級別和模型用於限制主體對客體的訪問操作，該模型用於加強訪問控制的信息保密性。
Bell-lapadula使用主體，客體，訪問操作（讀，寫，讀/寫）以及安全級別這些概念，當主體和客體位於不同的安全級別時，主體對客體就存在一定的訪問限制。實現該模型後，它能保證信息不被不安全的主體所訪問。
Bell-lapadula有三條強制的訪問規則：簡單安全規則（simple security rule）,星屬性安全規則（star property）,強星屬性安全規則（strong star property）.簡單安全規則表示低安全級別的主體不能從高安全級別客體讀取數據。星屬性安全規則表示高安全級別的主體不能對低安全級別的客體寫數據。強星屬性安全規則表示一個主體可以對相同安全級別的客體進行讀和寫操作。
所有的MAC系統都是基於BELL-LAPADULA模型，因為它允許在代碼裡面整合多級安全規則，主體和客體會被設置安全級別，當主體試圖訪問一個客體，系統比較主體和客體的安全級別，然後在模型裡檢查操作是否合法和安全。下圖是對bell-lapadula模型的簡要描述：
Subject(主體) Object(客體)
1．當安全級別為Secret的主體訪問安全級別為Top Secret的客體時，簡單安全規則（simple security rule）生效，此時主體對客體可寫不可讀（no read up）；
2．當安全級別為Secret的主體訪問安全級別為Secret的客體時，強星屬性安全規則(strong star property)生效，此時主體對客體可寫可讀；
3．當安全級別為Secret的主體訪問安全級別為Confidential的客體時，星屬性安全規則( star property)生效，此時主體對客體可讀不可寫(no write down)；

https://zhidao.baidu.com/question/16926494.html

# Biba Model

# Clark–Wilson model 


https://ithelp.ithome.com.tw/articles/10193613


狀態機模型 (State Machine Models)：用來保證所有被存取的 O，在各種 S 存取用例中皆安全。
信息流模型 (Information Flow Models)：用來避免未經授權的信息流發生。
互不干擾模型 (Noninterference Models)：用來保證 S1 的動作，不會影響到 S2 之存取狀態。
取予模型 (Take-Grant Models)：用來避免 S1 的權限，被非法轉送給 S2。
BLP 保密模型 (Bell–LaPadula Confidentiality Model)：
每個 S 都有許可證 (Clearance)，許可證劃分為不同層級，而每個 O 也有分類等級 (Classification)，當 S 和 O 位於不同的安全級別時，S 對 O 就存在一定的存取限制，此模型能保證資源不被不安全的主體所訪問。
Biba 完整性模型 (Biba Integrity Model)：較低安全層級之 S，不能「寫入 (Writing)」較高安全層級之 O。
Clark-Wilson 模型：是透過稽核的方法，來保證資料整全性。



ISO/IEC 27001
ISO/IEC 15408