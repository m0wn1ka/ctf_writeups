## delicious/web
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/3e9f8dd5-83f6-4628-a695-48c51d3ac474)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/05b59a96-d01e-4cad-aa0e-1976ce365a8c)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/4c7fa682-8842-4712-a3d4-035ab27fad5d)
- shaktictf{heyo_beginnerr_you_got_the_flag}


## find the flag/web
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/037ac7b7-e6f4-4857-9c00-fcafc6731448)
- os.popen https://www.tutorialspoint.com/python/os_popen.htm
- find cmd resource https://www.geeksforgeeks.org/find-command-in-linux-with-examples/
- find cmd usage
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7341fe59-e430-4b96-b774-ef2b355f8e99)
- we try to test in cmd
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e9594348-1367-4a0a-a086-4d392b7a4e1d)
- we try to test on the website
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b450ab9f-c1f7-4d84-9ec3-9ed7a57aae7c)
- we try in cmd
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/38a28775-d0d6-438f-aea6-9ee6cc73ca4a)
```
import os

from flask import Flask, request, render_template

app = Flask(__name__)

@app.get('/')
def index():
    test = request.args.get('test', None)
    if test is None:
        return render_template('index.html')

    command = f"find {test}"

    try:
        output = os.popen(command).read()

    except Exception as e:
        output = f"Error: {str(e)}"

    return render_template('index.html', output=output)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

```
- we try in website
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ec1ea4ce-f899-450d-b3ab-618709fa7e1c)
- shaktictf{finally_you found_the_flag_hehehheh!}
-
## notes v1/web
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c4276ffe-1d31-4c0f-9837-49a505d9c806)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a7c3a68f-9420-4ac4-a8e2-01199e1ccdce)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/d6800361-de4f-4516-9d40-6b3f1e54dd97)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a67729dc-497c-4254-a9bf-b28d04e702eb)
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/2dba1024-4e19-4dc1-a666-8a4c240d5032)
- create a note1
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7e5fad27-3a2d-4f41-b384-167a169ff980)
- on decoding jwt1
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/f71bd88b-0439-4d19-8766-e7f5b1c24b7a)
- see the edit notes feature
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/6485e38b-710b-4da6-804b-131414dfb3c4)
### source code review
- we see flag is in flag.txt file and being copied
- 





