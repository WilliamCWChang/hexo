---
title: Robot Framework keywords standard 
date: 2018-07-30 12:00:00
categories:
    - autotest

tags:
    - robotframework
---


# 建立Robot Framework Keywords的目的：
> RobotFramework雖然有提供基礎的Keywords，但仍然有不足的地方需要我們自己創造，但不同功能的keywords會導致需要學習如何使用，這可能導致Keywords會變得有學習成本，因此簡化keywrods和標準化keywords是該issue的目的，期望可以降低未來操作者的學習和閱讀成本，而且累積keywords也能符合DRY理論。
> >In software engineering, don't repeat yourself (DRY)



下圖為RBF的架構圖，在DAC的Autotest內，主要的Keywords放在Test Libraries，而Redmine上的Test Standard，經過Tester撰寫之後，以Test Data形式存在。因此後續主要討論的內容主要在Test Libraries。
![RBF架構圖](http://robotframework.org/img/architecture.png)


---

# Robot Framework Hub

提供Keywords資料庫，可以用來查詢Keywords。
[Robot Framework Hub](http://192.168.111.8:7070/doc/keywords/)

---

Procedure 直接表示為keyword title嗎?

Read
    (TE/DUT) (CounterValue) Should be (XX) in range (RANGE) [by Protocol]
    ${return} =    Get (TE/DUT) (CounterValue) in range (RANGE) [by Protocol]

Write
    Set (TE/DUT) (CounterValue) to (XX) [in range (RANGE)] [by Protocol]

 

 

Set DUT Device To Init With ${CFG_PATH}
Generate Modbus Address From ${CFG_PATH}
Set DUT "NAME" To ${value} In Range ${range} By "SERVICE"
DUT "NAME" Should Be ${value} In Range ${range} By "SERVICE"
example:
Set DUT BOOL_INTERNAL_REGISTER To ${0} In Range ${IR_CHANNEL_RANGE} By ModbusSlave
DUT BOOL_INTERNAL_REGISTER Should Be ${0} In Range ${IR_CHANNEL_RANGE} By ModbusSlave

 

Set TE Device to Init With ${TE_INIT_SETTING}
Set TE "NAME" Value/Status To ${value} In Range ${range}
Set TE Mode To ${value} In Range ${range}
TE "NAME" Value/Status Should Be ${value} In Range ${range}
TE Mode Should Be ${value} In Range ${range}
example:
TE Counter Value Should Be ${0} In Range ${DIO_CHANNEL_RANGE}

 

TECommander擁有自己獨立的介面

其餘因為不同的Service，所以介面又分成一類

TECommander:

Service

Set DUT ${BoolRegister} Value To ${value} In Range ${range} By Modbus