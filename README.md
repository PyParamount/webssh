## WebSSH
A simple web application to be used as an ssh client to connect to your ssh servers. It is written in Python, base on Tornado and Paramiko.

### Preview
![Login](https://github.com/huashengdun/webssh/raw/master/preview/login.png)
![Terminal](https://github.com/huashengdun/webssh/raw/master/preview/terminal.png)

### Install dependencies
```
$ pip install -r requirements.txt
```

### Run

```
$ python main.py
```

### Help

```
$ python main.py --help
```

### A config example for putting Nginx as a front web server
```
location / { 
    proxy_pass http://127.0.0.1:8888;
    proxy_http_version 1.1;
    proxy_read_timeout 300;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Real-PORT $remote_port;
} 
```

### Tips
* If you want to run it in a production server, please disable debug mode, set debug as False in settings.
* Try to use Nginx as a front web server (see config example above) and enable SSL, this will prevent your ssh credentials from being uncovered. Also afterwards the communication between your browser and the web server will be encrypted as they use secured websockets.

### About Python version
Should work from 2.7 to 3.6, but if you happen to find it does work for a specific python version, please open an issue here.
