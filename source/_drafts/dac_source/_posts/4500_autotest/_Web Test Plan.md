 Web Test Plan
 ===
 
## Test Suite 大類別
* Test case name
    * Given-在什麼情況下-確定狀態
    * When-進行什麼操作-將狀態轉換成另外一組狀態
    * Then-預期結果-修改後的狀態符合預期
    結果
* ! 有問題想要問

---

## Config Upload and change Mode
* config_validation.robot
    * Export Config 
        * ! config 的 import 和 export 如何驗證其是否正確?有無正確格式?
        - Given	Reset DUT to Default.
        * When	go to page "systemSetting"
        * ANd 	download config "old_device"
        * Then	check device name is change
    * Import Valid config
        * Given	Reset DUT to Default.
        * When	go to page "systemSetting"
        * And 	load config "valid_config"
        * Then	display "successful"
        * When	restart
        * Then	check device name is "valid_config"
    * Import Invalid config
        * Given	Reset DUT to Default.
        * When	go to page "systemSetting"
        * And 	load config "Invalid_config"
        * Then	check display error code
            - (檔案少一半)
            - (格式錯誤)

---

## Security
### RIO_Security_WebLogin

- [ ] Login with Right Password by (user/operator/admin)
    * Given Reset DUT to Default.
    * When  Login with (user/operator/admin) and right Password
    * Then  Display login Successful
    * And   Check is (user/operator/admin) Page
- [ ] Login with worng Password by (user/operator/admin)
    * Given Reset DUT to Default.
    * When  Login with (user/operator/admin) and wrong Password
    * Then  Display login Failed
- [ ] Login with worng Username and default password
    * Given Reset DUT to Default.
    * When  Login with "adminmoxa" and password "moxa"
    * Then  Display login Failed
- [ ] Login with worng Username and password
    * Given Reset DUT to Default.
    * When  Login with "adminmoxa" and password "moxamoxa"
    * Then  Display login Failed


### RIO_Security_Change Username and Password
    * ! Username/Password validation by (user/operator/admin) 詢問eric，是否在還未送出之前就進行密碼檢查，或是等到重新啟動後才會顯示密碼修改錯誤
    * Old Password incorrect by (user/operator/admin)
        - ! 無法測試Old Password incorrect，因為如果輸入錯誤的舊密碼，便無法輸入新密碼，欄位被設定成無法輸入。
        * Given Go to Page  /security/ServiceSettings
        * When  Set old Password "moxamoxa" 
        * And   Set new Password "1234567890abcdef1234567890abcd"
        * Then  Change Password Failed
    * Set blank new Password by (user/operator/admin)
        * Given Go to Page  /security/ServiceSettings
        * When  Set old Password "moxa"
        * And   Set new Password "" (! 是否允許空密碼)
        * Then  Change Password Failed
    * Set new Password and Login with new U/P by (user/operator/admin)
        * Given Go to Page  /security/ServiceSettings
        * When  Set old Password "moxa"
        * And   Set Password "newmoxa"
        * And   Set UserName "newuser"
        * Then  Change Password Successful
        * When  Logout and login with old U/P
        * Then  Login Failed
        * When  Logout and login with new U/P
        * Then  Login Successful
    * Change Password to defalut by user and Login with default by (user/operator/admin)
        * Given Go to Page  /security/ServiceSettings
        * When  Set new Password "moxa"
        * And   Set Password "moxa"
        * And   Set UserName (user/operator/admin)
        * Then  Change Password Successful
        * When  Logout and login with new U/P
        * Then  Login Failed
        * When  Logout and login with old U/P
        * Then  Login Successful

### RIO_Security_RetryAndTimeout
- ! (user/operator/admin) 是否共用 idle time, lockout time?
- ! 換成一個新的browser可以登入嗎
* Login and idle 5 min (改成不斷檢查，確保是在五分鐘後才出現，而不是睡五分鐘)
    * Given Reset DUT to Default
    * When  Login with (user/operator/admin) and right Password
    * And   Sleep 5 min
    * Then  Alert Session logout
* Set Idle Timeout
    * Given Reset DUT to Default
    * And   Set Idle Timeout  1 min
    * And   Logout
    * When  Login with (user/operator/admin) and right Password
    * And   Sleep 1 min
    * Then  Alert Session logout
* Disable Idle Timeout
    * Given Reset DUT to Default
    * And   Set Idle Timeout  0 = disable
    * And   Logout
    * When  Login with (user/operator/admin) and right Password
    * And   Sleep 6 min (超過5min)
    * Then  No Alert Session logout
