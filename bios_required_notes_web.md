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
