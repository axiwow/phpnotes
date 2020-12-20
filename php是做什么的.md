《PHP与WEB服务器的请求响应关系》

WEB服务器接受到一个页面的请求，PHP页面或者HTML页面，PHP页面交给PHP预处理器，PHP预处理器与数据库服务器交互，处理结果为静态页面，WEB服务器响应到浏览器。

如果是HTML页面的请求，直接响应到浏览器

《WAMP和PHP配置》
 
设置允许外网访问WEB服务器，httpd.conf

Directory /

设置Deny from all为Allow from all

可使用Apache主机IP地址远程访问该服务

修改端口号

查找Listen 80，修改为8080

设置起始页，查找DirectoryIndex

设置主要目录，查找DocumentRoot，设置

PHP时区设置，php.ini，date.timezone，设置为PRC

short_ open_ tag = On： 表示 允许 使用“<?” 和“?>” 作为 PHP 的 开始 标记 和 结束 标记。

output_ buffering = On： 表示 允许 使用 页面 缓存。 

display_ errors = On： 表示 打开 错误 提示， 在调 试 程序 时 经常 使用

在phpmyadmin打开，Privileges权限，root账户编辑权限，设置密码

phpmyadmin目录，config.inc.php，找到$cfg['Servers']设置，password为密码

《php开始和结束标记》

<?php   ?>

<scripte language="php"></script>

<?   ?>必须设置php.ini，short_open_tag为on

html中嵌入php，<?=$var ?>

php包含类时，如果加了?>会把结束标记后的视为文本输出，不加结尾的话，等于在PHP文件里书写HTML病毒代码，不会有问题

推荐纯PHP的程序（只有PHP代码的程序）都不加结尾，有HTML的再加结尾

被包含的类库和函数库，绝对不能加结尾

<%  %>   php.ini的asp_tags设置为On

《php注释》

/*


*/多行注释

<!--


-->HTML注释

PHP代码中的注释被PHP预处理器忽略，HTML注释会原封不动的输出到浏览器

《PHP语句块》

如果多条PHP语句密不可分，可以用语句块包括

<?php

{

echo "hello1";

echo "hello2";

}

《PHP程序的组成》
	* 
数据的采集
	* 
数据的处理
	* 
数据的输出

数据采集包括浏览器端的数据采集，数据提交，PHP端的数据采集

浏览器端的数据采集

form标签的action指定php程序路径，method指定get或post方法

input type="submit"指定表单提交按钮

html控件的name指定交互控件名，供php程序处理

三个交互控件，radio,checkbox,select>option

文本控件text,password,textarea

文件控件file

PHP的数据采集

使用$_GET或$_POST获取交互控件name属性，得到交互值

PHP的数据处理

与数据库交互，或自行处理

《PHP数据类型》

布尔boolean，整型integer，浮点型float,double

字符串型string，双引号中的变量会自动解析，单引号中的不会，因此单引号速度快，也可以用块包括起来变量

"hello {$world}"

数组array，对象class,object，资源数据类型resource，空null

伪类型，mixed表示可以接受任何数据类型，number整型或浮点型，void没有返回值、没有参数，callback可以接受一个自定义的函数

《PHP程序的输出》

echo和print，print_r输出数组带排版，var_dump输出任何数据类型

print有返回值，可以使用错误抑制符@

《PHP错误抑制符和exit》

在可能会报错的语句前加@

《命名规范》

类首字母大写，函数首字母小写，其余首字母大写

变量驼峰式命名首字母小写，其余首字母大写，或下划线

数组全部小写，有意义英文加s

数据库表字段，下划线分割

常量全部大写

类文件按照类名进行命名

《预定义常量》

DIRECTROY_SEPARATOR目录分割符

PHP_VERSION PHP的版本号

PHP_OS PHP所在的操作系统

内存中为常量的存储分配了一块空间，是全局的，程序运行期间不能修改和销毁

《变量的运行原理》

变量的回收机制是后进先出

栈内存是变量名，内存存放变量的值

传引用，两个栈变量公用同一块内存空间

$var1 &= $var2;

$$arg[1]将$arg[1]作为一个变量，还是将$$arg作为一个可变量

可通过

${$arg[1]}和${$arg}[1]

《变量的函数》

gettype()获得变量数据类型函数

defined()检查一个常量是否定义

isset()检查一个变量是否定义

unset()取消变量的定义

empty()检查变量是否为空，"",0,"0",0.0,null,false,[],空对象

is_null()变量未定义，unset的变量，变量的值为null

数据类型检测函数

is_数据类型，包括bool,string,int,integer,long,doule,float,real,numeric,scalar(标量),object,array,resource

《php运算符》

类运算符，obj instanceof class，判断一个对象是否属于类

执行运算符$cmd = `ping 127.0.0.1`;print $cmd;

位运算符，&都为1时才为1，|其中一个为1则为1，^只有一个为1,时，才为1，~0为1,1为0

>>每一次移动都代表乘以2

<<每一次移动都代表除以2

其中位运算符，判断的是多位的数字，会把一个数字转化为二进制进行运算

$a=12;$b=3;

$a&$b;$a|$b;$a^$b;$a>>$b;$a<<$b;~$a;

《PHP数据转化》

自动数据类型转化

布尔型参与运算时，true转化为1，false转化为0

浮点数与整型，整型转化为浮点型才运算

字符串，数字开头的字符串被视为数字，字符串不以数字开头会转化为0

字符串连接时，整型浮点型被转化为字符串，布尔型和null转化为空字符串

逻辑运算时，"",0,0.0,"0",null,空数组都被转化为false，字符串"0.0"会被转化为true

强制数据类型转化int,bool,float,string,array,object，(int)$a;

intval(),floatval(),strval()返回变量的整数值，浮点数值，字符串值

settype(var,type)包括，bool,int,string,float,array,object,null

《PHP流程控制语句》

不加break的switch，会一直执行，直到遇到break才停止执行

终止php程序的执行exit(msg)或者die(msg)

@($a=2/0) or exit("不能除以0");

exit不是函数而是语言结构