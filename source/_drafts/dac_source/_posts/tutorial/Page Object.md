---
title: Page Object
date: 2018-07-31 18:30:00
tags:
---

Page Object


# 宗旨
Within your web app’s UI there are areas that your tests interact with. 
A Page Object simply models these as objects within the test code. 
This reduces the amount of duplicated code and means that if the UI changes, the fix need only be applied in one place.


---

# POM:Page Object Model
 

page class包含web的元素和操作元素的方法

page class中的方法命名，最好根據其對應測試流程命名 
登入後等待幾秒: waitingForLoginSuccess



當你在為web頁面編寫測試時，你需要操作該web頁面上的元素來點擊鏈接或驗證顯示的內容。然而，如果你在測試代碼中直接操作html元素,那麼你的代碼是及其脆弱的，因為UI會經常變動。一個page對象可以封裝一個html頁面或部分頁面，你可以通過提供的應用程序特定的API來操作頁面元素，而不需要在HTML中四處搜尋。 [name=黃博文]

一个有意见分歧的地方是page对象是否应自身包含断言，或者仅仅提供数据给测试脚本来设置断言。在page对象中包含断言的倡导者认为，这有助于避免在测试脚本中出现重复的断言，可以更容易的提供更好的错误信息，并且提供更接近只做不问风格的API。不在page对象中包含断言的倡导者则认为,包含断言会混合访问页面数据和实现断言逻辑的职责，并且导致page对象过于臃肿。 [name=黃博文]

# Reference
[科科和測試-自動化測試的 Design Pattern：Page Objects](https://goo.gl/pQBr2Y

[PageObject-Martin Fowler](https://goo.gl/dIvhaJ)

[黄博文的地盘-翻译-page对象-Martin Fowler的翻譯文件](https://goo.gl/5w4E2y)


[SeleniumHQ/selenium](https://goo.gl/DYo66k)


[Pete's Dev Life](https://goo.gl/TVwuaP)這個很棒，我看了之後比較懂要怎麼做了。


# Reference
https://github.com/SeleniumHQ/selenium/wiki/PageObjects