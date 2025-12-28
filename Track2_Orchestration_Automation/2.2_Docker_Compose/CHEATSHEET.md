# Docker Compose Cheatsheet

```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "80:80"
  db:
    image: postgres:15
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:
```
