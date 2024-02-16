## GET aHEAD
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/aae4106d-5cdf-4f58-bfeb-9f0d612f1318)
- here we see on click red we see a get request
- on  choosing blue we see a post request
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
- the name of challenge is ahead so we can try to send a head request
- https://reqbin.com/req/c-tmyvmbgu/curl-head-request-example
```
:\tmp> curl 'http://mercury.picoctf.net:28916/index.php' -I      
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}
Content-type: text/html; charset=UTF-8

                                                                                                                                                                       
C:\tmp> curl 'http://mercury.picoctf.net:28916/index.php' --head
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}
Content-type: text/html; charset=UTF-8

         
```
## cookies
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1aad8b32-d624-4219-9d74-17c91f031736)
- try the cookie snickerdoodle as it appears there
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3ce99923-cfe7-4e83-9ce8-c9463c4f625d)
- we see as part of cookie there is a cookie with value 0
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/dab7ce44-c64d-4d95-8f19-c5064ab1d458)
- we try to send cookie as 1 ...
-![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/47fb7050-669d-4440-86b9-4f7400afc5fb)
- at one point 18 we get the flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5ae1de03-9f49-4849-a5bd-684c33027cf0)
## inspector
- we open the inspector dev tools
-![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fa080885-6c8f-4879-b9ae-1afc98abf3c4)
- picoCTF{tru3_d3 ---part 1
- in css we find the part 2
-![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/cadafb9d-4a4a-4ac0-b61b-bb8e7d300fcd)
- t3ct1ve_0r_ju5t
- in js file we find the last part
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/642538f6-8c14-4a43-bdfa-acf802b39263)
-  _lucky?832b0699}
-  so flag is picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?832b0699}

