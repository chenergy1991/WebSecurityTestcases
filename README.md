主要操作步骤：

1. 新建post数据库，导入post.sql。
2. 模拟XSS，运行xss module中的`XssApplication`，然后打开`localhost:8084/readPost.html`。
3. 模拟SQL注入，运行sql-injection中的`SQLInjectionApplication`，然后打开`localhost:8083/login.html`。
4. 模拟csrf，启动csrf-defence module中application，端口是8081，此为被攻击网站，启动 csrf-attack中的CSRFApplication，端口为8082，此为攻击网站。

代码运行环境：
1. 操作系统：Win 10
2. JDK：9.0.4
3. MySQL：5.0.96
4. IDE：IntelliJ IDEA 2019.1.1


MySQL数据库参考命令：
```
$mysql -u root -p
mysql> create database post;
mysql> use post;
mysql> source /Users/mac/Code/JavaWorkspace/web-security-master/sql/post.sql;
```

CSRF模块备注：
* csrf-defence的deletePost2.html对应/post2/{id}接口；该接口未做CSRF防御。
* csrf-defence的deletePost.html对应/post/{id}接口；该接口已经做CSRF防御。
`
参考链接：
* [常见web攻击总结](https://www.cnblogs.com/morethink/p/8734103.html#CSRF)
* [/morethink/web-security](https://github.com/morethink/web-security)（源码修改自该GitHub项目）