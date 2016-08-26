---
title: Fedora 19 下 Mysql 报错 ERROR 2002 解决方法
tags:
  - Fedora
  - Mysql
date: 2013-11-12 09:32:00
---

使用

<pre class="brush:bash">
mysql -u root -p</pre>

	启动Mysql报错

<pre class="brush:bash">
ERROR 2002 (HY000): Can&#39;t connect to local MySQL server through socket &#39;/var/lib/mysql/mysql.sock&#39; (2)
</pre>

	然后

<pre class="brush:bash">
su -
service mysqld start
mysql -u root -p</pre>

	还是出现

<pre class="brush:bash" style="font-size: 13px;">
ERROR 2002 (HY000): Can&#39;t connect to local MySQL server through socket &#39;/var/lib/mysql/mysql.sock&#39; (2)</pre>

	发现是service 这里可能会有问题

	用绝对路径启动就行了

<pre class="brush:bash">
/etc/init.d/mysqld start
</pre>

	启动Mysql

	完整命令

<pre class="brush:bash">
su -
/etc/init.d/mysqld start
mysql -u root -p</pre>

	 