## endpoint
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fac1ac04-40a8-4a61-8f1e-550cdce4ffdb)
- we upload the images and they will be shown
- on openign the image we see a share button
- on clicking the share button we see a post request has been sent
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8b43eb1c-c2e9-4bef-a2df-8e4eb5cd12ed)
- the curl req is
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ef8cc647-33d5-4968-b237-0b17a1abc261)
- the image name is not changed so we can try path traversal and see etc
- in the docker file we do see env variable as flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/6becda1c-04d8-41ea-87f7-d0a63c814b66)
## absolute urls for fetching images
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/aa09af89-7bf0-40fa-8d57-5f7e64858844)
- we can use absoulte urls ot fetch images
- on just giving a parmeter  with  name 'f'we get a  alert box
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7101a53f-f1d6-43cc-ad98-0a27e6b2380a)
- we can load a image with this f parameter
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d3de108d-9428-4dde-a7f8-ca119d8db2b9)
- the loading of image does allow path traversal as here we used ../
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/0f480569-5fda-4d62-8c8c-afabc97940fa)
```
https://ch1698138049.ch.eng.run/?f=https://radham0wn1ka.github.io/..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2Fassets%2Fimg/avatar.jpg
```
for this url it is giving   ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c2b2280c-c386-4eea-a153-97ca82a1ee6d)
- but if we try the same url in plain it gives 400
- ```
  https://radham0wn1ka.github.io/..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2Fassets%2Fimg/avatar.jpg
  ```
  ## source code
  - ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c2bf79cc-9505-401c-b3ff-de61fb4775cc)
- we see this printflag function writes the flag to public/random_uui/flag.txt
- the random uuid is mostyl unpredictable*
- so as soon as the server starts the flag is written ther
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/996bfabc-7546-48d6-8b99-e3f1a16dc8ea)
  
## ezv8/tempfile --not completed

https://docs.python.org/3/library/tempfile.html#tempfile.mktemp
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e482de54-71bc-4ea4-843c-2c431faefde0)
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/386ebae0-5ed6-4e08-9743-d6f10dd64d16)