* Login fail and retry 5 times
    * Given Reset DUT to Default
    * When  Login with (user/operator/admin) and incorrect Password 5 times
    * Then  Display login fail
    * When  Input right Password
    * Then  Display login fail
    * When  Sleep 5min
    * And   Input right Password
    * Then  Display login Successful
* Set retry Faliure Threshold and lockout time
    * Given Reset DUT to Default
    * And   Set Lockout Time to 1 min
    * And   Set retry Faliure Threshold 1 times
    * And   logout (restart)
    * When  Login with (user/operator/admin) and incorrect Password 1 time
    * Then  Display login fail
    * When  Input right Password ( time < 30 sec)
    * Then  Display login fail
    * When  Sleep 1 min
    * And   Input right Password
    * Then  Display login Successful
* Login fail 3 times
    * Given Reset DUT to Default
    * When  Login with (user/operator/admin) and Fault Password 3 times
    * Then  Display login fail
    * When  Login with (user/operator/admin) and Right Password
    * Then  Display login Successful
    * When  Login with (user/operator/admin) and Fault Password 2 times
    * Then  Display login fail
    * When  Login with (user/operator/admin) and Right Password
    * Then  Display login Successful
    * When  Login with (user/operator/admin) and Fault Password 5 times
    * Then  Display login fail
    * When  Input right Password
    * Then  Display login fail
    * When  Sleep 5min
    * And   Input right Password
    * Then  Display login Successful
* Alert Password should change after 100 days
    - 原來是設定電腦時間來讓時間過期，改成設定DUT時間，使其成為過期狀態。
    * Given Reset DUT to Default
    * When  Set time to 99 days after
    * And   Login with (user/operator/admin) and Right Password
    * Then  No Alert "Password need change"
    * When  Set time to 101 days after
    * And   Login with (user/operator/admin) and Right Password
    * Then  Alert "Password need change"
* Set Password Aging Time
    * Given Reset DUT to Default
    * Set Password Aging Time to 1
    * When  Set time to 2 days after
    * And   Login with (user/operator/admin) and Right Password
    * Then  Alert "Password need change"
### ~~RIO_Security_ServiceEnableDisable~~
* Comment
    * all Service is not include "Auto Search"/"IOXpress"/"Web"
    * Service
        * CGI Command Server
        * RESTful API
        * HTTPs
        * SNMP Agent
        * Modbus/TCP Slave
        * AOPC
        * Peer-to-Peer
* Default Serive
    * Given Reset DUT to Default
    * And   Log With Admin
    * And   Go to Page  /security/ServiceSettings
    * When  Connect to All Service
    * Then  all Service should be disable
    * And   all Service is disable
* Disable All Service
    * Given Reset DUT to Default
    * And   Log With Admin
    * And   Go to Page  /security/ServiceSettings
    * And   Disable All Service
    * When  Connect to All Service
    * Then  all Service should be disable
    * And   all Service is disable
* Enable All Service
    * Given Reset DUT to Default
    * And   Log With Admin
    * And   Go to Page  /security/ServiceSettings
    * When  Connect to All Service
    * Then  all Service should be Enable
    * And   all Service is Enable
* Press Real Reset Button
    * Given Press Real Reset Button
    * And   Log With Admin
    * And   Go to Page  /security/ServiceSettings
    * When  Connect to All Service
    * Then  all Service should be disable
    * And   all Service is disable
### ~~RIO_Security_AccessControl~~
- 設定不同的IP區段，來檢驗其AccessControl Rule

---






## Control and View (DI Counter DO Pulse)
### Common DI and DIO
#### Name data validation
    * Given	Reset DUT to Default.
    * And 	Go to Page ioSetting
    * And 	Set All mode to DO
    * When	single Name = ""
    * Then	display Fail (limit "")
    * When	single Name = "."
    * Then	display Fail (limit ".")
    * When	single = "TEST123456789123456789123456789"
    * And 	check  = "TEST123456789123456789123456789"
    * Then	display Fail (exceed 30 word)
    * When	no.1 and no.2 = "PU00"
    * Then	display Fail (duplicate name)
    * When	no.X name = "name-0000" "name-0001" ... "name-0016"
    * Then	display OK
    * When 	restart
    * And	Go to Page Dashboard
    * Then 	check all channel name is same
### DI
#### filter data validation
        * Given	Reset DUT to Default.
        * And 	Go to Page ioSetting
        * And 	Set All mode to DI
        * When 	Set ALL filter to 0
        * Then	display Fail
        * When 	Set ALL filter to 4095*channel(4095-65520)
        * Then	display Fail
        * When 	Set ALL filter to 10 20 30 ... 160
        * Then	display OK
        * When 	restart
        * And	Go to Page Dashboard
        * Then 	check name is same
