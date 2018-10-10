---
title: DAC IO測試手法
date: 2018-07-27 11:01:25
categories:
    - IO

tags:
    - IO
    - DI
    - DO
    - Pulse
    - AI
    - RTD
    - TC
---

# about
這篇文章主要寫該怎麼測試這些IO



# IO Itest Design Guide Line
* 測試分成service 和 IO測試項目

* 主幹:modbus

* service (A in b out觀念)
    - 只有測試結果的狀態變化，不特別針對IO功能測試
        - DUT GET
            - A=TE, B=Service
        - DUT SET 
            - A=Service, B=modbus(不明確的地方在於要不要檢查IO結果，我認為不要)
    - 安全性測試
    - check system info

* modbus slave service (主幹)
    - 只有測試不同point type可否正常讀取和寫入

* IO (by 主幹=main_service) 假設主幹已經測試過的狀態下進行
    - 因為不是service，所以沒有service A進B出的概念。
    - 主要認定main_service的功能為正常才可以測試IO
    
* RESTful 不管DI還是DO都要測試，只是DI會fail，DO會pass

* pulse poweron=on 應該要測試 count=0 是否可以利用modbus set pulse status=off







# IO
* By Channel type
    - DI
    - DO
    - RL
    - AI
    - RTD
    - TC
    - AO
* By sw inforamtion
    * Mode
    * Index
    * Name
* SYSTEM



# 作為軟體測試需要具備技能
* 快速架設環境
* 了解應用的story
* 找bug技巧
* 升級自身能力？


# 撰寫mantis須知
* 需要寫上version版本




# 想法
無法在protocol 測試的範圍，就放到IO測試
測試初期需要掌握全體方向來測試，了解範圍，設定目標，決定何謂完成，確認時間

Q: Counter status 為 stop，其value是否應該讀得到數值?
A: Yes

# RESTful 驗證方法
r/o 則 GET
r/w 則 Get and put

PUT後，需要先GET來確認


# 額外需要探討的問題
* 軟體還沒做的時候要測試嗎？
* 分類和名稱命名很重要，如果名稱常常不同的話，在不同地方得用不同的方式來稱呼一個東西會很麻煩。

* redmine使用kanban board不好管理，task深深深似海，太長了，無法按照自己想要的順序管理。
    * 未來需要更加圖像化來了解目前的管理進程
    * 需要一張表格知道目前每個task進度，每個人的運作狀況
* 測試的過程在於希望結果符合預期，如果測試足夠詳細，將可以知道產品在哪邊會有缺點，

# By 黑白箱差異
## 黑箱－了解我們的產品會被怎麼用
黑箱基本上很難計算程式涵蓋率，因為你根本不知道程式寫怎樣，當你知道而依據程式來測試，那就變成白箱測試了，而黑箱測試是依據使用者的角度來看，因此，了解產品會被如何使用，便是取得**使用方式**的涵蓋率。





# RESTful 4500
## AI
### AIIndex_AIName_AIMode_Get 6152
    1. config set mode = 0-10V
    2. restful check aiIndex
    3. restful check aiName
    4. restful check aimode
    5. config set mode = 0-20mA
    6. restful check aimode
    7. config set mode = 4-20mA(B)
    6. restful check aimode
    7. config set mode = 4-20mA
    6. restful check aimode
    7. config set mode = +-10V
    6. restful check aimode
    7. config set aiName = max_string 
    8. restful check aiName

### AIValue_Get 8504
    1. config set mode to ...
    2. IOCommender set AO (0,1024,2048,3072, 4095)
    3. modbus get scaled/raw max_min_value
    4. restful check scaled/raw max_min_value

### AIValueMaxMin_Get 8596
    1. import config to mode
        2. modbus set maxmin_reset to ON
        2. IOCommender set AO (0,1024,2048,3072, 4095)
        3. modbus get scaled/raw max_min_value
        4. restful check scaled/raw max_min_value
    5. XXXXXXXXXXXXXXXXX
        2. modbus set maxmin_reset to ON
        6. IOCommender set AO (4095, 3072, 2048, 1024, 0)
        7. modbus get scaled/raw max_min_value
        8. restful check scaled/raw max_min_value
    9. change to other mode and test

