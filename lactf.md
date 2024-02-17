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
## flag lang
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
