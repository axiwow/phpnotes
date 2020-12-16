error_reporting(0);不显示错误

异常类Exception，message异常消息内容，code异常代码，file异常文件名，line异常行号，getMessage,code,file,line

getTrace异常追踪信息，getTraceAsString字符串类型异常追踪信息，getPrevious异常链的前一个异常，__toString异常对象转化为字符串

__clone异常克隆

if($msg){return $msg;}else{throw new Exception('database error');}

try{}catch(Exception $e){echo $e->getMessage();}

创建自己的异常类

class EmailException extends Exception{

    return "邮箱异常";

}

错误级别配置

error_log(错误信息，错误文件发送何处，[文件，额外头])

0php系统日志，1邮件地址，3文件里，4 SAPI的日志处理程序

错误函数

handler(errno错误级别，errstr错误信息，errfile错误文件，errline错误行号，errcontext错误解析的作用域所有变量数组

set_error_handler('error_handler');

就可以自定义Exception的msg

php7中的错误处理，大多被视为Error异常自动加载，而不必将错误看做异常

try{}catch(Error $e){}

