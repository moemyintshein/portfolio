# portfolio


## To start application

- git clone https://github.com/moemyintshein/portfolio.git
- pytho3 -m venv venv
- source venv/bin/activate
- pip install -r requirements.txt
- gunicorn -w 4 app:app    (This will listen on port 8000)


## To use Nginx proxy

- vim /etc/nginx/sites-available/portfollio
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
- sudo systemctl restart nginx
