浏览器向WEB服务器发出一个请求，PHP程序接受到请求，再对请求进行处理，WEB服务器将处理结果作为响应返回给浏览器

get提交方式是将请求数据以查询字符串的方式附在URL后提交数据

?p1=value1&p2=value2&p3=value3

查询字符串不允许有空格的存在

get和post混合提交，在form中url带有查询字符串，method是post

post更安全，post能提交更多的数据，不同的提交方式php处理也不同

/开始的路径代表从WEB服务器根目录开始

./表示当前目录

../表示文件所在目录的上一级目录

form的enctype设置提交表单时的数据编码格式，默认为applicaiton/x-www-form-urlencode，文件上传时必须设置为

multipart/form-data

单选框

<input type="radio" name="" value="" checked></input>

复选框

<input type="checkbox" name="" value="" checked></input>

下拉框

<select name="" multiple>

<option value="" selected></option>

<option value=""></option>

</select>

文件框

<input type="file" name="" maxlength=""></input>

使用数组

<select name="s[]">

<input type="file" name="files[]"><input type="file" name="files[]">

<input type="checkbox" name="inter[]“><input type="checkbox" name="inter[]“>

《预定义变量》
$_GET，$_POST，$_REQUEST，$_COOKIE，$_SESSION，$_FILES，$_SERVER，$_ENV

《上传文件》

php.ini中的

file_uploads=On是否允许通过HTTP上传文件

post_max_size=8M配置post提交数据时，PHP服务器所能接受的最大表单数据大小

upload_max_size文件上传控件中上传文件的最大值，默认为2M

upload_tmp_dir上传文件中的产生临时文件目录

max_input_time解析提交数据的最大允许时间，单位是秒，为-1时表示不限制

memory_limit单个PHP程序在运行时，可以占用服务器最大内存数，默认值为128M，-1表示不限制

max_execution_time单个PHP程序在运行时占据服务器的最大时间，单位是秒，默认为30，0表示不限制

先检测是否超过post_max_size，检测隐藏域MAX_FILE_SIZE（超过状态码2）和upload_max_size（超过返回1）

max_execution_time响应时间超过，返回状态码3，上传成功返回状态码0

is_uploaded_file()判断是否为上传过程中产生的临时文件，和move_uploaded_file保存临时文件到WEB服务器或文件服务器

预定义变量$_FILES可以获取上传文件的相关信息

$_FILES['files']['name']上传文件的文件名，['type']上传文件的MIME类型，['size']上传文件的大小，['tmp_name']临时文件名，

['error']错误状态码，0成功，1upload_max_size超过，2MAX_FILE_SIZE超过，3部分上传，4没有选择上传文件

判断error状态码，如果为0，则移动文件到指定目录下move tmp_name到路径中

《其他采集数据的办法》

$_REQUEST即可以采集$_GET，也可以采集$_POST

php.ini的request_order="GP"，先get后post，改为PG，则先POST后get

$_SERVER变量

REMOTE_ADDR浏览器端的主机IP地址，$_SERVER['REMOTE_ADDR']

SERVER_ADDR服务器端IP地址

PHP_SELF当前文件名

QUERY_STRING查询字符串

REQUEST_URI除域名外的其余URI部分

DOCUMENT_ROOT  WEB服务器主目录







