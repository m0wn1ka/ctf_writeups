## web/username  --not completed
- question
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5d1faee1-8209-476c-b1a0-4ad79f6e2572)
- sample jwt token
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/44b60a25-ddd7-40d1-a690-94de02c832d1)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/0bb5e6e3-5677-4db7-9ced-5fbd4849299d)
- it is using hs256 may be it supports none
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjoiPGRhdGE-PHVzZXJuYW1lPnJhZGhhPC91c2VybmFtZT48L2RhdGE-In0.F3lx8mV6CHrqFYFL4x59D2nbZjNp0RLRU5LzIp3akF8
```
eyJhbGciOiAiTm9uZSIsICJ0eXAiOiAiSldUIn0K


  {
  "alg": "None",
  "typ": "JWT"
}

eyJhbGciOiAiTm9uZSIsICJ0eXAiOiAiSldUIn0K.eyJkYXRhIjoiPGRhdGE-PHVzZXJuYW1lPnJhZGhhPC91c2VybmFtZT48L2RhdGE-In0.ll
this is not workgni
```
## crypto /limited one
- question
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/bcdbb3db-91d6-4dd5-b6ac-606925ab58ca)
- this is the given code
```
import time
import random
import sys

if __name__ == '__main__':
    flag = input("Flag? > ").encode('utf-8')
    correct = [189, 24, 103, 164, 36, 233, 227, 172, 244, 213, 61, 62, 84, 124, 242, 100, 22, 94, 108, 230, 24, 190, 23, 228, 24]
    time_cycle = int(time.time()) % 256
    if len(flag) != len(correct):
        print('Nope :(')
        sys.exit(1)
    for i in range(len(flag)):
        random.seed(i+time_cycle)
        if correct[i] != flag[i] ^ random.getrandbits(8):
            print('Nope :(')
            sys.exit(1)
    print(flag)

```
### solution script
```
import time
import random
import sys
min_seed=0 #flag len from 0-25 and time from 0-256
max_seed=282 #25+256 +1(for safety)
correct = [189, 24, 103, 164, 36, 233, 227, 172, 244, 213, 61, 62, 84, 124, 242, 100, 22, 94, 108, 230, 24, 190, 23, 228, 24]
for j in range(257):  
    y=""
    for i in range(25):
            random.seed(i+j)
            x=chr(correct[i]^random.getrandbits(8))
            y=y+x
    if("wctf" in y):
         print("flag is ",y)
    # print("j is ",j)
```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7f6061b5-251a-4c5d-bd4f-290c28fc2f5a)
- flag is  wctf{f34R_0f_m1ss1ng_0ut}
