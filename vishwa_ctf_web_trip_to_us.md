## trip to us
- on inspecitn we see
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/eadc9a73-88e4-49e3-af30-68dd15522647)
- that on clicking on click here we go to err.php
- once we go there and inspcect once agin
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/678ee06e-f46a-4bca-840e-ff766026c4be)
- we see the alt is
```
 alt="Change User agent to 'IITIAN'
```
- so we user burp suit
- so we change it and see we get 302
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/59a9b900-f297-4811-a029-dd8a1616b2ff)
- we follow redireciton
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/10e60297-f022-4323-a79d-3ee3ab5f3e40)
- we see a new endpoint
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/80fee9d6-8c63-423d-9b4c-abfe340188e5)
### try sql injection
- try admin' and abc as pass
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/4748e77b-3b5f-4c3d-b2fe-5194a2ff66d4)
- so there is a sql injection vulnerability
- admin" does not give any query err
- try admin'#
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/60af7c51-c0b5-4f3f-9d91-f5fd8ded0f5e)
VishwaCTF{y0u_g0t_th3_7r1p_t0_u5}
