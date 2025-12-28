# 📖 DevOps Glossary – Từ điển thuật ngữ

---

## Giới thiệu

Tài liệu này tổng hợp các thuật ngữ thường gặp trong DevOps. Mỗi thuật ngữ được giữ nguyên tiếng Anh kèm giải thích tiếng Việt.

> 💡 **Quy tắc:** Thuật ngữ chuyên ngành **KHÔNG** được dịch sang tiếng Việt để tránh nhầm lẫn và phù hợp với tài liệu quốc tế.

---

## A

### API (Application Programming Interface)

Giao diện lập trình ứng dụng - cho phép các phần mềm giao tiếp với nhau thông qua các endpoint được định nghĩa sẵn.

### Artifact

Sản phẩm đầu ra của quá trình build (ví dụ: file `.jar`, `.war`, Docker image).

### Auto-scaling

Tự động tăng/giảm số lượng instance dựa trên tải hệ thống.

---

## B

### Bare Metal

Server vật lý, không chạy trên nền ảo hóa.

### Build

Quá trình biên dịch source code thành sản phẩm có thể chạy được.

### Blue-Green Deployment

Chiến lược deploy với 2 môi trường giống hệt nhau, cho phép chuyển đổi nhanh giữa version cũ và mới.

---

## C

### CI (Continuous Integration)

Tích hợp liên tục - Developer push code thường xuyên, hệ thống tự động build và test.

### CD (Continuous Delivery/Deployment)

- **Continuous Delivery:** Code luôn sẵn sàng để deploy (cần approve thủ công).
- **Continuous Deployment:** Tự động deploy mà không cần can thiệp.

### CIDR (Classless Inter-Domain Routing)

Ký hiệu để mô tả dải IP (ví dụ: `10.0.0.0/16` = 65,536 địa chỉ IP).

### Cluster

Nhóm các server/node làm việc cùng nhau như một hệ thống thống nhất.

### Container

Môi trường cô lập, nhẹ, chạy ứng dụng với đầy đủ dependencies. Không phải "thùng chứa"!

### ConfigMap

(Kubernetes) Object lưu trữ cấu hình dạng key-value, inject vào Pod.

---

## D

### Daemon

Tiến trình chạy nền (background process), ví dụ: Docker Daemon.

### Deployment

- (Chung) Quá trình đưa ứng dụng lên môi trường chạy thực tế.
- (Kubernetes) Object quản lý việc tạo và update Pod.

### Docker

Nền tảng containerization phổ biến nhất.

### Dockerfile

File text chứa các instruction để build Docker image.

### Docker Compose

Tool định nghĩa và chạy multi-container application bằng file YAML.

### DR (Disaster Recovery)

Kế hoạch khôi phục hệ thống khi xảy ra sự cố nghiêm trọng.

---

## E

### EC2 (Elastic Compute Cloud)

Dịch vụ máy ảo của AWS.

### EKS (Elastic Kubernetes Service)

Dịch vụ Kubernetes được quản lý bởi AWS.

### Environment Variable

Biến môi trường - lưu trữ cấu hình bên ngoài code.

---

## F

### Firewall

Tường lửa - kiểm soát traffic mạng dựa trên rules.

---

## G

### Git

Hệ thống quản lý version code phân tán.

### GitOps

Phương pháp quản lý infrastructure bằng Git repository.

---

## H

### HA (High Availability)

Tính sẵn sàng cao - hệ thống có thể hoạt động liên tục, ít downtime.

### Healthcheck

Kiểm tra định kỳ để đảm bảo service đang hoạt động bình thường.

### Helm

Package manager cho Kubernetes.

### Horizontal Scaling

Mở rộng bằng cách thêm nhiều instance/server.

---

## I

### IaC (Infrastructure as Code)

Quản lý hạ tầng bằng code (Terraform, CloudFormation...).

### IAM (Identity and Access Management)

Dịch vụ quản lý quyền truy cập của AWS.

### Image

(Docker) Template read-only để tạo container.

### Ingress

(Kubernetes) Object quản lý external access vào cluster.

---

