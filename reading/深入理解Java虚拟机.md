## 1 Java虚拟机
### 1.1运行时数据区域
![运行时数据区域](http://m.qpic.cn/psb?/V14Yvw6F0uSJqd/cj1iDWYAfGy3*QDjiH1UObSR4fDrVGr.g8BmIjRNPoI!/b/dEEBAAAAAAAA&bo=cQJtAQAAAAADBz0!&rf=viewer_4)
#### 1.1.1程序计数器
一块较小的内存空间，可以看做当前线程所执行的字节码的行号指示器。每个线程都有一个独立的程序计数器。如果执行的是Native方法则计数器的值为空。
#### 1.1.2Java虚拟机栈
它的生命周期与线程相同  
每个方法被执行的时候都会同时创建一个栈帧（Stack Frame）用于存储相关数据，包括：
1. 局部变量表：基本数据类型、对象引用和returnAddress(指向一条字节码指令地址)。所需内存空间在编译期间完成分配，运行时不可变
2. 操作栈
3. 动态链接
4. 方法出口
#### 1.1.3本地方法栈
与虚拟机栈类似，只是它是为Native方法服务
#### 1.1.4Java堆（heap）
被所有线程共享的一块内存，在虚拟机启动是创建。用于存放对象实例。  
它也是垃圾收集器管理的主要区域。
#### 1.1.5方法区（Non heap）
存储类信息、常量、静态变量、即时编译器编译后的代码。  
如果使用分代算法，永久代就是方法区。  
此区域较少进行垃圾回收，主要针对常量池的回收和对类型的卸载。  
运行时常量池:存储预置常量及运行期间的产生的新常量

### 1.2对象访问
#### 1.2.1句柄访问
![句柄访问](http://m.qpic.cn/psb?/V14Yvw6F0uSJqd/fqFS9yn2Ct.SnbnTjBFdH0EMSeqk.z615kcxk*CPM4A!/b/dD4BAAAAAAAA&bo=qQOnAQAAAAADBy4!&rf=viewer_4)
#### 1.2.2直接访问
Sun HotSpot采用这种方式
![直接访问](http://m.qpic.cn/psb?/V14Yvw6F0uSJqd/CFLtCu**aNy1U3uR5Jrl2qK3DYGRVvLW5k*zAQ35Xd8!/b/dFEBAAAAAAAA&bo=sQOlAQAAAAADFyQ!&rf=viewer_4)
