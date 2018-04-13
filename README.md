
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
	shell> nohup ./dbaECG -u xxxxx -p xxxxx  -lazy -d sda -C 5 -i 2 -L /tmp/dbaECG.log  > /dev/null 2>&1 &
```