## J

### Jenkins

Công cụ CI/CD open-source phổ biến.

---

## K

### Kubernetes (K8s)

Nền tảng orchestration container. Đọc là "ku-ber-ne-tees", viết tắt K8s (K + 8 chữ + s).

---

## L

### Load Balancer

Thiết bị/dịch vụ phân phối traffic đến nhiều server.

### Loki

Hệ thống log aggregation của Grafana Labs.

---

## M

### Microservices

Kiến trúc chia ứng dụng thành nhiều service nhỏ, độc lập.

### Monitoring

Theo dõi, giám sát hiệu năng và trạng thái hệ thống.

---

## N

### Namespace

(Kubernetes) Cách phân chia logic cluster thành nhiều môi trường ảo.

### NAT (Network Address Translation)

Dịch địa chỉ mạng - cho phép nhiều thiết bị dùng chung 1 IP public.

### NGINX

Web server và reverse proxy phổ biến.

### Node

Một máy (physical hoặc virtual) trong cluster.

---

## O

### Orchestration

Quản lý tự động vòng đời của containers (scheduling, scaling, healing...).

---

## P

### Pipeline

Chuỗi các bước tự động từ code đến production.

### Pod

(Kubernetes) Đơn vị nhỏ nhất có thể deploy, chứa 1 hoặc nhiều containers.

### Port Mapping

Ánh xạ port giữa host và container (ví dụ: `-p 8080:80`).

### Prometheus

Hệ thống monitoring và alerting open-source.

### Proxy

Trung gian giữa client và server.

### PV (Persistent Volume)

(Kubernetes) Storage resource ở cluster level.

### PVC (Persistent Volume Claim)

(Kubernetes) Yêu cầu storage từ Pod.

---

## R

### RDS (Relational Database Service)

Dịch vụ database được quản lý của AWS.

### Registry

Nơi lưu trữ Docker images (Docker Hub, ECR, GCR...).

### Replica

Bản sao của Pod/container để tăng availability.

### Reverse Proxy

Proxy đứng trước backend servers, nhận request từ client.

### Rolling Update

Cập nhật từng Pod một, không downtime.

---

## S

### S3 (Simple Storage Service)

Dịch vụ object storage của AWS.

### SAST (Static Application Security Testing)

Phân tích code tĩnh để tìm lỗ hổng bảo mật.

### Scaling

Khả năng tăng/giảm resource theo nhu cầu.

### Secret

(Kubernetes) Object lưu trữ dữ liệu nhạy cảm (password, token...).

### Security Group

(AWS) Virtual firewall cho EC2 instance.

### Service

(Kubernetes) Abstraction layer cho phép truy cập ổn định vào Pod.

### SLA (Service Level Agreement)

Cam kết về mức độ service giữa provider và customer.

### SLI (Service Level Indicator)

Metric đo lường chất lượng service.

### SLO (Service Level Objective)

Mục tiêu cụ thể cho SLI.

### SSH (Secure Shell)

Protocol để truy cập remote server an toàn.

### Subnet

Phân đoạn mạng nhỏ hơn trong VPC.

---

## T

### Terraform

Tool IaC phổ biến của HashiCorp.

### TLS/SSL

Giao thức mã hóa traffic (HTTPS).

---

## V

### Vertical Scaling

Mở rộng bằng cách tăng resource cho 1 server (CPU, RAM...).

### VM (Virtual Machine)

Máy ảo - mô phỏng hoàn chỉnh một máy tính.

### Volume

(Docker/Kubernetes) Cơ chế persist data bên ngoài container lifecycle.

### VPC (Virtual Private Cloud)

Mạng ảo riêng trên cloud.

---

## W

### Webhook

HTTP callback - tự động gọi URL khi có event xảy ra.

### Worker Node

(Kubernetes) Node chạy workload (Pod), khác với Control Plane.

### WSL (Windows Subsystem for Linux)

Cho phép chạy Linux trực tiếp trên Windows.

---

## Y

### YAML

Định dạng file cấu hình phổ biến trong DevOps (YAML Ain't Markup Language).
