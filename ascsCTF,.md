# login/web
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/24b66484-9f48-4f9b-9ae1-f98cabd207ec)
```
const express = require('express');
const crypto = require('crypto');
const FLAG = process.env.FLAG || 'flag{this_is_a_fake_flag}';

const app = express();
app.use(express.urlencoded({ extended: true }));

const USER_DB = {
    user: {
        username: 'user', 
        password: crypto.randomBytes(32).toString('hex')
    },
    guest: {
        username: 'guest',
        password: 'guest'
    }
};

app.get('/', (req, res) => {
    res.send(`
    <html><head><title>Login</title><link rel="stylesheet" href="https://cdn.simplecss.org/simple.min.css"></head>
    <body>
    <section>
    <h1>Login</h1>
    <form action="/login" method="post">
    <input type="text" name="username" placeholder="Username" length="6" required>
    <input type="password" name="password" placeholder="Password" required>
    <button type="submit">Login</button>
    </form>
    </section>
    </body></html>
    `);
});

app.post('/login', (req, res) => {
    const { username, password } = req.body;
    if (username.length > 6) return res.send('Username is too long');

    const user = USER_DB[username];
    if (user && user.password == password) {
        if (username === 'guest') {
            res.send('Welcome, guest. You do not have permission to view the flag');
        } else {
            res.send(`Welcome, ${username}. Here is your flag: ${FLAG}`);
        }
    } else {
        res.send('Invalid username or password');
    }
});

app.listen(5000, () => {
    console.log('Server is running on port 5000');
});
```
- app.js code
### possible testings
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/6bd080ce-6bcd-4eb9-804b-40a43f3a9b53)
- the connection is kept alive for 5 seconds...
- may be somethign with this url encoded
```
app.use(express.urlencoded({ extended: true }));
```
- res.send but not return res.send
- time based attacks like it did not use andy standard way of comparison of password checking
### express.urlencoded({exteded:true})
https://www.reddit.com/r/expressjs/comments/up0qe1/why_would_i_use_expressurlencodedextended_false/
- may be it will not work
- as the lenght of username is limited
- https://www.npmjs.com/package/qs#readme
- and we access the object based on username
