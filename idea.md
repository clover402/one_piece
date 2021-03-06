## 破解补丁
1. 目前来看2017.3.5的版本可以被破解
2. 下载crack.jar包放到对于idea的bin目录
3. 修改idea.exe.vmoptions或idea64.exe.vmoptions(按自己的需要来）,增加一行-javaagent:path-to-crack.jar(不用加引号)
4. 运行idea.exe或者idea64.exe.选择激活码（Activation Code），输入上面增加的那一行

## **推荐插件**
* Alibaba Java Coding Guidelines 阿里巴巴JAVA编码规约
* IDE Features Trainer 帮助使用者更好的熟悉和掌握IDE

## **GIT插件开启**
File -> Settings -> Version Control -> Git
Make sure SSH executable is set to “Native.” (If already so, switch to “Built-in,” apply it, then switch back to “Native.”)

## **GIT插件快捷键**
Ctrl + `    弹窗git的快捷操作框
Ctrl+Alt+A  git add
Ctrl+K      git commit
Ctrl+Shift+K git push


## **xdebug**
参考文档：https://blog.csdn.net/sszgg2006/article/details/78181757
1. **安装xdebug**
网上下载xdebug的dll文件php_xdebug-2.5.5-5.6-vc11-x86_64.dll(注意xdebug的版本和线程安全类型要完全跟php的保持一致)，拷贝到php的安装目录下的ext目录下,并修改php.ini配置文件，注意以下几行
```
xdebug.remote_host= 127.0.0.1
xdebug.remote_port = 9999
```
2. **修改idea xdebug配置**
文件 -> Settings -> Languages -> PHP -> Debug -> Xdebug
修改端口设置保持与php.ini中一致
3. **两种方式：远程浏览器触发 和 idea触发**
3-1. 远程浏览器触发
*. idea中Run -> Edit Configurations -> 添加PHP Remote Debug -> 设置Ide key
*. chrome浏览器安装xdebug的插件设置Ide Key与idea保持一致
*. 代码设置断点启动debug
*. 浏览器打开xdebug访问页面
3-2. idea触发
*. idea中Run -> Edit Configurations -> 添加PHP Web Application
*. 设置server和地址
*. 设置断点启动debug

## **debug快捷键**
* Shift+F9  开始调试
* Ctrl+F8 设置/取消断点
* F8  下一步（不进入方法）
* Shift+F8 跳出方法
* F7  下一步（进入方法）
* F9  跳到下一个断点
* Alt+F8 选中对象可弹出计算表达式
* Shift+F7  断点所在行有多个方法时会弹出选择进入哪个方法
* Ctrl+F12 结束调试

## **通用快捷键**
* Shift+F6  重命名
* Alt+Enter 选择类名自动引入包，选择接口可以自动生成实现类
* Ctrl+w 选中单词，范围一步一步扩大
* Tab 缩进
* Shift+Tab 反缩进
* Ctrl+N 搜索类
* Ctrl+Shift+N  搜索所有文件
* Ctrl+Shift+Alt+N 搜索标识
* Alt+左右  tab切换
* Ctrl+Shift+V 打开至少5条的粘贴板、
* Ctrl+Alt+S 弹出settings对话框
* Ctrl+shift+U 选中的内容大小写切换
* Ctrl+E 最近打开的文件
* Ctrl+Q 显示详细的函数说明
* Ctrl+P 线上函数参数
* Ctrl+Alt+Left/Right Navigation back/forward
* Alt+Right/Left Navigation between opened tabs
* Ctrl+Shift+Up/Down Move the current line of code
* Ctrl+Alt+V Extract variable
* Ctrl+Alt+F Extract field
* Ctrl+Alt+M Extract Method
* Ctrl+Alt+C Extract a constant
* Ctrl+Alt+P Extract a parameter
* Ctrl+Alt+N inline
* F5 Copy
* F6 Move
* Ctrl+Alt+L Reformat code
* Ctrl+Alt+I Auto-indent lines
* Ctrl+Alt+O Optimize imports
* Ctrl+Shift+A find action
* Ctrl+Shif+Left/Right/Up/Down resize window


## **Live Template**
### 参考文档：https://www.jetbrains.com/help/idea/using-live-templates.html
### 默认模板
1. fori   for (int i = 0; i < ; i++)
2. inn    if( xxx != null)
3. ifn    if( xxx == null)
### 自定义模板
1. **自定义**
Settings -> Editor -> LiveTemplates -> +  -> 设置作用的语言（java）、快捷输入的code和对应的完整代码块
2. **变量**
$var$ 两个美元符号夹起来的表示表里，有以下两个系统内置变量，变量可为占位符
Tab键可以切到下一个变量位置
* $END$ 表示最后一个占位符
* $SELECTION$ 用于环绕模板，选中一段代码，Ctrl+Alt+T会出来所有包含$SELECTION$的Live Template，选择一个，则选中的内容会替换$SELECTION$变量生成Live Template的内容
```
<pfs>
----------
private final static String $varName$  = "$var$";
```
3. **高级用法-函数**
函数参考文档 https://www.jetbrains.com/help/idea/2016.3/live-template-variables.html

* getClass()
```
<log>
---------
/** logger */
private static final Logger logger = LoggerFactory.getLogger($CLASS$.class);
```
选择变量占位符$CLASS$, 点Edit variables, 设置Expression为className()函数，使用log生成代码块是会自动获取类名并填充$CLASS$变量

* clipboard()/decapitalize()
设置$TYPE$的Expression为 clipboard()函数：返回当前粘贴板的字符串
设置$NAME$的Expression为decapitalize(TYPE)函数：输入的字符串首字母为小写
勾选后面的[skip if defined]选项，这样Tab就可以直接到下一个占位符

```
<pv>
---------
/**
 * $END$
 */
@AutoWired(required = false)
private $TYPE$ $NAME$;
```
4. **超级函数groovyScript()**

* groovyScritpt可以执行一段代码实现非常复杂的字符串处理功能
* 语法：groovyScript("code", p1, p2...)
  code: 一段代码/代码的绝对路径
  参数：1个或多个，会绑定到_1,_2,_3..._n, 在code中使用
* 示例：

```
decapitalize(groovyScript("_1.tokenize('.')[-1]", clipboard()))
groovyScript("'\"' + _1.collect { it + ' = [\" + ' + it + ' + \"]'}.join(', ') + '\"'", methodParameters())
```
5. **导入导出Live Template**

* File -> Export Settings -> choose [Live Templates] -> Input path -> ok
* File -> Import Settings -> choose File -> ok
