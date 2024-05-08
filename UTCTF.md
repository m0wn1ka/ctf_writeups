## easy mergers v1/web
- problem
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d40d7f24-935f-445b-863b-4cd6bbaed4fc)
### recon
- it is useing as backed express
- POST http://guppy.utctf.live:8725/api/makeCompany -on creating company a application/json body is going
- the list of companies getting is like this
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f2d1fe25-3655-4515-9c06-3b79fa4dd1fb)

- it is using http1 and chunked transfer encoding ,so if there are any middle  servers and a possible request smuggling
- there is a session cookie,based on which users are identified,it is neither jwt
- the json-object so might be a serilization and deserilization issue
### random tries
- command execution/injection(in normal attributes,in session)
- session manipulation to get session of user1
- loOok into the packagae.json and find old versions
- NEW LOIN
