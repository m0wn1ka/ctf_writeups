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


## web/they are coming
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/33814948-2683-4849-86e0-496c680db217)
- try to go to /robots.txt
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2d284718-1a59-48d4-aed8-7ed4dffbb1c2)
```
C:\home\radha\Downloads\viswa_ctf\web> echo "L3NlY3JldC1sb2NhdGlvbg=="|base64 -d
/secret-location                                                                                                                                                                       

```

- at admin
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7f5ccb6b-aec2-4684-b673-673b16def671)
- at secret-locaiton
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e32443b2-c5bb-43a0-85f7-e90e5778a8fc)
- try x headers for local host like forwarded for,forwarded host,
## tries
- X-Forwarded-Host: localhost --no
- X-Forwarded-Host: 127.0.0.1 --no
- X-Forwarded-For: 127.0.0.1 --no
- X-Forwarded-For: localhost --no
## robotstxt.html
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a7850246-609f-4918-90eb-3c6a05c04d4f)

### data at secret locaion
```
A Courrpt AI Agent and Its Army of 128 Aesthetic Looking Robots Are Heading Towards Local Vault of the City of Dawn!
```
### data at description
```
Aesthetic Looking army of 128 Robots with AGI Capabilities are coming to destroy our locality!
```
- so it has somthing to do with useragent
- 




## Recipe Archival Workshop
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d129a70b-8c8a-4abd-9369-b0ba57a36e38)
```
New interns in the Recipe Archival Workshop have a simple task- upload images of yummy delicacies and dream about tasting them some day.
```
- so we need to upload images and they will be may be visited by admin bot ,there exists a remote code execution
- say the uploaded files need to be saved somewhere
- so we need execute commands and get the output saved in public folder or try to ping the output to a webhook site
- here the check for file type does happen
- however it is not much strict
- we can say the name of file as png with extnsion and change the content as per our wish and it accepts and uplaods
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f143deae-1eb8-4d29-93b7-df121fe59091)
- it uses php as can be seen while uploading it goes to /upload.php
- try this
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8972e7cf-27a6-4723-9b70-4486babe87a1)
but did not work
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/45e17a62-c7f2-4c7f-889a-96d771fa4e58)


