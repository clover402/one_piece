## Chap8 Collections
### 8.2 Iterator
集合删除元素时一定要**使用迭代器的remove方法**，否则会抛异常

### 8.3 Set
集合，元素不可重复，通过元素的equals方法来判断，所以equals方法一定要写好  
如果元素是可变对象则可能会在元素改变后导致异常
#### HashSet LinkedHashSet 无序
#### TreeSet 实现了SortedSet接口带排序功能
#### EnumSet 元素都是枚举

### 8.4 List
有序集合
#### ListIterator 
增加了向前迭代 和 添加元素的方法  
#### ArrayList 
相当于数组的加强版,如果需要添加大量元素可以设置initalCapacity来提高性能，默认长度10。非线程安全
#### Vector 
线程安全，老版的List，性能要比ArrayList低
##### Stack 
栈，模拟栈的数据结构，后进先出，性能不好
#### LinkedList 
基于链表的List。插入删除速度快,随机访问性能差，采用迭代器来遍历元素更好
#### Arrays.asList 
固定长度List

### 8.5 Queue
模拟队列结构，先进先出
#### PriorityQueue 
按元素大小排序，不允许传入null，可以自然排序或定制排序
#### Deque
子接口，双端队列
##### ArrayDeque
基于数组的实现类，可以当做栈来使用，性能比Stack好
##### LinkedList
Deque的另外一个实现类，可以作为双端队列或者栈来使用

### 8.6 Map
类似于php中的关联数组，python的字典  
Set的实现就是基于value全为null的Map
#### HashMap
不能保证顺序。如果添加自定义类作为key，重写equals和hashCode是要保证两个方法判断标准一致
#### LinkedHashMap 
双向链表，维护元素插入顺序
#### Hashtable 
古老的数据结构，新版本不建议使用，线程安全，不运行null作为key或者value
##### Properties Hashtable的子类，可以读取属性配置文件到Map对象
#### TreeMap 
实现了SortedMap接口，根据key对节点进行排序，有自然排序和定制排序
#### WeakHashMap
key只保留对象的弱引用，如果key所引用的对象没有被其他强引用对象引用则可能会被垃圾回收，这些key对应的节点也可能会被自动删除
#### IdentifyHashMap
两个key严格相等时（==）才认为两个key相等
#### EnumMap
key必须是单个枚举类的枚举值，根据枚举值定义的顺序排列，不允许null作为key，创建时要指定枚举类


### 8.7 HashSet与HashMap性能说明
#### 术语
* bucket: 桶，hash表里存储元素的位置
* cpacity：容量，hash表中桶的数量
* initial capacity：初始化容量
* size：尺寸，hash表中记录的数量
* load factor：负载因子（size/capacity）
* 负载极限：最大填满程度，达到时成倍增加容量，并重新分配（rehashing），默认值0.75

### 8.8 工具类Collections
* reserve 反转
* shuffle 洗牌
* sort 排序
* swap 交换两个元素的位置
* rotate 翻转 将后x个元素移到前面或者前x个元素移到后面
* binarySearch 查找
* max/min 最大最小
* fill 填充
* frequency 返回指定元素出现次数
* indexOfSubList/lastIndexOfSubList 返回子列表在父列表中出现的位置索引
* replaceAll 替换
* emptyXxx()/singetonXxx()/unmodifiableXxx() 空集合/单元素集合/不可变集合

### 8.9 Enumeration接口
Iterator迭代器的古老版本  
* hasMoreElements
* nextElements  
新集合再不支持此接口  

## Chap9 泛型
泛型是为了集合而生  
如果要继续一个包含泛型的父类，需要指明形参的具体类型  
泛型不管实际类型参数是什么，运行时总是有同样的class  
静态方法、静态变量、静态初始化块不允许使用类型参数  ？？？
  
泛型与数组有所不同：Integer[] 是 Number[]的子类，List<Integer> 并不是List<Number>的子类  
通配符:  
* ? 表示任意类型
* ? extends ClassA 表示都是ClassA及其子类
* ? super ClassA 表示都是ClassA及其父类  
非泛型转泛型则类型信息会丢失，泛型转非泛型可以编译通过但是会发出“未经检查的转换”警告  
  

