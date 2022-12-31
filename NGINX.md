# Install NGINX Ubuntu/Debian
* sudo apt update
* sudo apt install nginx

## NGINX Reverse Proxy
location / {
    proxy_pass http://localhost:8000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    }
### Delete script 
try_files $uri $uri/ =404;

## Limit Request per menit (10req/mnt or 1req/6s)
limit_req_zone $binary_remote_addr zone=one:10m rate=10r/m;
in blok location / {
    limit_req zone=one;
}

## Restart NGINX
sudo systemctl restart nginx
sudo service nginx restart
sudo /etc/init.d/nginx restart

## Opsional
Install Node with nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
exit
node --version
