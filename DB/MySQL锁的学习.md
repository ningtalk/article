mysql锁  
## 分类
根据加锁范围，MySQL锁可以分为全局锁、表级锁、行级锁。  
## 全局锁
对整个数据库加锁。  
使用场景：做全库逻辑备份时，为保证备份期间的库在同一逻辑时间点，即一致性视图。  
使用方式：  
* flush tables with read lock,使数据库处于只读状态
* mysqldump官方自带逻辑备份工具，参数 -single-transaction 会在导数据之前启动一个事务，确保拿到一致性视图。使用mysqldump的前提条件是存储引擎支持隔离级别（MyISAM不支持）
* set global readonly = true 也可以做到全库只读，但不建议使用，在客户端出现异常的情况下会保持readonly,会导致长时间处于不可写的状态，风险较高
## 表级锁
MySQL有两种表级锁：
* 表锁
* 元数据锁，MDL
## 行级锁