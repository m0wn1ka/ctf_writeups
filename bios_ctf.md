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


# required notes --not completted 


## source code
- flag is in environment variable
- flag is fetched and written to notes/random_location.json
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/752388bf-6570-4fdc-bfda-4955efd0efd0)
- there is a funciton/middleware `restrictToLocalhost` it fetche req.connection.remoteAddress and matches it with 127.0.0.1 ,only if
   satisfies it calls the next(),else access denied with 403
- https://stackabuse.com/bytes/how-to-get-a-users-ip-address-in-express-js/
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/bb052d25-a64c-4b6b-8b14-b6162ea8cbd6)
- so the proxy address will be forwarded
- https://nir-choubey-2011.medium.com/split-second-writeup-nullcon-hackim-ctf-2020-96426070cb72 this says by req going through burp we get 127.0.0.1
- - https://www.npmjs.com/package/glob
  ## generate note id
  - create a random id and return
  ## location
  - at /notes/random_id.json ---flag
  - at /notes/Healthcheck.json --{title:healthchck,contnet:success}

## restrict to localhost middleware function
- check for 0. address and calls next() on validation
## cleanserver function
- delete require.cache - a place where the required modules are cached
## path /search
- uses restrict to localhost middleware
### get /search:noteId
- noteid=req.param.noteid
- // the main glob() and globSync() resolve/return array of filenames
- notes=glob.sync(notes/noteid)
- if there are some notes,it checks the access
- https://nodejs.org/api/fs.html#fsaccesssyncpath-mode
- we see ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ece179c4-b2c9-40ef-a0ad-39c3d43081e3)
- Flag indicating that the file is visible to the calling process. This is useful for determining if a file exists,
  but says nothing about rwx permissions. Default if no mode is specified.
- so if file does exist we get message notefound
- 
## path GET /delte
- a call to clean server funciton
- res.send(delted successufllu)

## path /customise
### get
- render customize template
### post
- base on req.body it changes the setting.proto
- this file is again used in create post request
## path /create
### get /craete
- render create
### post /create
- checks whetehr the post request to creat a note is accouding to the schema or not
- then it writes the data to /notes/random_id
## path /view:noteid
- note=resolve(notes/req.param.noteid)
```
pp.get('/view/:noteId', (req, res) => {
  const noteId = req.params.noteId;

  try {
    let note=require.resolve(`./notes/${noteId}`);
    if(!note.endsWith(".json")){
      return res.status(500).json({ Message: 'Internal Server Error' });
    }

    let noteData = require(`./notes/${noteId}`);
    for (var key in module.constructor._pathCache) {
      if (key.startsWith("./notes/"+noteId)){
        if (!module.constructor._pathCache[key].endsWith(noteId+".json")){
          if (noteId===healthCheckId){
            cleanserver();
          }
          delete module.constructor._pathCache[key];
          return res.status(500).json({ Message: 'Internal Server Error' });
        }
      }
    }
    if(req.query.temp !== undefined){
      fs.unlink(`./notes/${noteId}.json`, (unlinkError) => {
        if (unlinkError) {
          console.error('File missing');
        }
        noteList=noteList.filter((value)=>value!=noteId);
      });
    }
    return res.render('view', { noteData });

  } catch (error) {
    console.log(error)
    return res.status(500).json({ Message: 'Internal Server Error' });
  }
});
```
here  while resovleing the require.resovle() there is not sanitation ,may be path traversal and load the whole /notes and see the cache...
- 

##
 ...
 - https://ch1598141041.ch.eng.run/view/Healthcheck
 - for this path the response is
 -  ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/30f76818-18f0-4f16-a5fa-ddb6e6132a8b)

## way1
```
 app.get('/view/:noteId', (req, res) => {
  const noteId = req.params.noteId;

  try {
    let note=require.resolve(`./notes/${noteId}`);
    if(!note.endsWith(".json")){
      return res.status(500).json({ Message: 'Internal Server Error' });
    }

    let noteData = require(`./notes/${noteId}`);
```
- here we can try to requie the parent direcory and see the cache to get the flag ,as flag is in /notes
## way2
- our input is in json formate so there can be some desrilizaion issues
## way3
- while accessing the created note we access url/view/id
- so all we need to find is correct id
- bruteforcing is not the intended way
- what we can do is
```
app.get('/search/:noteId', (req, res) => {
  const noteId = req.params.noteId;
  const notes=glob.sync(`./notes/${noteId}*`);
  if(notes.length === 0){
    return res.json({Message: "Not found"});
  }
  else{
    try{
      fs.accessSync(`./notes/${noteId}.json`);
      return res.json({Message: "Note found"});
    }
    catch(err){
      return res.status(500).json({ Message: 'Internal server error' });
    }
  }

})
```
- here we use search method
```
 const notes=glob.sync(`./notes/${noteId}*`);
```
- our noteid is directly appended so we can give nothing
- so if we bypass the remote address check we can find all the files in the notes folder
- but the output is whether there is a msg or not
#### needed code
- req1:bypass remote address check
- try from a-z* when ther is msg of message found we go and tryx(a-z)*
- this loop run through the lenght of id which is 16
### ssrf
- so we need to do ssrf
- it is mostly similart to this https://infosecwriteups.com/nodejs-ssrf-by-response-splitting-asis-ctf-finals-2018-proxy-proxy-question-walkthrough-9a2424923501
- option1-request splitting
- option2- https://huntr.com/bounties/505a3d39-2723-4a06-b1f7-9b2d133c92e1/ -use @


