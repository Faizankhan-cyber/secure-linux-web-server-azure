# Commands Used

## Update Server

```bash
sudo apt update
sudo apt upgrade -y
```

## Install Nginx

```bash
sudo apt install nginx -y
```

## Enable Nginx

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

## Check Status

```bash
sudo systemctl status nginx
```

## Verify Port 80

```bash
sudo ss -tulpn | grep :80
```

## Test Nginx

```bash
curl localhost
```

## Backup Default Page

```bash
sudo mv index.nginx-debian.html index.nginx-debian.html.backup
```

## Replace Website

```bash
sudo mv ~/index.html /var/www/html/index.html
```

## Restart Nginx

```bash
sudo systemctl restart nginx
```