### AIValueMaxMin_Put 8597
    1. import config to mode
        2. IOCommender set AO (0,1024,2048,3072, 4095)
        3. modbus get scaled/raw "max_value"
        4. restful check scaled/raw "max_value"
    5. restufl set  maxmin_reset to ON
        3. modbus get scaled/raw "min_value"
        4. restful check scaled/raw "min_value"

    5. XXXXXXXXXXXXXXXXX
        2. IOCommender set AO (0,1024,2048,3072, 4095)
        3. modbus get scaled/raw "max_value"
        4. restful check scaled/raw "max_value"
    5. restufl set  maxmin_reset to ON
        3. modbus get scaled/raw "min_value"
        4. restful check scaled/raw "min_value"
    9. change to other mode and test

### AIBurnoutValue from(AIStatus 13410)
    2. import config set mode to BO value to 2
    3. RESTful check ai-BO-value is 2
    2. import config set mode to BO value to 3
    3. RESTful check ai-BO-value is 3

### AIStatus 13410
    1. import config set mode to burnout mode
    2. import config set mode to BO value to 1.8(not default)
    3. IOCommender set ao-raw-value to 20mA
    4. RESTful check ai-status is 0
    3. IOCommender set ao-raw-value to 2.5mA
    4. RESTful check ai-status is 3
    3. IOCommender set ao-raw-value to 1.25mA
    4. RESTful check ai-status is 1



## DI
- [x] DIStatus_Get 5773
    1. config set status = 0
    2. io set status = 1
    3. restful check status = 1
    4. io set status = 0
    5. restful check status = 0
- [x] DIIndex_DIName_DIMode_Get 5666
    1. config set mode = di
    2. restful check index = 0,1,2,3...
    3. restful check name = DI_00
    4. restful check mode = di
    5. 
    6. config set mode = counter
    8. restful check mode = counter
    9. 
    10. config set ch-name = DI-XX_123....
    11. restful check name = DI-XX_123....

## Counter
- [x] CounterStatus_Get 5774
    1. config set status = 0
    2. restful check status = 0
    3. config set status = 1
    4. restful check status = 1
### CounterStatus_Put 5779
    1. config set status = 0
    2. restful check status = 0
    3. 
    4. restful set status = 1
    5. restful check status = 1
    6. io set count = 100 
    7. io set status = start
    8. restful check value = 100
    9. 
    10. restful set status = 0
    11. restful check status = 0
    12. io set count = 100 
    13. io set status = start
    14. restful check value = 0
### CounterValue_Get 5775
    1. config set status = 1
    2. io set count = 100
    3. restful check value = 100
    4. 
    5. io set count = 65535
    6. restful check value = 65535+100 (more than 1 word)
### CounterValue_Put 5778
    1. config set status = 1
    2. restful check value = 0
    3. 
    4. restful set value = 100000
    5. restful check value = 100000
    6. modbus check value = 100000
    7. 
    8. restful set value = 100
    9. restful check value = 100
    10. modbus check value = 100
### CounterOverflowFlag_Get 5776
    1. config set value = 4294967280 (MAX-16)
    2. config set status = 1
    3. 
    4. modbus check of_flag = 0
    5. restful check of_flag = 0
    6. restful check status = 1
        > 可以remove
    7. restful check value = 4294967280
    8. 
    9. io set count = 100
    11. io set status = 1
    12. 
    13. modbus check of_flag = 1
    14. restful check of_flag = 1
    15. restful check status = 1
        > 可以remove
    16. restful check value = 184
    17. 
    18. modbus set of_flag_clear = 1
    19. 
    20. modbus check of_flag = 0
    21. restful check of_flag = 0
    22. restful check status = 1
        > 可以remove
    23. restful check value = 184
