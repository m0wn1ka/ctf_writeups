## smoke out the rat
```
                                                                                                                                                                      
C:\home\radha\Downloads\viswa_ctf\digita forensics\smoke out the rat> file *
DBlog-bin.000007: MySQL replication log, server id 1 MySQL V5+, server version 8.0.36

```
https://www.boltic.io/blog/mysql-binlog
- BinLogs are written in a binary format and are not meant to be read directly by humans. However, they can be viewed and analysed using tools
  such as MySQL Binlog, which is included in the MySQL distribution
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8e83bd67-bcd8-45fe-b0d8-2772d439be71)
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/da4b781b-e6aa-4435-bbe3-08d85ae68977)
### trying binlog
```
C:\home\radha\Downloads\viswa_ctf\digita forensics\smoke out the rat> sudo mysqlbinlog DBlog-bin.000007
/*!50530 SET @@SESSION.PSEUDO_SLAVE_MODE=1*/;
/*!40019 SET @@session.max_delayed_threads=0*/;
/*!50003 SET @OLD_COMPLETION_TYPE=@@COMPLETION_TYPE,COMPLETION_TYPE=0*/;
DELIMITER /*!*/;
# at 4
#240217 14:45:13 server id 1  end_log_pos 126 CRC32 0x32e61563  Start: binlog v 4, server v 8.0.36 created 240217 14:45:13 at startup
# Warning: this binlog is either in use or was not closed properly.
ROLLBACK/*!*/;
BINLOG '
IXnQZQ8BAAAAegAAAH4AAAABAAQAOC4wLjM2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAhedBlEwANAAgAAAAABAAEAAAAYgAEGggAAAAICAgCAAAACgoKKioAEjQA
CigAAWMV5jI=
'/*!*/;
# at 126
#240217 14:45:13 server id 1  end_log_pos 157 CRC32 0xea8569cb  Ignorable
# Ignorable event type 35 (MySQL Previous_gtids)
# at 157
#240218 21:54:55 server id 1  end_log_pos 236 CRC32 0x92d92a42  Ignorable
# Ignorable event type 34 (MySQL Anonymous_Gtid)
# at 236
mysqlbinlog: Character set '#255' is not a compiled character set and is not specified in the '/usr/share/mysql/charsets/Index.xml' file
zsh: segmentation fault  sudo mysqlbinlog DBlog-bin.000007

```

