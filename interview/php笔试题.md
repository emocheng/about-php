# 2016某知名互联网公司PHP面试题及答案

##### 1 字符串”\r”,”\n”,”\t”,”\x20”分别代表什么

```````
 “\r”代表的含义是： 
在Linux、unix 中表示返回到当行的最开始位置，在Mac OS 中表示换行且返回到下一行的最开始位置，相当于Windows 里的 \n 的效果。 
“\n”代表的含义是： 
在Windows 中表示换行且回到下一行的最开始位置。相当于Mac OS 里的 \r 的效果，在Linux、unix 中只表示换行，但不会回到下一行的开始位置。 
“\t”所代表的含义是： 
键盘上的“TAB”键，跳格（移至下一列）。 
“\x20”所代表的含义是：是32在ASCII表中16进制的表示。

```````

##### 2 以下语句输出的结果是什么

```````
$a = 3;
echo "$a",'$a',"\\\$a","${a}","$a"."$a","$a"+"$a";
```````
3$a\$a3336

##### 3 以下语句输出的结果是什么

```````
setcookie("a","value");
print $_COOKIE['a'];

```````
value(若只是这两段编码运行，则会提示PHP Notice: Undefined index: a)

##### 4 php中将当前页面重定向到另一个页面怎么写？

header();

##### 5 什么是魔术引号(magic_quotes_gpc)? 

魔术引号（Magic Quotes）是一个自动将进入 PHP 脚本的数据进行转义的过程。提示：最好在编码时不要转义而在运行时根据需要而转义。

##### 6 在类的方法中，如何调用其父类的同名方法？ 

parent::方法名

##### 7 php中如何取得get，post参数，和上传的文件

``````
$_GET,$_POST,$_FILES
``````

##### 8 如何取得客户端的ip(要求取得一个int)

`````
$_SERVER["REMOTE_ADDR"];ip2long进行转换
`````

##### 9 include和require的区别

require:出现错误后直接终止退出，程序不再执行 
include:包含一个不存在的文件，会提示警告程序会继续执行

##### 10 extends的作用是什么 

类的继承

##### 11 @test()和&test()的区别

@test()的作用是屏蔽test()方法中警告的作用 
&test()引用test()方法

##### 12 array+array与array_merge()的区别 

````````
二者之间的区别是： 
1 键名为数字时，array_merge()不会覆盖掉原来的值，但＋合并数组则会把最先出现的值作为最终结果返回，而把后面的数组拥有相同键名的那些值“抛弃”掉（不是覆盖） 
2 键名为字符时，＋仍然把最先出现的值作为最终结果返回，而把后面的数组拥有相同键名的那些值“抛弃”掉，但array_merge()此时会覆盖掉前面相同键名的值
````````

##### 13 请列举最少3个php对象的魔术方法和说明它们的用途 

```````
 构造方法： __construct() 
析构方法__destruct() 
__get() 控制私有的受保护的未定义的成员属性的访问 
__set() 对私有的受保护的未定义的成员属性进行赋值控制 
__isset() 对私有的受保护的未定义成员属性进行isset和empty的判断控制 
等等

```````

##### 14 什么是fpm

FastCGI Process Manager：FastCGI进程管理器

##### 15 描述一下php开发中常见的几种攻击以及解决方案

`````````````
SQL注入： 
解决这个问题的办法是，将 PHP 的内置 mysql_real_escape_string() 函数用作任何用户输入的包装器。这个函数对字符串中的字符进行转义，使字符串不可能传递撇号等特殊字符并让 MySQL 根据特殊字符进行操作。 
跨站点脚本攻击（XSS）: 
strip_tags() 函数，这个函数可以清除任何包围在 HTML 标记中的内容 
或者使用htmlspecialchars() 函数。
`````````````

##### 16 echo intval(0.58*100) 输出的结果是57，试分析这是为什么？ 

````````````
 原因就是浮点数精度的问题。 
 简单的十进制分数如同 0.1 或 0.7 不能在不丢失一点点精度的情况下转换为内部二进制的格式。
 这就会造成混乱的结果：例如，floor((0.1+0.7)*10) 通常会返回 7 而不是预期中的 8，因为该结果内部的表示其实是类似 7.9999999999…。
 这和一个事实有关，那就是不可能精确的用有限位数表达某些十进制分数。例如，十进制的 1/3 变成了 0.3333333…。
 所以永远不要相信浮点数结果精确到了最后一位，也永远不要比较两个浮点数是否相等。如果确实需要更高的精度，
 应该使用任意精度数学函数或者 gmp 函数
````````````

#### [面试题来源](https://blog.csdn.net/whq19890827/article/details/52684369)

