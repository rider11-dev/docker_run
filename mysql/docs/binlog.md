- 参考
    - https://github.com/alibaba/canal/wiki/QuickStart
    - https://zhuanlan.zhihu.com/p/177001630
- my.cnf
```ini
[mysqld]
log-bin=mysql-bin # 开启 binlog
binlog-format=ROW # 选择 ROW 模式
server_id=1 # 配置 MySQL replaction 需要定义，不要和 canal 的 slaveId 重复
```
- 创建用户、授权
```sql
CREATE USER canal IDENTIFIED BY 'canal';  
GRANT SELECT, REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'canal'@'%';
-- GRANT ALL PRIVILEGES ON *.* TO 'canal'@'%' ;
FLUSH PRIVILEGES;
show grants for 'canal';
```
- 检查
```shell
# 是否打开
show variables like 'log_bin';
show variables like 'binlog_format';
# 查看binlog日志文件列表
show binary logs;
# 查看当前正在写入的binlog文件
show master logs;
```
