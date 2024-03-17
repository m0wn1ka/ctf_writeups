## ez v2 --not completed
- question
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/091f07ae-16a8-4286-88f9-f3d08ce4925b)

- here access control allow origni is *
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/0b9abc7e-77db-4bcd-acec-1c2367a87235)
- flag is at a random place as can be seen by /dev/random
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e060deba-06a5-4755-9488-fe1e4d85259d)
## url down --not complted
- qustin ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7d1beb40-c692-4aa2-ae93-a9028d53dd0b)
- for any given url it checks whetehr the site is workign or not
- it accepts even webhook urls(https://webhook.site/2080eca9-c0a6-441b-b350-b870fd7acb01) and github(radham0wn1ka.github.io/
- it is not accepting a http://
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8d7dc75e-f91a-4887-a351-b800f780264d)
- for this kind of urls /post/check it gives a 500 https://abc/pdokjfkdl
- 
## one key to rule them all --not completed
```
[program:sshd]
command=/usr/sbin/sshd -D -o "Port=2222" -o "PubkeyAcceptedKeyTypes=ssh-ed25519" -o "AllowTcpForwarding=no" -o "PasswordAuthentication=no" -o "PrintMotd=no
```
so we see ssh is runnign and no pass

## no excueses
- decriptin ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3932812c-3f5e-47a7-99fa-652fdea552f5)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/4d708d78-3713-45e5-be80-61de7c928880)
<i><b>abc</i>dddd<<        nteresting to hear that you can't solve this challenge because abc
<i><b>abc</i>dddd<<>       Interesting to hear that you can't solve this challenge because abcdddd<<>! We hope you will solve it in the end!
```

Interesting to hear that you can't solve this challenge because bcd
dddee

ff

hi
theere!
We hope you will solve it in the end!
```
- bcd<br/>dddee</p>ff</p><pre>hi</br>theere
