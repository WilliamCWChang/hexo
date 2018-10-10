# Robot Framework User Guide
# 1   Getting started

## 1.1   Introduction
Robot Framework 
- 基於 Python-based
- 可擴充的keyword (extensible keyword-driven test automation framework)

支援如下測試方式
- end-to-end acceptance testing
- acceptance-test-driven development (ATDD)

It can be used for testing distributed, heterogeneous applications, where verification requires touching several technologies and interfaces.

The framework has a rich ecosystem around it 

consisting of various generic test libraries and tools that are developed as separate projects. For more information about Robot Framework and the ecosystem, see http://robotframework.org.

- open source software released under the Apache License 2.0. 
- 由Robot Framework Foundation所贊助

### 1.1.1   Why Robot Framework?
- Enables easy-to-use tabular syntax for creating - test cases in a uniform way.
- Provides ability to create reusable higher-level - keywords from the existing keywords.
- Provides easy-to-read result reports and logs in - HTML format.
- Is platform and application independent.
- Provides a simple library API for creating - customized test libraries which can be - implemented natively with either Python or Java.
- Provides a command line interface and XML based - output files for integration into existing build - infrastructure (continuous integration systems).
- Provides support for Selenium for web testing, - Java GUI testing, running processes, Telnet, SSH,-  and so on.
- Supports creating data-driven test cases.
- Has built-in support for variables, practical - particularly for testing in different - environments.
- Provides tagging to categorize and select test - cases to be executed.
- Enables easy integration with source control: - test suites are just files and directories that - can be versioned with the production code.
- Provides test-case and test-suite -level setup - and teardown.
- The modular architecture supports creating tests - even for applications with several diverse - interfaces.


### 1.1.2   High-level architecture

Robot Framework is a generic, application and technology independent framework. It has a highly modular architecture illustrated in the diagram below.

![Robot Framework architecture](http://robotframework.org/robotframework/latest/images/architecture.png "Robot Framework architecture")


The test data is in simple, easy-to-edit tabular format. 

When Robot Framework is started, it processes the test data, executes test cases and generates logs and reports. The core framework does not know anything about the target under test, and the interaction with it is handled by test libraries. Libraries can either use application interfaces directly or use lower level test tools as drivers.


### 1.1.3   Screenshots
請直接參考RFW網站

### 1.1.4   Getting more information
#### Project pages

The number one place to find more information about Robot Framework and the rich ecosystem around it is http://robotframework.org. Robot Framework itself is hosted on GitHub.

#### Mailing lists

There are several Robot Framework mailing lists - where to ask and search for more information. - The mailing list archives are open for everyone - (including the search engines) and everyone can - also join these lists freely. Only list members - can send mails, though, and to prevent spam new - users are moderated which means that it might - take a little time before your first message - goes through. Do not be afraid to send question - to mailing lists but remember How To Ask - Questions The Smart Way.

- robotframework-users : General discussion about all Robot Framework - related issues. Questions and problems can be - sent to this list. Used also for information - sharing for all users.
- robotframework-announce : An announcements-only mailing list where only - moderators can send messages. All announcements - are sent also to the robotframework-users - mailing list so there is no need to join both - lists.
- robotframework-devel : Discussion about Robot Framework development.

## 1.2   Copyright and license
 
Robot Framework is open source software provided under the Apache License 2.0. Robot Framework documentation such as this User Guide  use the Creative Commons Attribution 3.0  Unported license. Most libraries and tools in the larger ecosystem around the framework are    also open source, but they may use different    licenses.

The full Robot Framework copyright notice is included below:

```java
Copyright 2008-2015 Nokia Networks
int cool;
cool = 0;

Copyright 2016-     Robot Framework Foundation

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```


## 1.3   Installation instruction
 
 
## 1.4   Demonstrations
