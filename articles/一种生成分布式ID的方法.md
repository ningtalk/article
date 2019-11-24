

## 基础知识
### 左移`<<`
1. 使用格式为`value << num`，表示value向左移位num位，规则是：丢弃最高位，最低位补0，如果移动为位数超过该类型的最大位数，编译器会对移位的位数进行取模。    
   例如 `5 << 2`表示将5向左移2位.  
2. 运算规则
* 按二进制形式把所有的数字向左移动对应的位数，高位移出(舍弃)，低位的空位补零。
* 当左移的运算数是int 类型时，每移动1位它的第31位就要被移出并且丢弃；
* 当左移的运算数是long 类型时，每移动1位它的第63位就要被移出并且丢弃。
* 当左移的运算数是byte 和short类型时，将自动把这些类型扩大为 int 型。
3. 数学意义
在数字没有溢出的前提下，对于正数和负数，左移一位都相当于乘以2的1次方，左移n位就相当于乘以2的n次方。  

### 按位与`&`
如果相对应位都是1，则结果为1，否则为0。  

### 按位或`|` 
如果相对应位都是0，则结果为0，否则为1。  

## snowflake算法
snowflake是Twitter开源的分布式ID生成算法，结果是一个long型的ID。其核心思想是：使用41bit作为毫秒数，10bit作为机器的ID（5个bit是数据中心，5个bit的机器ID），12bit作为毫秒内的流水号（意味着每个节点在每毫秒可以产生 4096 个 ID），最后还有一个符号位，永远是0。  

### 实现
[Java实现](https://github.com/npvip/StudyNote/blob/master/src/main/java/cn/np/snow/SnowflakeIdWorker.java)




## 参考
* Leaf——美团点评分布式ID生成系统:https://tech.meituan.com/MT_Leaf.html
* 分布式唯一id：snowflake算法思考:https://juejin.im/post/5a7f9176f265da4e721c73a8
* 百度uid-generator:https://github.com/baidu/uid-generator/blob/master/README.zh_cn.md