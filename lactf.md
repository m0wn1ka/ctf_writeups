# web 
## terms and conditions
- here the description is
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2df325df-8850-4309-9213-325bf57d10dc)
- this is how the endpoint is
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f833eef7-2e19-413b-9b14-fe2f8a4d3551)
- when we try to place our cursor on it it moves
- so there is frontend scirpt which stops us
- so try it in mobile
- there is a condition to stop touching as well
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/eeb99f3b-2f24-4d50-b444-133fcb854037)
- then we see there is no form to submit as well
- so the element is getted by id by the server and the corresponding function to get the flag is called
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3e207ba1-a1bd-483a-9c2b-d67a09ea1f46)
- we dont even have access to the function either
- but we can get the element by id and try to click it
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2dd3f5e8-c200-4821-8582-655bd77b7463)
- so the flag is lactf{that_button_was_definitely_not_one_of_the_terms}
- document get element by id https://www.w3schools.com/jsref/met_document_getelementbyid.asp
## flag lang --not completed
- at endpoint ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a7c010c4-81a0-4cbc-9966-415706db2a83)
- the zip file has
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7883fc67-9ed4-46f0-955c-9dd59f0ee4ec)
- on inspection
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/dd9b8939-6fea-40cc-9c35-ad2770b4194e)
- so on change of the value of country we get redirected to new
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/9c1460b7-9ee5-46c5-8618-718c59c6ddd7)
- when we try to change flag of our country there is a change in location.href i.e we reload the page
- while chainging the flag of other country we just get the needed details using fetech
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/50f87018-a5b5-4afa-b302-1c909fc0c574)
### route view
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/724c0e32-604d-49cc-95cc-eee84bbcb899)
- on the request to view we do send a cookie normlally
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/db7e9353-5422-4b5f-b3fd-b6091c64e20d)
### home path 
- on having no iso cookie it will be set to 'us'
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/90a48d46-c25a-4bcc-aa2b-5fea7714870c)
### route switch 
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/24dc9e2f-5b57-4a0d-b90c-c58a57fec3c5)
- based on the value of `to `  from the countryData country will be feteched
- if the  `country` does not have a passoword it will set the iso of the country as cookie and redirect to it self
- and if the country has passoword it will be checked against the req.cookies.passowrd  then a well the same will happend,
  set the iso as cookie 
