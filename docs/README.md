![logo](https://user-images.githubusercontent.com/16918550/124081276-e99bc880-da7d-11eb-91ea-a7030338e5b1.png){:align="right" width="256px" height="176px"}
# 毕方智能云沙箱
毕方智能云沙箱(***Bold-Falcon***)是一个开源的自动化恶意软件分析系统。它用于自动运行和分析文件，并收集全面的分析结果，概述恶意软件在独立操作系统中运行时所做的工作。我们的工作是二次开发开源cuckoo沙箱，包括**更新项目结构**，**重写整个前端的用户交互**和**添加基于机器学习的检测模块**，使恶意软件分析系统可以**思考**。

#### 开源资料
+ [cuckoo](https://github.com/cuckoosandbox/cuckoo) Cuckoo Sandbox is an automated dynamic malware analysis system
+ [cuckoo-modified](https://github.com/spender-sandbox/cuckoo-modified) Modified edition of cuckoo
+ [cuckooDroid](https://github.com/idanr1986/cuckoo-droid) CuckooDroid - Automated Android Malware Analysis with Cuckoo Sandbox.
+ [docker-cuckoo](https://github.com/blacktop/docker-cuckoo) Cuckoo Sandbox Dockerfile
+ [cuckooautoinstall](https://github.com/buguroo/cuckooautoinstall) Auto Installer Script for Cuckoo Sandbox
+ [cuckooML](https://github.com/honeynet/cuckooml) CuckooML: Machine Learning for Cuckoo Sandbox
+ [Panda-Sandbox](https://github.com/PowerLZY/Panda-Sandbox) Cuckoo python3 (Unfinished)
+ [HaboMalHunter](https://github.com/Tencent/HaboMalHunter#readme_cn) HaboMalHunter is a sub-project of Habo Malware Analysis System

#### 源码分析
+ [cuckoo技术分析全景图](https://cloud.tencent.com/developer/article/1597020)
+ [cuckoo沙箱源码分析上](https://bbs.pediy.com/thread-260038.htm)
+ [cuckoo沙箱源码分析中](https://bbs.pediy.com/thread-260087.htm)
+ [cuckoo沙箱源码分析后](https://bbs.pediy.com/thread-260252.htm)
+ [腾讯哈勃Linux沙箱源码分析上](https://zhuanlan.zhihu.com/p/54756592)
+ [腾讯哈勃Linux沙箱源码分析下](https://zhuanlan.zhihu.com/p/54756845)

#### 项目结构更新
  - [x] 整理工程目录打包lib：（common，core），Modules（辅助功能、虚拟机、处理、签名、机器学习模型检测）
  - [x] 省略\CWD目录：添加 analyzer、db、examples、Mal_sample、sample_data、storage、log等目录

#### 主要更新内容

+ 学习内容
  - [x] Yara规则、ssdeep
  - [x] DLL注入、动态信息提取原理
  - [x] 历届网络技术挑战赛调研
  - [x] [用Github Page快速创建项目文档网站](https://zhuanlan.zhihu.com/p/323457078)
  - [ ] [动态牌子](https://img.shields.io)
  - [ ] 创建Bold-Falcon logo in logo.py
  - [ ] pypi上传模块，pip安装
  - [x] requirements.txt 整理
  - [ ] Frog:create an image and add an image and a host to the Fog server
  - [ ] 解析plugins.py, class RunSignatures()原理
  - [ ] 解析analyzer/windows/analyzer.py 虚拟机运行脚本
  - [ ] [malware-detection](https://github.com/dchad/malware-detection)

+ 设计文档
  + [x] 参考文献记录（设计依据）
  + [x] 国内沙箱深度调研
  + [x] 图标+起名

+ 家族签名模块
  - [x] [cuckoo 社区签名库](https://github.com/cuckoosandbox/community)
  - [x] [cuckoo的行为签名](https://www.secpulse.com/archives/75180.html)
  - [ ] 添加挖矿+使用自定义签名

+ 机器学习模块
  - [x] 数据集：kaggle microsoft 10000个软件、挖矿软件 6000个；
  - [ ] 报告显示内容：模型检测图展示、使用特征展示、预测威胁得分；
  - [x] 静态检测引擎: ember、string、Op-code、灰度图、malconv；
  - [x] 动态检测引擎：API调用序列；
  - [x] 家族聚类（hdbscan等）；
  - [ ] 定义基类Ml、loader等；
  - [ ] 定义模型命名规则
  - [ ] 添加Smaple——malware，200个json report样本；**gist.github.com**
  - [ ] 沙箱应该设置多久去运行恶意软件？[Does Every Second Count? NDSS 2021](https://www.ndss-symposium.org/ndss-paper/does-every-second-count-time-based-evolution-of-malware-behavior-in-sandboxes/)

+ 后期需求
  + [ ] 环境打包，Docker\shells安装
  + [ ] blog解析文档编写
  + [ ] 虚拟机管理：libvirt+高并发虚拟机
  + [ ] 沙箱内存管理：MemScrimper: Time- and Space-Efficient Storage of *Malware* Sandbox Memory Dumps （2018 DIVMA）
  + [ ] 3.3.5 REST API(Cuckoo docs) wsgi应用程序
  
#### 常见问题
+ Machine * status gurumeditation
  -  找到虚拟机安装目录下VBox.log日志文件
  -  在日志文件中找到ProcessID, ```kill - 9 ProcessID```
+ python 2/3 joblib.dump() 和 joblib.load()
  - 不同python版本的pickle.dump()和pickle.load()是可以相互转换和支持的
  - 在python3中，您应该使用较低的协议号来编写pickle数据 ```pickle.dump(your_object, your_file, protocol=2)```

#### 文档结构

+ 说明
  + 背景介绍
  + 内容设计
  + 功能全景图
+ 安装
  + **准备主机**
  + Preparing the Guest
+ 使用
  + **Starting Cuckoo**
  + **Submit an Analysis**
  + **Web interface**
  + **REST API**
  + **Analysis Packages**
  + **Analysis Results**
  + **Tasks Clean**
+ 开发
  + 开发环境配置
    + Development with the Python Package
    + Developing with Pycharm
  + 辅助功能模块
  + 机器交互模块
  + 文件分析模块
  + 结果处理模块
  + 家族签名模块
  + 机器学习模块
  + 报告生成模块
  + 用户交互模块
+ 扩展

























