Autotest 周會
===




















# 2018/06/21
* 6/29 DI Ping 確認可不可以提早拿到DI Module
* test id
* Session login會不會完成
* 找 Eric 拿 spring3 表格確認
* IP 表格 整理
* mantis 更新了，我host這塊。

---

# 上周提到的問題
* AI config parser 完成時間會是什麼時候?
* 45M IO with Safe Mode
	* 詢問什麼時候得完成?
	* 六月最後一周
* 下周6/21找Software RD決定最後的功能有哪些。
	* 6/22確認
* 什麼時候決定把哪些功能延後?
* 改版本(0.9->1.0)的時候要再把E-test在跑過一次。

----

* Web frontend(6/22)
	* backend還在規劃中，時間明天確認
* 先規劃出哪些需要自動化的項目。從TJ的表格
* Noka 如何定義成功傳完資料???? 
	* 可以詢問Eric有沒有和PM談過
	* 使用者如何了解成功的定義
	* 找Noka確認流程圖
	* 和Austing討論該行為是否正常

---

# 任務現況
(各自現況?、有無資源議題?、有無尚未分配的任務?)
* AI
* Safe Mode
* Web
* TC RTD 精準度問題

---

## Function test

----

### Protocol
| Feature | DI | DO | RL | TC | RTD | AI |
|:-------:|:--:|:--:|:--:|:--:|:---:|:--:|
| SNMP    | v  | v  | v  | v  | v   |    |
| RESTful | v  | v  | v  | v  | v   |    |
| modbus  | v  | v  | v  | v  | v   |    |

----

### IO
* 45M IO with Safe Mode
* Reset-to-Default and Rescue
* AI (Iocommender要如何重新設計ai的部分)

----

### Config
* Config and Upgrade with Security
### SYSTEM
* device ready status (LED)?

----

### Web
* Noka討論 internal. Error 可以使用system error 但是該功能還沒做
* Dashboard. 等待 backend 6/19初稿 6/22完成
* 目前暫無Session control(login page)





---

## CI
後續William和tj接CI的部分(upgrade FWR) 

---


# 資源

* 還有什麼資源沒有取得
	* 硬體方面(士益提供轉接板等等)
		* 6/15拿到ai兩組×2(voltage and current)
		* 6/29拿到全部的sysytem test用的模組
		* Power Module規劃和Hardware拿取的時間(dumyy power module *4)
		* autotest 不需要測試Power Module
		* 6/29的AI硬體會晚到，可能會延後到7/3號拿到ai模組
	* 軟體方面(缺少什麼function)
	* [I-Test 需求清單](https://goo.gl/Bjw4jP)
	
---





---

# 額外討論
* Redmine使用(會有很多的notification)


* 盡可能以redmine來討論和統整資料
	* http://dac-redmine.moxa.com/projects/autotest/issues
* 目標設定為6/29需要完成的項目(v0.9)
	* https://goo.gl/uyxiVT


---

## System Test

----

### Scenario 1
* 模擬最常見的IO組合
	* IO modules x 8
* 模擬OT
	* ModbusTCP Slave
* 模擬IT
	* Restful/SNMP
* 模擬客戶
	* Http

### Scenario 2
* 模擬極限的IO模組組合
	* IO modules x 32