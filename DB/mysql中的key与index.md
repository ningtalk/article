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
