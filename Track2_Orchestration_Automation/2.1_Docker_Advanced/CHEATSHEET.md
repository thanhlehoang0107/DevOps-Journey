# Docker Advanced Cheatsheet

```dockerfile
# Multi-stage build
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
HEALTHCHECK CMD curl -f http://localhost/ || exit 1
```
