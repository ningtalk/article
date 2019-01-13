# MySQL
## MySQL逻辑架构
![MySQL逻辑架构图](https://github.com/npvip/article/blob/master/file/image/mysql%E9%80%BB%E8%BE%91%E6%9E%B6%E6%9E%84%E5%9B%BE.png)  

分为Server层和存储引擎层两部分：  
1. Server层：包括连接器、查询缓存、分析器、优化器、执行器等，涵盖MySQL的大多数核心服务功能以及所有的内置函数，所有跨存储引擎的功能都在这一层实现，如存储过程，
触发器，视图等。  
2. 存储引擎层：复制数据的存储和提取，架构模式是插件式的，支持InnoDB，MyISAM,Memory等多种，InnoDB是MySQL5.5.5版本开始之后的默认存储引擎，是最流行的存储引擎。  

### 优化器
优化器的作用
* 表里有多个索引的时候，决定使用哪个索引 
* 一个语句有多个join的时候，决定各个表的连接顺序