- `Do you speak the language of the flags?` may be we need to use accept language as flag...
- `does not work`
# crypto/valentines-day ---not commpleted
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/988828e2-64ed-4174-a128-f26d52531207)
- cipher text
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c6d2ec5b-ca52-4daa-839a-ed0f8690393a)
- at line 12 we do see the flag but in encrypted format
- we are given a small part of the plain text
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/86707368-e933-46ff-b8b4-0dbb8a996501)
# rev/shattered-memories
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e1e3e8c5-955a-49a1-af69-04021832889f)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fb930fe8-1111-4918-9280-f2a29c89d6fb)
- now we use ghidra to analyse the code
- we see the main funciton
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8ccc22ff-fb79-4755-8d37-288cb5f21285)
- here we see case 5 is the win
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/07370113-6160-4a5d-abda-2b8cf5a578ec)
- we see the flag but not in order
- so we order them and get the flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f4e1f061-7935-4517-b5cc-72a0fc3339d7)
- lactf{not_what_forgive_and_forget_means}
## crypto/valentines-day
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/edc1a7e2-7d2d-4147-a4d3-c796f6c824ff)
- given cipher text is like this
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/94aeba41-c21f-4c5c-9781-08c3fd194040)
-  and this is the first line of the decoded part as given
-  ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7491ba53-2c14-4838-9184-75638ccf064e)
- veniger cipher is like  ceaser cipher but for each letter it  has different move for the lenght of the key
- here the as part of hint it was told the key length is 161
- so for each 161 chars of the cipher text the key will be repeated
- so as in the given cipher text we do see the flage but it is encrypted (can be found by {} as these are not encrypted)
- the veniger cipher only encryptes alphabets and not special symbols and numbers
- so we divide the cipher text such that we remove all non alphbet chars
- then we splice the string to reach the flag i.e [:161] then [161:161*2] like this
- we get the part where the flag lies
### part1 of code
```
cipher='''Br olzy Jnyetbdrc'g xun, V avrkkr gb sssp km frja sbv kvflsffoi Jnuc Sathrg. Wkmk gytjzyakz mj jsqvcmtoh rc bkd. Canjc kns puadlctus!

L xyw fmoxztu va tai szt, dbiazb yiff mt Zzhbo 1178 gyfyjhuzw vhtkqfy sniu eih vbsel edih tpcvftz, xcie ysnecsmge hbucqtu qt wcorr crzhg-olhm srr gkh gdsjxqh gnxxl rtr guez jewr klkkgak dx uuka nnv hmvwbj gmv glz fvyh, jueg eww oq i wuqglh Z lrigjsss ynch xun esivmpwf: "oof hvrb frtbrq it Kcmlo?"

C ltzihfvxsq ghp abqs qrfzf glvx de HN bnty gocr gr:

Eiaj zek rvocf vnriiu ob Puiza. Xegjy webrvbvrj. Frat s vgxhidm kepldrv gbq phxgv.

Ehlb'w wuhu C ixyzchlr, ilc srez foq e wxzb sdz nrbrb. Eej W und siieesx nd pvvgb zvr pooi. B fox wc nrax v pedgei aex phvqe. Hqdru pc tvvtrv, C zyoxvxsq ghq wyvbg yzgmex KEKN=/ife/lgcyr/qg/ejl:$TNXC, eej hurn mlp qowtswvqn:

wrm ~cuamyh/umlofikjayrvplzcwm.gdg | pzwj
ropgf{qvjal_dfuxaxzbk_gbq_jeci_hdt_nr_hdr_eexij}

'''
c=''''''
for i in cipher:
    if i.isalpha():
        c+=i
c1=c[:161]
c2=c[161:322]
c3=c[322:483]
c4=c[483:644]
c5=c[644:]
print(c5)
# print(c)
print(len(c5))
print("eexij" in c5)
p='''On this Valentine's day, I wanted to show my love for professor Paul Eggert. This challenge is dedicated to him. Enjoy the challenge!
'''
plain=''''''
for i in p:
    if i.isalpha():
        plain+=i
print(plain[:44])
print(c[:44])
````
- now we go to part2 of solving
- now the last part has just 44 chars 
- in p we store the plain text relvent length
- in c we store the corresponding cipher text of the same length
- we convert both of them to lower chars
- in x we store what should be decrypted
```#c=p+k
#k=c-p
#p=c-k
```
- as this is the rule we find the keys
- then using cyclic manner we get the x decrypted by the same rules
### part2 code
```
p='''OnthisValentinesdayIwantedtoshowmyloveforpro'''
c='''BrolzyJnyetbdrcgxunVavrkkrgbssspkmfrjasbvkvf'''
x='''gpzwjropgfqvjaldfuxaxzbkgbqjecihdtnrhdreexij'''
p=p.lower()
c=c.lower()
#c=p+k
#k=c-p
#p=c-k
keys=[]
for i,j in zip(p,c):
    i=ord(i)
    j=ord(j)
    k=j-i
    keys.append(k)
    # print(k,end=" ")
for a,b in zip(x,keys):
    a=ord(a)
    p=a-b
    if(p<97):
        p=123-(97-p)
    if(p>122):
        p=96+(p-122)
    print(chr(p),end=" ")

# ropgf{qvjal_dfuxaxzbk_gbq_jeci_hdt_nr_hdr_eexij}
# lactf{known_plaintext_and_were_off_to_the_races}
```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/680ad6e8-67d2-4462-b8d7-589e22faf9c9)
- we remove the whitespacces
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/44a404c3-2faa-4687-b115-c76c85ba45b2)

- we rearrange the underscores and get the flag
```
# ropgf{qvjal_dfuxaxzbk_gbq_jeci_hdt_nr_hdr_eexij}
# lactf{known_plaintext_and_were_off_to_the_races}
```
# at end
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/0978dacf-53ae-466a-a996-45ecf4fa56cd)
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/0fb74768-66ed-4b85-bc7e-18beb1803bb5)
