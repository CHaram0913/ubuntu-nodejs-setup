# Instructions

```bash
# Initialization
sudo apt-get upgrade
sudo apt-get update

# Get Essential Packages
sudo apt-get install -y build-essential

# Install nodeJS
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install pm2
sudo npm i -g pm2

# Install nginx
sudo apt-get install nginx
sudo ufw allow 'Nginx HTTP/S'
sudo ufw status

# Install mongoDB
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
sudo apt-get update
sudo apt-get install -y mongodb-org
sudo systemctl start mongod
sudo systemctl status mongod

# Install redis
sudo apt-get install redis-server
sudo systemctl restart redis-server.service
sudo systemctl enable redis-server.service

# Install git
apt-get install git-core
```

# Nginx Configurations

```bash
## Files

# nginx configuration directory
/etc/nginx

# main nginx configuration file
/etc/nginx/nginx.conf

# sites available
/etc/nginx/sites-available

# sites enabled
/etc/nginx/sites-enabled

# snippets
/etc/nginx/snippets

# logs
/var/log/nginx/access.log
/var/log/nginx/error.log

## default config (sites-available/default)

...
    location / {
        proxy_pass http://localhost:port;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
...
```