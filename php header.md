header(msg)

msg的语法格式，header_name:header_value

header的几个语法头

Location:URL

Refersh:N;url=URL

页面延迟几秒后，自动刷新跳转到url，若延迟时间为0，则等价于Location:URL

Set-Cookie:name=value

服务器响应内容的控制

Content-Type:MIME类型

text/html;charset=utf-8

Content-Length:长度

正文信息的长度，1234为正文消息的长度为1234字节，收到指定字节数信息就认为已经被完整接收了

Content-Disposton:attchment;filename=文件名;

提示下载对话框，提示浏览器用户下载对应的文件信息

浏览器缓存的远程控制

HTTP/1.0

HTTP/1.1

3个可以控制浏览器缓存的HTTP头，Last-Modified,Expires,Cache-Control



public正文信息可以被多个浏览器用户共享，private仅对当前浏览器用户有效，对其他用户无效

no-cache不能被浏览器缓存，js,css图像等静态资源除外

no-store不能被浏览器缓存

must-revalidate所有缓存数据都必须重新验证

proxy-revalidate代理服务器的缓存

max-age缓存数据的寿命，单位是秒

s-maxage代理服务器的缓存，单位是秒


MIME类型都有哪些？





