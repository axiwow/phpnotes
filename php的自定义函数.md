《include和require》

include可以包含互联网上的资源，php.ini开启allow_url_include=On

require和include的区别

使用include，如果找不到文件，被引用文件发生错误，继续执行后面的代码

使用require，被引用文件发生错误，找不到被引用文件，提示warning信息和fatal error致命错误信息后停止程序运行

多次引用同一文件的情况中，include_once和require_once可以避免多次引用同一个PHP文件

《引用传值和变量函数》

如果需要修改传递给函数的变量的值，可以使用引用传值方式

function func(&$var){}

变量函数

$var = 'func';

$var();

《return》

return "返回值";也可以return("返回值");

return只会结束被引用php程序的运行，是体现在包含文件中，exit是结束全部

return;无返回值的return，直接返回

《函数参数类型》

Bool,Int,Float,String,Array,Callback(回调函数),Class/Interface

可变参数function test(...$num){foreach($num as $key=>$value){echo $value;}test(1,2,3,4);

list($one,$two,$three)=[1,2,3];

返回值的类型声明

function sum($a,$b):float{return $a+$b;}  float(3.0)

严格模式declare(strict_type=1);

可变函数

$func="hello";function hello(){};$func();

匿名函数echo preg_replace_callback('~-([a-z])~',function($match){return strtoupper($match[1];},"hello-world");

闭包函数$greet = function($name){print $name;} $greet("hello wolrd");

可变变量实际上就是定义一个字符串值同名的变量，双$调用原先的值是变量名的变量

转化为closure的对象实例，闭包函数也可以作为变量的值

$msg = "hello";$ex = function() use($msg){print $msg;}

要使得修改后的变量值作用到函数内

$msg= "hello";$ex = function() use(&$msg){print $msg;}

《递归与迭代》
在面临一个庞大的问题时，需要把这个庞大的问题拆分成各个细小的单元，解决了每个细小的单元的问题，这个庞大的问题就迎刃而解了

递归就是程序调用自身，函数不断引用自身，直到引用的对象已知。构成递归需要满足以下两个条件

子问题需与原始问题为同样的事，且更为简单

不能无限制地调用本身，必须有一个出口，化简为非递归状况处理

递归的一种语句结构

if(条件)函数本身 return 答案值; else{退出return;}






