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
## limited 2
- question
```
import time
import random
import sys

if __name__ == '__main__':
    flag = input("Flag? > ").encode('utf-8')
    correct = [192, 123, 40, 205, 152, 229, 188, 64, 42, 166, 126, 125, 13, 187, 91]
    if len(flag) != len(correct):
        print('Nope :(')
        sys.exit(1)
    if time.gmtime().tm_year >= 2024 or time.gmtime().tm_year < 2023:
        print('Nope :(')
        sys.exit(1)
    if time.gmtime().tm_yday != 365 and time.gmtime().tm_yday != 366:
        print('Nope :(')
        sys.exit(1)    
    for i in range(len(flag)):
        # Totally not right now
        time_current = int(time.time())
        random.seed(i+time_current)
        if correct[i] != flag[i] ^ random.getrandbits(8):
            print('Nope :(')
            sys.exit(1)
        time.sleep(random.randint(1, 60))
    print(flag)

``` 
### sovle not working
```
import time
import random ##not workign
import sys
correct = [192, 123, 40, 205, 152, 229, 188, 64, 42, 166, 126, 125, 13, 187, 91]
start=1703847081
end  =1704149481
for k in range(start,end):
    sleep_time=0
    y=''
    for i in range(15):
        # Totally not right now
        time_current = k+sleep_time
        random.seed(i+time_current)
        x=chr(correct[i]^random.getrandbits(8))
        sleep_time=sleep_time+(random.randint(1, 60))
        y=y+x
    # print("y is ",y)
    if("wctf" in y):
        print("flag is ",y)
print("done")

```
## solves
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c895409f-fc18-4c45-903c-8ea23bcd0d98)
## scoreboard
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b75dbc89-5d49-4c58-ab8e-52c33133ddad)
## profile
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/9149a902-1b48-454b-8d16-bfd4029e1a56)
