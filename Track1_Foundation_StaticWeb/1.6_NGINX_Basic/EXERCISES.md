# 💪 Exercises: NGINX Basic

> Bài tập tự luyện NGINX.

---

## Exercise 1: Static Site ⭐

1. Cài đặt NGINX
2. Tạo HTML page tại `/var/www/mysite`
3. Viết config để serve site
4. Enable site và reload NGINX
5. Test với curl

---

## Exercise 2: Virtual Hosts ⭐⭐

Setup 2 virtual hosts:

- `site1.local` → `/var/www/site1`
- `site2.local` → `/var/www/site2`

Test bằng cách modify `/etc/hosts`.

---

## Exercise 3: Reverse Proxy ⭐⭐

1. Run Node.js app on port 3000
2. Configure NGINX reverse proxy
3. Forward requests từ port 80 → 3000
4. Add proxy headers
5. Test end-to-end

---

## Exercise 4: Load Balancing ⭐⭐⭐

1. Run 3 backend instances (port 3001, 3002, 3003)
2. Configure upstream với round-robin
3. Add health checks
4. Test load distribution
5. Try weighted balancing

---

## Exercise 5: SSL/HTTPS ⭐⭐⭐

1. Generate self-signed certificate
2. Configure HTTPS server block
3. Redirect HTTP → HTTPS
4. Add security headers
5. Test với browser

---

## Exercise 6: Caching & Optimization ⭐⭐

Configure:

- Gzip compression
- Browser caching (cache-control headers)
- Static file caching
- Connection keepalive

Measure performance before/after.

---

## 📝 Checklist

- [ ] Exercise 1: Static Site
- [ ] Exercise 2: Virtual Hosts
- [ ] Exercise 3: Reverse Proxy
- [ ] Exercise 4: Load Balancing
- [ ] Exercise 5: SSL/HTTPS
- [ ] Exercise 6: Caching

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
