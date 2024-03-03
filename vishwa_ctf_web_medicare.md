## web/MediCare Pharma
```
function createAccount() {
  alert("Access Forbidden");
}

function submitForm() {
    var username = document.getElementById("uname").value;
    var password = document.getElementById("pass").value;
    var xhr = new XMLHttpRequest();
  
    xhr.onreadystatechange = function () {
      console.log('ReadyState:', xhr.readyState);
      if (xhr.readyState == XMLHttpRequest.DONE) {
        console.log('Status:', xhr.status);
        if (xhr.status == 200) {
          alert(xhr.responseText);
        } else {
          alert("Error : " + xhr.status);
        }
      }
    };
    
    xhr.open("POST", "login.php", true);
    xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
    
    var data = "username=" + encodeURIComponent(username) + "&password=" + encodeURIComponent(password);
    
    xhr.send(data);
  }
  
```
### payload --no response --500
```
';';'":"admin&&&***)(":>?'';';';''''
```

```
b';
```
gives 500


```
b';#
```
gives not error

## chekcking payloads
- username=admin'&password=root gives 500
- username=admin' 'radha&password=root 502
- username=CONCAT('foo','bar')&password=root 500
- username=admin-- &password=root no err    SELECT * FROM users WHERE username='admin-- ' and pass='root'
- username=admin/*&password=root SELECT * FROM users WHERE username='admin/*' and pass='root'
- username=1%2b1&password=root  Incorrect Username or Password
