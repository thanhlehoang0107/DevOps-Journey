# NGINX Cheatsheet

```nginx
server {
    listen 80;
    server_name localhost;
    root /usr/share/nginx/html;
    index index.html;
}
```

```bash
nginx -t          # Test config
nginx -s reload   # Reload
```
