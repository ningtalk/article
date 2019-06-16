# MySQL
本文主要记录学习MySQL的相关知识点，来源包括《MySQL技术内幕：InnoDB存储引擎》、技术博客等。  

## 体系结构
![MySQL体系结构-摘自MySQL官方手册](https://github.com/npvip/article/blob/master/file/image/MySQL%E4%BD%93%E7%B3%BB%E7%BB%93%E6%9E%84.png)
从图中可见，MySQL Server结构从上自下主要有：  
* 连接层
  - Connection Pool
* 管理服务和工具组件
  - Management Service & Utillties
* 服务层
  - SQL interface...：SQL 接口...
  - Parser...:解析器等
  - Optimizer..:优化器等
  - Caches & Buffers:缓存
* 引擎层
* 存储层  

### 连接层
与客户端的连接服务，包含本地socket通信，完成连接处理、权限认证、及安全方案，在该层进入了线程池的概念。
### 服务层
完成核心服务功能，包括连接器、查询缓存、分析器、优化器、执行器等。SQL接口、查询缓存、SQL的分析和优化以及部分内置函数的执行。  
所有跨存储引擎的功能都在这一层实现，如存储过程，触发器，视图等。  
### 引擎层
存储引擎负责MySQL的数据的存储和提取，服务层通过API与存储引擎进行通信，不同存储引擎具有不同的功能特性。
架构模式是插件式的，支持InnoDB，MyISAM,Memory等多种，`InnoDB`是MySQL5.5.5版本开始之后的默认存储引擎，是最流行的存储引擎。 
### 存储层
数据存储层，将数据存储在运行于设备的文件系统上，并完成与存储引擎的交互。

## 存储引擎
MySQL区别于其他数据库的一个最重要的特性是存储引擎。每个存储引擎都有各自的特点，可以根据具体的应用场景来选择合适的存储引擎。  
常见的存储引擎：
* InnoDB:最常用
* MyISAM
* NDB
* Memory  
...

### InnoDB
InnoDB是事物安全的MySQL存储引擎，是第一个完整支持ACID事物的存储引擎，从MySQL5.5开始是默认的表存储引擎。  
特点：  
* 行锁设计
* 支持MVCC
* 支持外键
* 提供一致性非锁定读
* 有效的利用内存和CPU

#### InnoDB体系结构
* 后台线程
* 内存

