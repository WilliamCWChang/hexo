test id
=====

Hi ALL 

把早上討論的東西我在這邊整理一下。 

遇到的問題： 

Spec. ID的顆粒度大小設計。 

l 有些Spec ID項目很難開到很細節，例如RESTful DO Status可以Get和Put，但只會開一項Spec. ID。 

l 如果Spec. ID沒有開很詳細，會導致測試項目無法追蹤，測試項目目前以2500為例，會利用Redmine Issue來追蹤有無寫過該測試項目。 

l 流程： 

n PM開Spec ID 

n RD開 Redmine issue 後寫功能 

n ITEST 開 Redmine testcase standard issue 後寫 robot file

n 進行autotest 

l 流程上遇到的問題：會同時開兩份不同的issue，中間的對應很模糊， 

解決方法討論： 

名稱定義： 

Spec ID：PM開規格的時候所提供的EXCEL 

Test ID：我們未來將要整理的表格。 

1. Spec ID和Test ID應該都屬於獨立的，不能有重複。 

2. Spec ID 會在Redmine上開issue，將來會從robot轉換成report 

3. Test ID 是因應Spec ID的不足，所以另外加開。Spec ID不等於Test ID的原因，一個Spec ID可能對應到不同的測試項目，例如DO Status GET和PUT兩個測試項目，所以可以使用Test ID作為Testcase Name來對應。 

4. Spec ID轉換到Test ID的過程需要RD來確認，目前屬於手動轉換，希望未來可以自動從PM的Spec ID轉換到Test ID，然後再來補齊剩餘的部分。 

5. 可以考量是否在robot裡面加註Test ID，希望方便追蹤測試項目。 

�"
