
dba心电图
========================================================================================================================

基于orzdba脚本修改，添加用户名和帐号以及“Show Full Processlist”参数
 
```
Usage :
Command line options :

	 -h,--help           Print Help Info.
	 -i,--interval       Time(second) Interval.
	 -C,--count          Times.
	 -t,--time           Print The Current Time.
	 -nocolor            Print NO Color.

	 -l,--load           Print Load Info.
	 -c,--cpu            Print Cpu  Info.
	 -s,--swap           Print Swap Info.
	 -d,--disk           Print Disk Info.
	 -n,--net            Print Net  Info.

	 -u                  MySQL User(default root).
	 -P                  MySQL Password(default iforgot).
	 -P,--port           Port number to use for mysql connection(default 3306).
	 -S,--socket         Socket file to use for mysql connection.

	 -mysql              Print MySQLInfo (include -t,-com,-hit,-T,-B).
	 -innodb             Print InnodbInfo(include -t,-innodb_pages,-innodb_data,-innodb_log,-innodb_status)
	 -com                Print MySQL Status(Com_select,Com_insert,Com_update,Com_delete).
	 -hit                Print Innodb Hit%.
	 -processlist        Print Show Full Processlist
	 -innodb_rows        Print Innodb Rows Status(Innodb_rows_inserted/updated/deleted/read).
	 -innodb_pages       Print Innodb Buffer Pool Pages Status(Innodb_buffer_pool_pages_data/free/dirty/flushed)
	 -innodb_data        Print Innodb Data Status(Innodb_data_reads/writes/read/written)
	 -innodb_log         Print Innodb Log  Status(Innodb_os_log_fsyncs/written)
	 -innodb_status      Print Innodb Status from Command: 'Show Engine Innodb Status'
						(history list/ log unflushed/uncheckpointed bytes/ read views/ queries inside/queued)

	 -T,--threads        Print Threads Status(Threads_running,Threads_connected,Threads_created,Threads_cached).
	 -B,--bytes          Print Bytes received from/send to MySQL(Bytes_received,Bytes_sent).
	 -rt                 Print MySQL DB RT(us).

	 -sys                Print SysInfo   (include -t,-l,-c,-s).
	 -lazy               Print Info      (include -t,-l,-c,-s,-com,-hit).

	 -L,--logfile        Print to Logfile.
	 -logfile_by_day     One day a logfile,the suffix of logfile is 'yyyy-mm-dd';
	                     and is valid with -L.

Sample :
	shell> ./dbaECG -u xxxxx -p xxxxx -innodb  -C 5 -i 2  2>/dev/null
	shell> ./dbaECG -u xxxxx -p xxxxx -lazy -d sda -C 5 -i 2 2>/dev/null
	shell> ./dbaECG -u xxxxx -p xxxxx -processlist -C 5 -i 2 2>/dev/null
	shell> nohup ./dbaECG -u xxxxx -p xxxxx  -lazy -d sda -C 5 -i 2 -L /tmp/dbaECG.log  > /dev/null 2>&1 &
```

processlist参数会把sleep线程过滤掉，保留活动线程


```
	shell> ./dbaECG  -u monitor -p xxxxx  -processlist -C 5 -i 2  2>/dev/null

.=================================================.
|          Welcome to use the dba ECG !           |
'=============== Date : 2018-04-13 ==============='

HOST: mycat01.mysql.com   IP: 192.168.49.246
DB  : performance_schema|sys
Var : binlog_format[ROW] max_binlog_cache_size[17179869184G] max_binlog_size[1G]
      max_connect_errors[100000] max_connections[10000] max_user_connections[9990]
      open_files_limit[50000] sync_binlog[0] table_definition_cache[912]
      table_open_cache[1024] thread_cache_size[64]

      innodb_adaptive_flushing[ON] innodb_adaptive_hash_index[ON] innodb_buffer_pool_size[4G]
      innodb_file_per_table[ON] innodb_flush_log_at_trx_commit[2] innodb_flush_method[O_DIRECT]
      innodb_io_capacity[200] innodb_lock_wait_timeout[5] innodb_log_buffer_size[16M]
      innodb_log_file_size[2G] innodb_log_files_in_group[2] innodb_max_dirty_pages_pct[75.000000]
      innodb_open_files[1024] innodb_read_io_threads[4] innodb_thread_concurrency[64]
      innodb_write_io_threads[4]

-------------------------------------- show full processlist --------------------------------------
---------------------------------------------------------------------------------------------------
####################################### 2018-04-13 10:52:37 #####################################>
 11036	monitor	localhost	NULL	Query	0	starting	show full processlist

####################################### 2018-04-13 10:52:39 #####################################>
 11037	monitor	localhost	NULL	Query	0	starting	show full processlist

####################################### 2018-04-13 10:52:41 #####################################>
 11038	monitor	localhost	NULL	Query	0	starting	show full processlist

####################################### 2018-04-13 10:52:43 #####################################>
 11039	monitor	localhost	NULL	Query	0	starting	show full processlist

####################################### 2018-04-13 10:52:45 #####################################>
 11040	monitor	localhost	NULL	Query	0	starting	show full processlist

```