## crypto-valentines day
- it was said it used portable network graphics
- so we know that staring bits pattern of png
- with that we get the key 
```
The first eight bytes of a PNG file always contain the following (decimal) values:

   137 80 78 71 13 10 26 10
```
## receck
```
f = open("test.png", "rb").read()
key = [f[0], f[1], f[2], f[3], f[4], f[5], f[6], f[7]]
print("key is ",key)
```
### result
```
key is  [137, 80, 78, 71, 13, 10, 26, 10]
```
## encrypted way 
```
from PIL import Image
from itertools import cycle

def xor(a, b):
    return [i^j for i, j in zip(a, cycle(b))]

f = open("original.png", "rb").read()
key = [f[0], f[1], f[2], f[3], f[4], f[5], f[6], f[7]]

enc = bytearray(xor(f,key))

open('enc.txt', 'wb').write(enc)
```
### solve.py
```
from itertools import cycle

def xor(a, b):
    return [i^j for i, j in zip(a, cycle(b))]


enc_file=open("enc.txt","rb")
enc_data=enc_file.read()
print("size of enc_data is ",len(enc_data))
print("ecn data[:50]",enc_data[:50])
key = [137, 80, 78, 71, 13, 10, 26, 10]

dec_file=open("dec.png","wb")
dec_file.write(bytes(xor(enc_data,key)))

enc_file.close()
dec_file.close()



```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/316432f8-5164-4e6b-b2fa-bd1568bef076)
VishwaCTF{h3ad3r5_f0r_w1nn3r5}