### Counter
#### filter data validation
    * Given	Reset DUT to Default.
    * And 	Go to Page ioSetting
    * And 	Set All mode to Counter
    * When 	Set ALL filter to 0
    * Then	display Fail
    * When 	Set ALL filter to 65536
    * Then	display Fail
#### PowerOnValue data validation
    * Given	Reset DUT to Default.
    * And 	Go to Page ioSetting
    * And 	Set All mode to Counter
    * When 	Set ALL PowerOnValue to -1
    * Then	display Fail
    * When 	Set ALL PowerOnValue to 4294967295+1
    * Then	display Fail
#### Counter Config and Control
    * Given	Reset DUT to Default.
    * And 	Go to Page ioSetting
    * When 	Set ALL filter to 4095*channel(4095-65520)
    * And 	Set ALL Direction (even:up odd:down)
    * And 	Set ALL PowerOnValue to 1~4000000000
    * And 	Set ALL Power off Storage (even:enable odd:disable)
    * And 	Set ALL Trigger (rising falling both)
    * And 	Set ALL Power on Status (even:start odd:stop)
    * When 	restart
    * And	Go to Page Dashboard
    * Then 	check All should be same
    * When 	press counter start/stop
    * Then 	ui start/stop change
#### TE Testing (按照之前的testcase)
    * SI_RIO_IO_DI_Counter_Trigger
    * SI_RIO_IO_DI_Counter_Filter
    * SI_RIO_IO_DI_Counter_Initial
    * SI_RIO_IO_DI_Counter_Overflow
    * SI_RIO_IO_DI_Counter_SaveStatus
### DO
#### Delay data validation
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* And 	Set All mode to DO
* When 	Set ALL PowerOnValue to -1
* Then	display Fail
* When 	Set ALL PowerOnValue to 65535+1
* Then	display Fail
#### DO Config and Control
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* When 	Set ALL PowerOn (even:enable odd:disable)
* And 	Set ALL Delay to 1~65535-1
* And 	Set ALL SafeMode (On Off Hold-last)
* When 	restart
* And	Go to Page Dashboard
* Then 	check All should be same
* When 	press do on/off
* Then 	ui start/stop change
#### TE Testing (按照之前的testcase)
* SI_RIO_IO_DO_DO_Value
* SI_RIO_IO_DO_DO_PowerON
* SI_RIO_IO_DO_DO_SafeStatus
### Pulse
#### ON Width data validation
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* And 	Set All mode to Pulse
* When 	Set ALL Width to 0
* Then	display Fail
* When 	Set ALL Width to 1
* Then	display Successful
* When 	Set ALL Width to 65535+1
* Then	display Fail
* When 	Set ALL Width to 1
* Then	display Successful
#### OFF Width data validation
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* And 	Set All mode to Pulse
* When 	Set ALL Width to 0
* Then	display Fail
* When 	Set ALL Width to 1
* Then	display Successful
* When 	Set ALL Width to 65535+1
* Then	display Fail
* When 	Set ALL Width to 1
* Then	display Successful
#### Count data validation
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* And 	Set All mode to Pulse
* When 	Set ALL Count to -1
* Then	display Fail
* When 	Set ALL Width to 0
* Then	display Successful
* When 	Set ALL Count to 65535+1
* Then	display Fail
* When 	Set ALL Width to 0
* Then	display Successful
#### Delay data validation
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* And 	Set All mode to Pulse
* When 	Set ALL Count to -1
* Then	display Fail
* When 	Set ALL Width to 0
* Then	display Successful
* When 	Set ALL Count to 65535+1
* Then	display Fail
* When 	Set ALL Width to 0
* Then	display Successful
#### Pulse Config and Control
* Given	Reset DUT to Default.
* And 	Go to Page ioSetting
* When 	Set ON Width to 10*Channel
* And 	Set OFF Width to 10*Channel
* And 	Set Count to 10*Channel
* And 	Set Delay to 10*Channel (Need test)
* And 	Set Status to (even:enable odd:disable)
* And 	Set Safe to (even:enable odd:disable)
* And 	restart
* And	Go to Page Dashboard
* Then 	check All should be same
* When 	press Start/Stop
* Then 	ui start/stop change
#### TE Testing (按照之前的testcase)
* SI_RIO_IO_DO_Pulse_Width
* SI_RIO_IO_DO_Pulse_Count
* SI_RIO_IO_DO_Pulse_PowerON
* SI_RIO_IO_DO_Pulse_PowerONDelay
* SI_RIO_IO_DO_Pulse_SafeStatus

