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
## scavanger hunt
- picoCTF{t from source code
- h4ts_4_l0t_0f_pl4c
- these are from ctrl+u,css,js=>robots.txt
- then we need to go to .htaccess
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ecb45bf4-9d0c-4737-8efd-7ff6958d76a3)
-  Part 4: 3s_2_lO0k_74cceb07}
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b4799a4f-4013-4099-bc52-f03c1c7bb167)
- picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_74cceb07}
## where are robots
- https://jupiter.challenges.picoctf.org/problem/36474/robots.txt on this we get
```
User-agent: *
Disallow: /477ce.html
```
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c7b00782-b4c2-4468-9de0-0c628655fb84)
## factory login
- we see admin cookie is false
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ec4879cc-8566-4601-bf4a-c6072f2ecaf6)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/48d94be6-1bda-4fb0-b998-0a353c5517ac)
- now change the cookie
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/df263465-a349-4412-b1a7-ca4c8916d7ce)
- picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}

## it is my birthday
- here we need to submit 2 files with same md5
- so we try to find the collison in md5
- from here we get the 2 files https://www.mscs.dal.ca/~selinger/md5collision/
- the file  extension is checked so we change it to pdf
- which leads to ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d69010d7-9d19-404e-9d0e-1b94714c350c)
- picoCTF{c0ngr4ts_u_r_1nv1t3d_aebcbf39}

## who are you
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/6eea86f4-d868-4505-b660-d84138d0d9d2)
- so now we change the user agent
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d1ebc698-fa63-42ff-8746-29c5f80f316c)
- <h3 style="color:red">I don&#39;t trust users visiting from another site.</h3>
- so now we change/add the referer header
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/974bc9ad-7a5f-4b84-a60f-53b7532cbb41)
- now we get <h3 style="color:red">Sorry, this site only worked in 2018.</h3>
- now we add a date header backing to 2018
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f54dd569-5341-46ea-a14b-84276c6c9d57)
- <h3 style="color:red">I don&#39;t trust users who can be tracked.</h3>
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/59155011-91c1-40d2-9581-6d4d9e0868b6)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/96739913-3ed0-473a-a604-718440afa724)
- now it says it want people from switzerland
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For we see this header is the key here
- we try to use a swedish ip from google
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/cd90b54e-c79b-4e4f-8e0b-7ac83c346da9)
- <h3 style="color:red">You&#39;re in Sweden but you don&#39;t speak Swedish?</h3>
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1a924b69-8d16-41c8-9e5b-0b747c10d6d9)
- from this site we do see sv
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/48bb490d-4e97-4405-94c7-b9260acf9b8f)
- now to the list of accept languages we add sv
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f59fa3b9-00d1-4b45-a8a3-b50cd4fd5892)
- picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_79e451a7}
## login
- the description is
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/56dcfd13-6dcb-4ae4-8309-836ffaf3afd5)
- this is the site
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2920bf56-c5cd-47bb-a457-91de806e9b87)
- we look at the source code and unminify it
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/bf9ef6a2-c75b-4384-ad2e-eda9992ce4f5)
- there we see atob of password is the flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ba55f80c-4c1d-4301-8d2d-434a42c544c6)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7cf1d948-886a-42a1-821e-d0fae27db7aa)
- picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}


## on includes
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/0e20f7f2-35a0-4d88-ba60-c1990929424c)
- in styles.css ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d7387842-6630-48e6-9e36-8756a1ced14e)
- picoCTF{1nclu51v17y_1of2_
- and is script.js ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/031bc0ae-dd92-4b75-bcb6-ddb248174d52)
- picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}
## inspect html
- here on inspection we get the flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/995147d6-33ad-4dbf-a08a-2d128d14f5ed)
## local authority
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/403fcd92-89e1-4591-aad1-11d1abb783fb)
- on followin along the threads
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ccd1f969-6f7a-4266-84fe-6e2d4bb2b98e)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/87f50a6b-12b9-4558-b231-3ec2383f0198)
-  picoCTF{j5_15_7r4n5p4r3n7_a8788e61}


## search source
- here in one of the css file we get the flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d8371dfd-f19a-44f1-b922-37864fa0c711)
- picoCTF{1nsp3ti0n_0f_w3bpag3s_ec95fa49}

## findme 
- here we submit the username and passowrd and we see a coulple of splashes of redirections
- we try to see them one after another and we see base64 encoding =
- we decode to see the interesingness
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/49bdfc23-54c1-48cf-8de3-813ffa1d0443)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b58b3c0e-fcde-4985-aa8a-afcd688d3397)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8ccba068-dcc3-4592-ad07-f2a0b843638b)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c1e57c71-7b6b-4a7a-8cf3-043a0fbdb64c)
- picoCTF{proxies_all_the_way_d1c0b112}


## match the regex
- paaaaaF!
- picoCTF{succ3ssfully_matchtheregex_2375af79}
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3ff07eb7-ab50-4c78-9b8c-a02f5c3a0ed8)
- on looking at the source code
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2d44d29e-032c-47e6-8749-3f2310f5be41)
- we see we need to start with p and have 5 chars then end with F!
