# MySQL中的`key` vs `index`

## 问题
 mysql建表时(如下)，关键字`key`的作用是什么?
```
DROP TABLE IF EXISTS `phpcolor_ad`
CREATE TABLE `phpcolor_ad` (
`id` mediumint(8) NOT NULL AUTO_INCREMENT,
`name` varchar(30) NOT NULL,
`type` mediumint(1) NOT NULL,
`code` text,
PRIMARY KEY (`id`),
KEY `type` (`type`)
);
```

## KEY
`KEY`是数据库的物理结构，具有两层含义：  
* 约束：偏重于约束和规范数据库的结构完整性
* 索引：辅助查询

KEY包括PRIMARY KEY,UNIQUE KEY,FOREIGN KEY
* `PRIMARY KEY`：有两个作用，一个是约束作用，用来规范一个存储主键和唯一性，但同时也在此`key`上建立了一个`index`
* `UNIQUE KEY`：有两个作用，一个是约束作用，用来规范数据的唯一性，但同时也在此`key`上建立了一个`index`
* `FOREIGN KEY`：有两个作用，一个是约束作用，用来规范数据的引用完整性，但同时也在此`key`上建立了一个`index`



## 参考
* http://einverne.github.io/post/2017/07/mysql-key-vs-primary-key-vs-unique-key-vs-index.html#%E6%93%8D%E4%BD%9C%E7%B4%A2%E5%BC%95
* https://yq.aliyun.com/ask/4614
* https://blog.csdn.net/nanaMasuda/article/details/52543177
