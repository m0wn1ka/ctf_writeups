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
