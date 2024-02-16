## soap
- endpoint
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/09c24ca3-dd83-4381-bc6c-724768be79a9)
- as part of hint it was said to have xxe vuln
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b731a5bd-f7ed-4c1c-86a6-62b2e00c6a89)
- https://portswigger.net/web-security/xxe#exploiting-xxe-to-retrieve-files
- <!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
- and we need to refer to xxe
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7b9e8069-955d-408a-a57a-cd31b6ee2f27)
- and at the bottom we do see the flag
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/33e7fb3d-a505-44dd-8b83-9ed9fb8f4412)
- picoCTF{XML_3xtern@l_3nt1t1ty_0dcf926e}

## super serial
- here we see it have a php session id,nothin to be noted in the source code ,css,html,js
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1d1845d6-60de-4b54-b623-298ce9545c62)
- now by looking at the hints it says flag is at ../flag
- try it in browser ,but browser normalizes the path
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a272533c-645f-4d89-b335-4c86b71f8add)
- now we url encode the /
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1dd321c9-a9e4-4371-b94c-09b7e30f6836)
- and we get 403
- what if we remove the php session id ,still same forbidden
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ccc4374d-6919-4007-9bf2-e056b702f3e2)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/bfad4ecb-5bed-43b1-a4a8-c0563790eea1)
- now we try to go for index.phps
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b2bd6c63-38ed-47a7-b603-4c4bf5e26aa3)
- now authetication.php
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/717e409e-f7ba-45ac-a82b-2ebe1c792156)


# https://portswigger.net/web-security/deserialization/exploiting