## Chap10 异常处理
### Error
一般为虚拟机相关问题，如系统崩溃、虚拟机错误、动态链接失败等  
程序无需处理
### Exception
* getMessage 异常描述
* printStackTrace 将异常的跟踪栈输出
* getStackTrace 返回异常的跟踪栈信息  
finally主要进行资源的回收
#### Checked异常
编译时的错误，必须解决了才能执行  
要么显示抛出异常，要么捕获并处理
#### RuntimeException
运行时异常  
把原始异常信息隐藏，仅向上提供必要的异常提示信息的处理方式，可以保证底层异常不会扩散到表现层，可以避免向上暴露太多实现细节，
这完全符合对象封装的原则，这种方式叫责任链模式（也叫异常链）  
不要用异常处理来代替正常的业务逻辑判断，它的效率很低  
try语句块不要过于庞大
不要使用空catch  

## Chap14 Annotation(注解)
### 14.1 常用注解
#### Override 方法重写使用，可以检查重写的方法定义是否正确
#### Deprecated 一般用于被弃用的方法或类
#### SuppressWarnings 去掉编译器警告，可以通过参数去掉各种类型的警告
#### SafeVarargs 专门为抑制“堆污染”（讲不带类型的泛型赋值给带类型的）警告提供

### 14.2 JDK的元Annotation
修饰其他Annotantion定义用的
#### Retention
指定被修饰的注解可以保留多长时间
* RetentionPolicy.SOURCE 只在源代码时有效
* RetentionPolicy.CLASS 在类文件时有效
* RetentionPolicy.RUNTIME 运行时都有效

#### Target
指定被修饰的注解可以用于修饰哪些程序单元
* ElementType.ANNOTATION_TYPE 只能修饰注解
* ElementType.CONSTRUCTOR 只能修饰构造器
* ElementType.FIELD 只能修饰成员变量
* ElementType.LOCAL_VARIABLE 只能修饰局部变量
* ElementType.MEHTOD 只能修饰方法定义
* ElementType.PACKAGE 只能修饰包定义
* ElementType.PARAMETER 可以修饰参数
* ElementType.TYPE 可以修饰类、接口或枚举

#### Documented
指定被其修饰的注解类将被javadoc工具提取成文档

#### Inherited
被它修饰的注解A将有继承性，父类使用了注解A，则子类将自动被注解A修饰

### 14.3 自定义Annotation
#### 定义注解
语法如下
```java
//注解都是通过@interface来定义，使用时用@YourAnnotation即可
public @interface YourAnnotation{
    //成员变量需要用方法的形式来定义，并设置默认值。如果没有设置默认值在使用时就必须要给属性设定值
    String name() default "yeeku";
    int age() default 32;
}
```
#### 读取注解
注解通常无法直接生效，通常要读取后写实现逻辑，读取注解主要使用反射中如下三个方法
* getAnnotation(Class<T> annotationClass) 获取指定注解
* Annotation[] getAnnotations() 获取元素上所有的注解
* boolean isAnnotationPresent(Class<? extends Annotation> annotationClass) 判断元素是否存在指定类型的注解

### 14.4 编译时处理Annotation
主要是实现生成额外的源代码和其他文件，需要APT（Annotation Processing Tool）来处理。


## Chap15 输入/输出
### 15.1 File类 操作文件和目录
### 15.2 JAVA的IO流
JAVA把不同的输入/输出源（键盘、文件、网络等）抽象为流（stream），stream是从起源（source）到接受（sink）的有序数据  
#### 流的分类
* 输入流 & 输出流
* 字符流（16位） & 字节流(8位)
* 节点流（低级流） & 处理流（高级流）

### 15.3 字节流&字符流
Reader Writer/InputStream OutputStream  
处理的单位不一样，一个是字节位单位，一个是字符（4个16进制数）为单位

