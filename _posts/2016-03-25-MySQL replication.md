MySQL5.5 master/slave replication steps

1. Setting the Replication Master Configuration
To configure the binary log and server ID options, you will need to shut down your MySQL server and edit the my.cnf or my.ini file. Add the following options to the configuration file within the [mysqld] section. If these options already exist, but are commented out, uncomment the options and alter them according to your needs. For example, to enable binary logging using a log file name prefix of mysql-bin, and configure a server ID of 1, use these lines:
<code><pre>
[mysqld]
log-bin=mysql-bin
server-id=1
</pre></code>

After making the changes, restart the server.

If you omit server-id (or set it explicitly to its default value of 0), a master refuses connections from all slaves.
Ensure that the skip-networking option is not enabled on your replication master. If networking has been disabled, your slave will not able to communicate with the master and replication will fail.

2. Setting the Replication Slave Configuration
On a replication slave, you must establish a unique server ID. 
<code><pre>
[mysqld]
server-id=2
</pre></code>

Restart.

If you are setting up multiple slaves, each one must have a unique server-id value that differs from that of the master and from each of the other slaves. Think of server-id values as something similar to IP addresses: These IDs uniquely identify each server instance in the community of replication partners.

3. Obtaining the Replication Master Binary Log Coordinates
3.1 Start a session on the master by connecting to it with the command-line client, and flush all tables and block write statements by executing the FLUSH TABLES WITH READ LOCK statement:
<code><pre>
mysql> FLUSH TABLES WITH READ LOCK;
</pre></code>
Warning
Leave the client from which you issued the FLUSH TABLES statement running so that the read lock remains in effect. If you exit the client, the lock is released.
3.2 In a different session on the master, use the SHOW MASTER STATUS statement to determine the current binary log file name and position:
<code><pre>
mysql> SHOW MASTER STATUS;
</pre></code>

The "File" column shows the name of the log file and Position shows the "position" within the file. In this example, the binary log file is mysql-bin.000003 and the position is 73. Record these values. You need them later when you are setting up the slave. They represent the replication coordinates at which the slave should begin processing new updates from the master.
<b>remember the File and position value which you need to specify on the slave server</b>


4. Creating a Data Snapshot Using mysqldump
shell> mysqldump demo --master-data > d:\demo.db --user=root --password=xxx

5. Setting Up Replication with Existing Data
shell> mysql -u root -pxxxx demo < demo.db

6. Start slave threads
mysql> START SLAVE;

7. Setting the Master Configuration on the Slave
mysql> CHANGE MASTER TO
    ->     MASTER_HOST='master_host_name',
    ->     MASTER_USER='replication_user_name',
    ->     MASTER_PASSWORD='replication_password',
    ->     MASTER_LOG_FILE='recorded_log_file_name',
    ->     MASTER_LOG_POS=recorded_log_position;
    
8. Check slave replication status
mysql> show slave status\G



MySQL5.5 主从复制配置步骤

1. 配置主服务器
备注：配置主服务器前需要首先暂停服务器使用(停止使用yycoin应用以及所有需要用到数据库的相关程序)。
关闭mysql服务，在mysql安装目录下找到my.conf,并找到 [mysqld] 部分,加入以下两行:
[mysqld]
log-bin=mysql-bin
server-id=1

改完保存,重启mysql

2. 配置备份服务器
同样关闭mysql,在my.conf中找到[mysqld]部分，加入一行：
[mysqld]
server-id=2

保存重启.

3. 获取主服务器二进制日志坐标(复制起点)
使用mysql客户端连接服务器,执行以下语句以禁止写入数据库
mysql> FLUSH TABLES WITH READ LOCK;
备注：如果断开当前客户端会导致写入锁被释放。
重新打开一个mysql客户端,执行以下语句获取当前二进制日志文件坐标
mysql> SHOW MASTER STATUS;
其中"File"栏位代表日志文件名,"Position"栏位代表复制坐标。 记住这两个栏位的值,后边配置备份服务器时需要用到它们。


4. 主服务器数据库做好备份
shell> mysqldump demo --master-data > d:\demo.db --user=root --password=xxx

5. 在备份服务器导入数据备份
shell> mysql -u root -pxxxx demo < demo.db

6. 在备份服务器上启动slave线程
mysql> START SLAVE;

7. 在备份服务器上设置master信息
mysql> CHANGE MASTER TO
    ->     MASTER_HOST='主服务器IP',
    ->     MASTER_USER='root',
    ->     MASTER_PASSWORD='主服务器数据库访问密码',
    ->     MASTER_LOG_FILE='步骤3中的File栏位',
    ->     MASTER_LOG_POS=步骤3中的Position数值;
    
8. 配置好之后，可以在主服务器上写入数据,检查备份服务器是否自动同步，也可以在备份服务器上执行以下命令查看复制状态：
mysql> show slave status\G


### Reference
http://dev.mysql.com/doc/refman/5.5/en/replication-howto.html
show processlist