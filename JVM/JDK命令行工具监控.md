# 命令行工具的监控
## JVM的参数类型
* 标准参数
* X参数
* XX参数

### 标准参数
在JDK各个版本中比较稳定。  
* -help
* -server -client
* -version -showversion
* -cp -classpath

### X参数
非标准化参数，用的不是很多。    
* -Xint：解释执行
* -Xcomp：第一次使用就编译成本地代码
* -Xmixed：混合模式，JVM自己决定是否编译成本地代码

### XX参数
非标准化参数，在JDK个版本中相对不稳定（有变化），主要用于JVM调优和Debug。  

#### Boolean类型
* 格式：-XX:[+-]<name> 表示启用(+)或禁止(-)<name>属性。  
* 例：
```
// 使用CMS垃圾收集器
-XX:+UseConcMarkSweepGc
// 使用G1垃圾收集器  
-XX:+UseG1GC  
```
### 非Boolean类型
* 格式：-XX:<name>=<value> 表示<name>的属性值是<value>
* 例：  
```
// GC最大暂停时间500毫秒
-XX:MaxGCPauseMillis=500
// 
-XX:GCTimeRatio=19
```

### -Xmx -Xms
* 最常见的两个参数，属于XX参数
 - -Xms等价于-XX:InitialHeapSize
 - -Xmx等价于-XX:MaxHeapSize
 
## 查看JVM运行时参数
* -XX：+PrintFlagsInitial:查看初始值
* -XX:+PrintFlagsFinal：查看最终值
* -XX:+UnlockExperimentalVMOptions：解锁实验参数 

### PrintFlagsInitial
* =表示默认值  
* *=表示被用户或JVM修改后的值



## 查看命令
### jps
查看java进程的命令，类似linux中的ps。  

### jinfo
* 查看最大内存：jinfo -flag MaxHeapSize <pid>
* 查看垃圾回收器：jinfo -flag UseG1GC <pid>;jinfo -flag UseParallelGC <pid>

### jstat
查看JVM统计信息。  
#### 类装载
jstat -class <pid>
jstat -gc <pid> <interval> <times>:间隔interval(毫秒)，总输出times次  


## 导出内存映射文件
导出内存映射文件的方法主要有两种：一种是通过配置JVM运行参数；一种是通过`jmap`命令导出。  
### 配置JVM参数导出
该方式内存溢出时会自动导出：  
`-XX:+HeapDumpOnOutOfMemoryError`  
`-XX:HeapDumpPath=./`  

### jmap
使用jmap命令手动导出：  
`jmap -dump:format=b, file=heap.hprof <pid>`  
jmap命令的其他用法可查看参考里的文档。

### MAT分析内存溢出
工具（待完善）


## 参考
* javase 7 docs:https://docs.oracle.com/javase/7/docs/technotes/tools/share/jps.html