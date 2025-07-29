# portfolio


## To start application

- git clone https://github.com/moemyintshein/portfolio.git
- pytho3 -m venv venv
- source venv/bin/activate
- pip install -r requirements.txt
- gunicorn -w 4 app:app    (This will listen on port 8000)


## To Configure Nginx

- vim /etc/nginx/sites-available/portfollio

For Non-SSL
```
server {
    listen 80;
    server_name your_domain.com;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

For SSL
```
server {
    listen 443;
    ssl    on;
    ssl_certificate    /etc/ssl/your_domain.pem;
    ssl_certificate_key    /etc/ssl/your_domain.key;
    server_name your_domain.com;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
- sudo systemctl restart nginx
