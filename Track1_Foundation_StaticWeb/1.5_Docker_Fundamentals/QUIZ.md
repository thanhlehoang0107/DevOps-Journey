# ❓ Quiz: Docker Fundamentals

> 20 câu hỏi về Docker.

---

### Q1: Container vs VM

Container khác VM như thế nào?

a) Container có OS riêng  
b) Container share host kernel  
c) VM nhẹ hơn container  
d) Không khác nhau  

---

### Q2: Docker Image

Docker image là gì?

a) Running container  
b) Read-only template  
c) Docker configuration  
d) Virtual machine  

---

### Q3: Dockerfile CMD

Lệnh `CMD` trong Dockerfile dùng để?

a) Run command during build  
b) Set default command khi container start  
c) Copy files  
d) Set environment  

---

### Q4: EXPOSE

`EXPOSE 80` trong Dockerfile làm gì?

a) Publish port 80  
b) Document port 80  
c) Block port 80  
d) Forward port 80  

---

### Q5: Volume

Docker volume dùng để?

a) Increase container size  
b) Persist data  
c) Network containers  
d) Build images  

---

### Q6: Port Mapping

`docker run -p 8080:80` có nghĩa gì?

a) Container 8080 maps to host 80  
b) Host 8080 maps to container 80  
c) Both ports 8080  
d) No mapping  

---

### Q7: Detached Mode

Flag `-d` trong `docker run -d` có nghĩa gì?

a) Debug mode  
b) Detached (background)  
c) Delete after run  
d) Disk mode  

---

### Q8: Docker Network

Network type default của Docker là gì?

a) host  
b) bridge  
c) none  
d) overlay  

---

### Q9: RUN vs CMD

`RUN` khác `CMD` như thế nào?

a) RUN execute at runtime, CMD at build  
b) RUN execute at build, CMD at runtime  
c) Same thing  
d) RUN for files, CMD for commands  

---

### Q10: COPY vs ADD

`COPY` khác `ADD` như thế nào?

a) Không khác  
b) ADD can extract archives and URL  
c) COPY can extract archives  
d) ADD không copy được  

---

### Q11: Layer

Mỗi instruction trong Dockerfile tạo gì?

a) Container  
b) Image layer  
c) Volume  
d) Network  

---

### Q12: Prune

`docker system prune` làm gì?

a) Delete all containers and images  
b) Remove unused data  
c) Restart Docker  
d) Update Docker  

---

### Q13: Entrypoint

`ENTRYPOINT` khác `CMD` như thế nào?

a) ENTRYPOINT can be overridden easily  
b) CMD appends to ENTRYPOINT  
c) Same thing  
d) ENTRYPOINT for files only  

---

### Q14: Multi-stage

Multi-stage build dùng để?

a) Build multiple apps  
b) Reduce final image size  
c) Run multiple containers  
d) Create multiple networks  

---

### Q15: Tag

Nếu không specify tag, default tag là gì?

a) v1  
b) default  
c) latest  
d) none  

---

### Q16: Logs

Lệnh xem logs của container running?

a) `docker logs container_name`  
b) `docker show logs`  
c) `docker container logs`  
d) a và c đều đúng  

---

### Q17: Health Check

`HEALTHCHECK` instruction dùng để?

a) Check Docker health  
b) Define container health check  
c) Check host health  
d) Monitor resources  

---

### Q18: Resource Limits

Flag nào giới hạn memory?

a) `--memory-limit`  
b) `--mem`  
c) `-m` or `--memory`  
d) `--ram`  

---

### Q19: Registry

Docker Hub là gì?

a) Docker documentation  
b) Public container registry  
c) Docker CLI  
d) Docker desktop  

---

### Q20: Context

Build context là gì?

a) Docker daemon  
b) Files sent to daemon for build  
c) Dockerfile location  
d) Environment variables  

---

## 📝 Answers

<details>
<summary>Click để xem đáp án</summary>

| Q | A | Q | A |
|---|---|---|---|
| 1 | b | 11 | b |
| 2 | b | 12 | b |
| 3 | b | 13 | b |
| 4 | b | 14 | b |
| 5 | b | 15 | c |
| 6 | b | 16 | d |
| 7 | b | 17 | b |
| 8 | b | 18 | c |
| 9 | b | 19 | b |
| 10 | b | 20 | b |

</details>

---

**[← Back to README](./README.md)**
