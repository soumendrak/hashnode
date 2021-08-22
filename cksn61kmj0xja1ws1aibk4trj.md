## Run Nginx with Flask in Windows OS

It's hard to get a one-stop article that contains all the information to implement these in Windows.  
Nginx is used as a load balancer, with its reverse proxy server.

![Design diagram of the set up](https://cdn.hashnode.com/res/hashnode/image/upload/v1629634630291/ija5NZR2t.png)
Design diagram of the set-up 

## Nginx config

The upstream servers where the incoming requests will be redirected need to be mentioned like below:

```yml
upstream backend {
    server <IP1>:<port1>;
    server <IP2>:<port2>;
    server <IP3>:<port3>;
}
```
You can add as many servers as you like depending on the load. It's recommended the upstream servers need to be in separate machines. However the same IP also can be mentioned.

## Configuring HTTPS changes

Nginx server can be SSL supported. This is a sample code.

``` yml
    upstream backend {
        server 127.0.0.1:8020;
        server 127.0.0.1:8021;
        server 127.0.0.1:8022;
    }
```
```yaml
    # HTTPS server
    server {
       listen       8019 ssl;
       server_name  11.222.33.444;
    
       ssl_certificate      "<certificate.pem file absolute path>";
       ssl_certificate_key  "<certificate_key.pem file absolute path>";
       ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

       ssl_session_cache    shared:SSL:1m;
       ssl_session_timeout  5m;

       ssl_ciphers  HIGH:!aNULL:!MD5;
       ssl_prefer_server_ciphers  on;

       location / {
           root   html;
           proxy_pass http://backend/;
       }
    }
```
The WSGI server with `Cherrypy` and `Flask`

``` python
from flask import Flask
from cheroot.wsgi import Server as WSGIServer

# sample app with flask
app = Flask(__name__)

"""
Processes with app
"""

server = WSGIServer(bind_addr=(<IP Address>, int(<port>)), wsgi_app=app, numthreads=100)
try:
    server.start()
except KeyboardInterrupt:
    server.stop()
```


You can follow this link to run Nginx as a service in windows.
Here the app from Flask is used to route the API URLs we get as HTTP requests. As Flask server is highly recommended to not use in production server, Cherrypy is doing the purpose here.