# web 
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