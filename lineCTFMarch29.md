## solved challenges
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/19a3b566-1ce2-4a7a-aed1-de058942d86a)
## score board
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/02832408-92c7-4ef8-abe2-974e1c913be4)



# jail boy /web
- problem
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/54bdb294-23cb-4028-ac66-7de8bd490d23)
- the endpoint
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f168bc26-f61d-41d2-bb88-186ed8241f29)
- we see it is using jwt tokens from the letter e
### black box approach
- straight away as we see it has 100 points which means it is a beginner
- it mostly could be a simple jwt issue
- decode the jwt token
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/226e9283-59e8-4034-9e23-31173ebbdb6a)
- so we see it uses hs256
- so we know there exiss
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5a4f6821-9090-41ed-acec-71bb3f2fc2ab)
- so we try none algorithm in header did not work (reomve signaurue keep the dot,remove sign remove the dot) both did not wokr
- then went through this article
- https://blog.dixitaditya.com/exploiting-jwt-lack-of-signature-verification
- what if the signature is not verifed at all
- so remove the signaure but keep the dot to maintain the sturcutre of jwt
- and it works
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7f1e5387-d65b-44ce-818b-369e3024d99f)
- GET /?j=eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbiJ9.
- just changed the subject to amdin and encoded
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/9306d620-dde3-498d-b6bf-1ae07b00c548)
```
        <p>flag is <code>LINECTF{337e737f9f2594a02c5c752373212ef7} &#x1f389;</code></p>
```
### white box approach
- we are given the source code
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fc5daa89-cbec-45e2-aa25-1ec7f215a8df)
- from docker file we see it uses java
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3247fb2d-a1cb-4df3-96a0-8832f8d8167d)
- here we see the parsing of jwt token in line 29 which is the insecure line
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fa0463b9-4ba6-4565-89f5-0e2c25dc9f23)


# jalyboy-jalygirl/web
- pretty much the same as before
- but from code review here it looks like it uses asymmetric keys
- but there does not apper a alogrithm imposition during verfication
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/31f976d8-0dfb-460a-bb2d-3e73bfe3cdaf)

- so may be we can use the public key and sign ourselves as admin with it and say the algorihm uses hs256 (place alg:hs256)
- decoding the token we see it uses es256
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/99d9cddd-fc06-4893-b9db-cbe60337a1db)
- to understand edcsa https://www.youtube.com/watch?v=0NGPhAPKYv4
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3bbe8d7c-3b2b-4c44-bc77-15f65797d239)
- from this https://www.cryptomathic.com/news-events/blog/explaining-the-java-ecdsa-critical-vulnerability
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/fc974da3-b9bf-4413-a35b-c6ac683ed66c)
- and we see it is java 17
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c1f69fa6-7187-4516-8a66-2c9494a76eea)
- so the main check that r,s being zero condition is not checked in this implementation
- so now we need to bypass the signature
- https://www.linkedin.com/pulse/exploitation-psychic-signatures-cve-2022-21449-zakhar-fedotkin/
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/bd4ba188-dd89-4f1a-bfc9-f7b48b4ec81b)
- first sent this request
```
GET /?j=eyJhbGciOiJFUzI1NiJ9.eyJzdWIiOiJndWVzdCJ9._____wAAAAD__________7zm-q2nF56E87nKwvxjJVH_____AAAAAP__________vOb6racXnoTzucrC_GMlUQ HTTP/1.1
```
- same sub as guest but signature is with 0,0
- we are still guest only with this request
- now change the sub to admin
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e9e7dfca-fe43-452c-b1cd-9c23504b3c3e)
- now with this request we get the flag and login as admin
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/91fe33ce-4c53-4b24-8960-2b80c498a30f)

- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5924424c-c5ca-4edf-bb93-2c655d0dd88e)
```
           <p>flag is <code>LINECTF{abaa4d1cb9870fd25776a81bbd278932}</code> &#x1f389;</p>
```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8ffdc9c7-1d65-492b-b9ea-92f53f9a07ae)
## zipviewer-version-citizen/web --not completed
- descritpion of challenge
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/44ba8465-49f4-4d3f-9e4e-b243be908662)
- the source code
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/eb5a31ea-26c0-4f07-85fc-ccc942c54e19)
- we see it uses vapour framework which is written in swift and made my apple inc
- a little bit of proxy pass
- https://dev.to/danielkun/nginx-everything-about-proxypass-2ona
- so req to / will go to http://webapp;
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3431498f-56d9-48ea-89a2-eaaf613587c7)
- same site =lax cors cofig
- when giving username  req goes to /enter/user_input and redirct to /viewer
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/332b594c-3191-445d-835c-cde8ec35d932)
- 
