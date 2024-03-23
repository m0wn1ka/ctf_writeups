## jail boy /web
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

  