### CounterOverflowFlagClear_Put 8491
    1. config set value = 4294967280 (MAX-16)
    2. config set status = 1
    3. 
    4. modbus check of_flag = 0
    5. restful check of_flag = 0
    6. restful check status = 1
        > 可以remove
    7. restful check value = 4294967280
    8. 
    9. io set count = 100
    11. io set status = 1
    12. 
    13. modbus check of_flag = 1
    14. restful check of_flag = 1
    15. restful check status = 1
        > 可以remove
    16. restful check value = 184
    17. 
    18. restful set of_flag_clear = 1
    19. 
    20. modbus check of_flag = 0
    21. restful check of_flag = 0
    22. restful check status = 1
        > 可以remove
    23. restful check value = 184
## DO
- [x] DOStatus_Get 5782
    1. config set status = 0
    2. restful check status = 0 
        > recommend to remove the step, the step should test in IO items)
    3. modbus set status = 1
    4. restful check status = 1
    5. modbus set status = 0
    6. restful check status = 0
- [x] DOStatus_Put 8415
    1. config set status = 0
    2. restful check status = 0
        > should be removed
    3. restful set status = 1
    4. modbus check status = 1
    5. io check status = 1
    3. restful set status = 0
    4. modbus check status = 0
    5. io check status = 0
- [x] DOIndex_DOName_DOMode_Get
### DO PowerOnStatus

## Pulse
### PulseStatus_Get 5815
    1. config set count = 0
    2. restful check status = 0
    3. 
    4. modbus set status = 1
    5. io check value =/= 0
    6. restful check status = 1
    7. 
    8. modbus set status = 0
    9. io check value = 0
    10. restful check status = 0
### PulseStatus_Put 8489
    1. config set count = 0
    2. restful check status = 0
    3. 
    4. restful set status = 1
    5. io check value =/= 0
    6. restful check status = 1
    7. 
    8. restful set status = 0
    9. io check value = 0
    10. restful check status = 0
### PulseCount_Get 5817
    1. config set count = 100
    3. restful check count = 100
    4. modbus set status = 1
    5. io check value = 100
    6. 
    7. config set count = 10000
    8. restful check count = 10000
    9. modbus set status = 1
    10. io check value = 10100
### PulseCount_Put 8490
    1. config set count = 100
    3. restful check count = 100
    4. modbus set status = 1
    5. io check value = 100
    6. 
    7. restful set count = 200
    8. restful check count = 200
    9. modbus set status = 1
    10. io check value = 300
    11. 
    12. restful set count = 10000
    13. restful check count = 10000
    14. modbus set status = 1
    15. io check value = 10300
### PulseOnOffWidth_Get 8594
    1. config set count= 100
    2. 
    3. config set width = 20
    4. io set filter=1
    5. restful check width = 20
    6. modbus set status = 1
    7. io check count = 100
    8. 
    9. config set width = 160
    10. io set filter=15
    11. restful check width = 160
    12. modbus set status = 1
    13. io check count = 100
    14. 
    15. config set width = 65535
    16. restful check width = 65535
### PulseOnOffWidth_Put 5821
    1. config set count= 100
    2. 
    3. config set width = 20 
    4. io set filter=1
    5. restful check width = 20
    6. modbus set status = 1
    7. io check count = 100
    8. 
    9. restful set width = 160
    10. io set filter=15
    11. restful check width = 160
    12. modbus set status = 1
    13. io check count = 100
    14. 
    15. restful set width = 65535
    16. restful check width = 65535


## IR
- [x] IRTable_Get 6115
    1. config set value = 0
    1. restful check value = 0
    1. modbus set value = MAX
    1. restful check value = MAX
    > 1. same step
- [x] IRTable_Put 8543
    1. config set value = 0
    1. restful check value = 0
    1. restful set value = MAX
    1. modbus check value = MAX
    > 1. same step

## SYS
### ServiceEnable 5475
### SysInfoTable 6040
### SysInfoTable_Device 6082
### SysInfoTable_Network_LAN 6083

