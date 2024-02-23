## web/empty execution --not completed
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b816f86c-fa58-4187-b741-22e4eed5159f)
### docker file
```
FROM python:alpine3.19

WORKDIR /usr/src/app

RUN pip install flask

COPY empty_execution.py .
RUN chmod 665 ./empty_execution.py

COPY flag.txt .
RUN chmod 664 ./flag.txt

RUN adduser -D ctf 

RUN chown -R root:ctf $(pwd) && \
    chmod -R 650 $(pwd) && \
    chown -R root:ctf /home/ctf/ && \
    chmod -R 650 /home/ctf

RUN mkdir ./executables

USER ctf

EXPOSE 80

CMD ["python", "empty_execution.py"]
```
- file permissions on flag 664 https://linuxize.com/post/what-does-chmod-777-mean/
- https://www.w3schools.com/python/ref_os_access.asp
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/dd5ecaa3-a1a8-464f-8f23-0ccbd91ff627)
