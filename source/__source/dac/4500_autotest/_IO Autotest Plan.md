IO Autotest Plan
===


# Testing Case Template
* Now
	* RD : test standard
	* Itest : robot
	* one radmine map to one robot
* Problem
	* redmine test std. is diff from .robot
	* 待測物更變，測試項也會變更？
* Better
	* redmine std. 快速轉換成 .robot

---

* RD的function test是否包含IO?
	* 例如測試RESTful的時候，IO尚未ready，可否讀取到預設的數值來驗證RESTful已經可以運作？
	* 
* 




* TE

* DUT
	* IO
	* Service
		* RESTful
		* SNMP
		* Modbus














---

# 過去-[考量過去有所不足，所以給予願景]
單打獨鬥越來越困難因應，，具有分工合作的團隊具有相對優勢。
但分工合作本身更加困難，如何


* 最終目標，將自動化概念逐漸融入產業思維，將需要
    * 明確規則 Test Standard
    * 高度重複性 Continue Test
## 對誰有什麼幫助？



# 目前-[完成的功能]
## 我做的部分(重要)
## 硬體架構
## 軟體架構
## 使用方式

# 未來-[期待與問題檢討]
## 問題檢討

### 各種外部Library
* 目前沒有整理得很好，未來持續精進

### Robot FrameWork 
* The keyword "wait_until_keyword_succeeds" will make the following parameters change type from list to unicode.
    > fix bug - put the waiting code in the python 

### IOXPress
* New FWR can't load web default?

### Test Standard
* Itest 所需要的和RD所想要的可能有所不同。
    * RD在意他設計的部分有沒有出現
        * 例如剛剛設計一個欄位，他有出現嗎？
        * RD也同時需要建立測試和debug的思維，避免到最後才進行測試。
    * Itest在意能不能使用
        * 如果規格說有欄位，那麼該欄位對應的功能正常嗎？


* 兩者寫的不同？
    DO -> Power on
    Pulse -> Power On Status
    table problem
