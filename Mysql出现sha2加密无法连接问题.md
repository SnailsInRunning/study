# mysql8 ：客户端连接caching-sha2-password问题

## 问题描述：在安装mysql8的时候如果选择了密码加密，之后用客户端连接比如navicate，会提示客户端连接caching-sha2-password,是由于客户端不支持这种插件
## 解决方案：
 
    ALTER USER 'root'@'localhost' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER; 
    #更新密码（mysql_native_password模式）    
    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '{NewPassword}';