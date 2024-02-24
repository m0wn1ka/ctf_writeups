## web/it_is_okay --not completed
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b05bdca3-b437-411f-9ce7-63a9f57152c2)
- we give a team name it creates an instace
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e7bedabd-ebb7-43b6-832b-4dc70a03efb2)
- we login with the given password and name
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f34900d0-2cde-4e81-8a4d-8c368fc9e103)
- to the url we are supposed to send a url and it will try to fetch it
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/126ce412-ef00-4243-be23-c5dd3c210a19)
- if we goole address we get goole ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/aa4b2d89-7172-4aa8-b001-0ec8094bdde2)
- if we get directyl goole
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/bee2e7b1-5c39-41e8-a438-e8da7021b933)
- if we get google from this url
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3ec92e40-92ba-42b4-9c50-2c909c8e447c)
- it will fetch the content and display no iframes
- when we try to fetch 127.0.0.1
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/14a7ae9c-a086-41f0-8835-3bde137ccf90)
- http connection pool https://devblogs.microsoft.com/premier-developer/the-art-of-http-connection-pooling-how-to-optimize-your-connections-for-peak-performance/
- on giving a webhook site url we do see the user agent is python-requests
  - ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/145c9f1e-107f-4cf5-8e2f-b26b1e16bd0a)
- we can run alert by having a alert html in a webhook and make the site visit our webhook
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/39dc3ecc-dfde-4e79-993a-94189c1aebc2)

