重定向的概念

浏览器向服务器发送page1页面的请求，page1页面响应到浏览器一个重定向响应头

浏览器收到WEB服务器page1页面的响应头后，向响应头中的page2服务器发送请求，page2页面响应结果（运行结果）返回到浏览器

javascript实现重定向

window.location="http://www.baidu.com";

window.location.replace('http://www.baidu.com");

php实现重定向

header('Location:url');

会话控制，HTTP是无状态的协议

浏览器向WEB服务器page1页面请求，page1页面响应一个cookie响应头到浏览器，浏览器存储cookie到浏览器进程还是浏览器端主机硬盘中

向page2发送请求时，会自动的将浏览器端的cookie信息放到第二次请求头中

cookie响应头的信息有

Set-Cookie包含cookie信息

name cookie的标记名称

value cookie的值

expire过期时间，UNIX时间戳

path在WEB服务器的有效路径

domain有效域名

secure是HTTP还是HTTPS

只有浏览器端cookie没有过期，domain和path有效的时候，该cookie才有效，否则cookie失效

会话cookie，cookie过期时间为过去的时间，或者没有指定cookie的过期时间，存储在浏览器进程中

持久cookie，cookie过期时间为未来的某个时间，保存在浏览器硬盘文件中

防止提示，header already sent错误提示信息，将output_buffering设置为On

创建cookie，setcookie()函数

setcookie('key','value1',time()+60,'','',false);

任何键值对，的值经过urlencode()函数处理

预定义变量$_COOKIE，删除cookie，setcookie('key','')

设置cookie数组

setcookie('name[1]','value1');setcookie('name[2]','value2');setcookie('name[one]','value3');

session会话技术

从用户第一次访问服务器开始，到断开服务器的连接，形成一个session会话周期

浏览器向WEB服务器的page1页面发出请求，page1产生一个独立的标记标识该请求，将session文件保存在WEB服务器硬盘中。

page1页面向响应头添加一个cookie响应头，在响应发送到浏览器前，可以给session文件添加用户，cookie响应头随着page1页面的响应发送给浏览器

浏览器向WEB服务器page2发出请求，自动将浏览器的cookie信息放入到第二次请求头中，page2接受cookie信息的session标记，取出session文件对应的用户个人信息，从而实现不同页面间的参数传递

session和cookie的区别

cookie在浏览器端，session在服务器端

浏览器用户可以禁止cookie，无法禁止session

session使用，关闭浏览器只会使得浏览器端会话cookie失效，不会使得session信息失效

只有page1页面响应后才有cookie信息，因此第一次请求page1页面时，page1页面不能访问到cookie信息

session可以存储复合型数据类型，cookie只能存储字符串类型

PHP使用session

session_start()产生一个session标记，创建session id命名的文件和cookie响应头信息，session name作为键（PHPSESSID），
session id标记作为值

使用$_SESSION实现用户信息，在session文件的注册，读取，修改和释放

page1页面执行结束后，cookie响应头随着page1页面的响应发送到浏览器，浏览器将cookie信息保存到浏览器使用的内存中
浏览器将响应头请求page2，page2调用session_start()，由于请求头中存在session id，page2页面不再产生新的session id，而是获取到session id，和将session id对应的session文件解析到$_SESSION中，page2可以访问page1写入到session文件的信息。浏览器关闭后，会话cookie从浏览器端内存删除，session文件依旧存在，直到过期时间到

若浏览器关闭了cookie，可以将session name和session id附在url后面进行传递，保证能够寻找到对的session文件即可

session在php.ini文件中的配置

session.save_handler=files  files文件保存，user数据库保存

session.save_path=files  session文件的保存路径

session.use_cookies=1  session id使用cookie传递，为0时使用查询字符串

session.name=PHPSESSID  session id的名称

session.auto_start=0  是否自动开启session  

session.cookie_lifetime=0  过期时间，浏览器一旦关闭，session立即失效

session.cookie_path=/   传递session id时cookie的有效路径

session.cookie_domain=   使用session时cookie的有效域名

session.gc_maxlifetime=1440  1440s，24分钟，session无操作自动销毁掉

开启session，session_start()加载php.ini文件有关session的配置信息至WEB服务器内存，创建session id或者使用已有的session id，请求头中有Set-Cookie:PHPSESSID=的cookie信息，则直接使用该session，没有创建一个新的session id标识该请求，把session文件解析到$_SESSION变量中，产生cookie响应头信息发送到浏览器，php程序开启session，会产生cookie响应头信息，因此使用

session_start开启session前，浏览器不能有任何输出

session.auto_start=1不必每个页面使用session_start()开启session

session_id返回一个session id标记

session_name设置session name的值

PHP定义了一个常量SID，session name=session id

不包含PHPSESSID=session id，则创建SID常量，否则为空字符串

第一次请求有PHPSESSID=session id的字符串，第二次请求SID的值为空字符串

传session_id()到Url查询字符串中，php端session_id($_GET['phpsessid']);session_start();

$_SESSION数组中用于读取session文件的信息，unset释放$_SESSION数组的某些元素，此时session文件的对应信息也会被删除，但该函数无法删除session文件，删除session文件的所有信息，$_SESSION=array();不能使用unset($_SESSION);否则无法通过$_SESSION维护session文件

session_unset()等价于$_SESSION=array();

session_destory()销毁session文件，

彻底删除session的所有资源，清除浏览器的cookie信息，使用setcookie()把session设置为过期即可


setcookie(name,value,expire,path,domain,secure,httponly)

expire是过期时间，秒为单位

path的cookie的有效目录，/当前目录均可用，/foo/在foo目录和其子目录均可用

example.com该域名和所有子域名均可用

secure是否https，httponly是否可通过js操作cookie

使用$_COOKIE[name]访问cookie

php.ini通过session_save_path设置session文件的存储路径

可以用redis存储session，使用session_set_save_handle函数