### 15.4 输入/输出流体系
#### rule: 文本使用字符流，二进制文件使用字节流 
#### 转换流：InputStreamReader OutStreamWriter  字节流->字符流
#### 管道流：PipedInputStream PipedOutputStream PipedReader PipedWriter
#### 缓冲区：BufferedReader BufferedWriter
#### 推回输入流： PushbackInputStream PushbackReader 将数据推回到缓冲区

### 15.5 重定向标准输入/输出
System.in, System.out标准输入/输出，默认是键盘和显示器，可以通过System的setErr，setIn，setOut方法来设置

### 15.6 读取其他进程数据
主要使用Process类的3个方法获取子进程的错误流、输入流、输出流

### 15.7 RandomAccessFile
可自由读写文件，可以向已存在的文件追加内容。无法向文件的指定位置插入内容，会覆盖原来的内容

### 15.8 对象序列化
目的：存储java对象，或通过网络传输java对象  
操作：将对象转换成字节序列  
需要实现Serializable 或 Externalizable接口  
写入：ObjectOutputStream对象的writeObject方法  
读取：ObjectInputStream对象的readObject方法  
反序列化需要提供对象所属的类，而且反序列化不需要调用构造函数。如果存在引用类则引用类要可序列化，如果有父类，而且要用父类的属性则父类也要支持序列化  
同一个对象序列化时只有第一次会写入对象数据，后面只会存其id  
如果希望某字段不参与序列化，可以通过transient关键字实现（瞬态）  
自定义序列化可通过writeObject, readObject, readObjectNoData方法来实现  
writeReplace方法可以在序列化对象时将该对象替换成其他对象  
readResolve该方法的返回值会替换原来反序列化的对象，主要用于单例类、枚举类  
版本：定义一个类的序列化版本 private static final Long serialVersionUID=xxxL，只要该值一样就可以进行序列化反序列化。  
如果修改了非静态非瞬台Field，则需要更新上面的ID，否则不用更新。新版本类新增Field也可以兼容。

### 15.9 NIO
#### Channel 通道
对传统输入输出系统的模拟，提供map方法，可以直接将一块数据映射到内存
必须通过Buffer来操作
建议都通过传统节点（InputStream/OutputStream）的getChannel方法来返回对应的Channel
* map方法: 返回对应的Buffer
* read方法
* write方法
##### DatagramChannel/SocketChannel/ServerSocketChannel UPD/TCP网络通信
##### Pipe.SinkChannel/Pipe.SourceChannel 线程之间通信
##### FileChannel 

#### Buffer 容器
本质是一个数组，要通过Buffer来操作Channel对象
* capacity 容量：最大容量
* limit 界限：第一个不能被读写的缓冲区位置索引
* position 位置：下一个可以被读写的缓冲区位置索引  
* flip方法：装入数据后调用，为取出数据做准备
* clear方法：输出数据结束后调用，为装入数据做准备
* get/put方法：放入取出数据，注意有个相对和绝对的概念，相对会从position开始会改变position的值，绝对从头开始不影响position
##### ByteBuffer 通过ByteBuffer.allocate(capacity)创建
##### MappedByteBuffer（通过Channel.map()创建）
##### CharBuffer 通过CharBuffer.allocate(capacity)创建

#### 字符集和编码
* Unicode：Java默认字符集
* GBK 简体中文
* BIG5 繁体中文
* ISO-8859-1 ISO拉丁字母表,也称ISO-LATIN-1
* UTF-8
Charset.availableCharsets()获取JDK支持的所有字符集  
Charset.forName("UTF-8")获取字符集对象，该对象有编码器和解码器，可以将ByteBuffer和CharBuffer进行互相转换  
StandarCharsets工具类包含常用字符集对象

#### 文件锁
FileLock支持文件锁定
FileChannel中的lock（阻塞）/trylock（非阻塞）方法可以获得文件锁FileLock对象，这两个方法还可以只锁定部分内容，以及设置是否为共享锁

### 15.10 NIO.2


