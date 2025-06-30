# Kiến Thức Tổng Hợp: Git, Frameworks, Clean Architecture, DDD & Làm Việc Nhóm

## 1. Kiến Thức Git / Framework Đã Dùng và Tìm Hiểu

### Git

#### 1.1. Các khái niệm quan trọng

* **Git** là hệ thống quản lý phiên bản phân tán, giúp theo dõi lịch sử thay đổi của mã nguồn.
* **Repository (repo)**: nơi lưu trữ mã nguồn, có thể là local hoặc remote (GitHub, GitLab,...).
* **Commit**: bản ghi thay đổi.
* **Branch**: nhánh phát triển song song.

#### 1.2. Các lệnh Git phổ biến

* Khởi tạo và sao chép:

  * `git init`: Khởi tạo repo local.
  * `git clone <url>`: Tải repo từ remote.
* Trạng thái và thay đổi:

  * `git status`: Kiểm tra trạng thái file.
  * `git add <file>`: Thêm file vào staging area.
  * `git commit -m "message"`: Ghi thay đổi với message.
* Làm việc với nhánh:

  * `git branch`: Liệt kê các nhánh.
  * `git checkout -b <branch>`: Tạo và chuyển nhánh.
  * `git merge <branch>`: Gộp nhánh.
  * `git rebase <branch>`: Rebase nhánh.
* Push/Pull:

  * `git push`: Đẩy code lên remote.
  * `git pull`: Lấy và merge code từ remote.

#### 1.3. Nâng cao

* `git stash`: Lưu tạm thay đổi.
* `git reset`, `git revert`: Quay lại các commit cũ.
* `git log`, `git reflog`: Xem lịch sử commit.
* `git cherry-pick`: Lấy 1 commit từ nhánh khác.

#### 1.4. Best Practices

* Đặt tên nhánh rõ ràng: `feature/login`, `bugfix/fix-login-error`
* Commit message theo chuẩn:

  * `feat:` thêm tính năng
  * `fix:` sửa lỗi
  * `refactor:`, `test:`, `docs:`, `chore:`...
* Tránh commit file không cần thiết (node\_modules, .env,...)
* Luôn cập nhật `main` trước khi merge bằng `pull` hoặc `rebase`

---

### Frameworks/Tools đã dùng

#### 1.5. Backend

* **NestJS**:

  * Framework xây dựng trên Node.js.
  * Hỗ trợ Dependency Injection, Module hóa.
  * Hỗ trợ REST API, GraphQL, WebSockets.
  * Kết hợp tốt với CQRS, EventBus, Testing, Swagger.

* **Express.js**:

  * Web framework tối giản.
  * Dùng trong middleware, cấu hình route đơn giản.

#### 1.6. ORM / Database

* **TypeORM**:

  * Mapping dữ liệu giữa class và bảng DB.
  * Hỗ trợ cả SQL và NoSQL (MySQL, Postgres,...)

* **Prisma**:

  * ORM hiện đại, dễ viết query.
  * Tự động generate type và schema.

#### 1.7. Frontend

* **ReactJS**:

  * Thư viện UI phổ biến.
  * Component-based.
  * Hỗ trợ state management bằng Redux, Context API.

* **Next.js**:

  * Framework React hỗ trợ SSR/SSG.
  * Phù hợp SEO, tạo page nhanh.

#### 1.8. Authentication & Security

* **JWT (JSON Web Token)**:

  * Ký và xác thực request.
* **Passport.js**:

  * Hỗ trợ nhiều chiến lược auth: local, Google, Facebook,...
* **CSRF Token**:

  * Bảo vệ khỏi tấn công giả mạo request.

#### 1.9. Testing

* **Jest**: framework test phổ biến
* **@nestjs/testing**: hỗ trợ test module, service trong NestJS

#### 1.10. Docker

* Viết `Dockerfile`, `docker-compose.yml`
* Các lệnh cơ bản:

  * `docker ps`, `docker build`, `docker run`, `docker stop`
* Tạo môi trường dev/production độc lập

---

## 2. Cách Thức Làm Việc Nhóm

### 2.1. Giao tiếp & quy trình làm việc

* **Daily Standup**: báo cáo tiến độ hằng ngày
* **Retrospective**: rút kinh nghiệm sau mỗi sprint
* **Code Review**: yêu cầu mọi PR đều được review kỹ
* **Giao tiếp hiệu quả**: rõ ràng, văn minh, không đổ lỗi

### 2.2. Task Management

* **Trello / Jira**: chia task theo column (To do, In progress, Done)
* **Task gắn rõ deadline, assignee, priority**
* **User Story / Acceptance Criteria**

### 2.3. Version Control

* Không commit vào `main` trực tiếp
* Sử dụng nhánh theo feature và tạo pull request
* Gắn link task vào mô tả PR để trace

### 2.4. DevOps / CI-CD

* Thiết lập pipeline với GitHub Actions, GitLab CI,...
* Các bước phổ biến:

  * Check lint
  * Run unit test
  * Build và deploy staging

### 2.5. Các công cụ hỗ trợ

* **Slack / Discord**: giao tiếp nhóm
* **Notion / Confluence**: tài liệu dự án
* **Postman**: test API

---

## 3. Clean Architecture & Domain-Driven Design (DDD)

### 3.1. Clean Architecture

#### Tầng và chức năng:

1. **Entities**:

   * Domain objects, rule cốt lõi
   * Không phụ thuộc framework hay DB

2. **Use Cases / Application Layer**:

   * Logic cụ thể cho từng nghiệp vụ
   * Giao tiếp với Entities và gọi các repo

3. **Interface Adapters**:

   * Chuyển đổi dữ liệu qua lại giữa format phù hợp UI/DB
   * Controllers, Presenters, DTOs

4. **Frameworks & Drivers**:

   * DB, UI, REST Framework,...
   * "Biết tất cả", nhưng không chứa logic nghiệp vụ

#### Ưu điểm:

* Tách biệt rõ ràng
* Dễ test với mock
* Dễ mở rộng

#### Nhược điểm:

* Cồng kềnh cho dự án nhỏ
* Tốn effort setup ban đầu

### 3.2. Domain-Driven Design (DDD)

#### Tư tưởng:

* Mô hình hóa phần mềm xoay quanh logic nghiệp vụ
* Áp dụng Ubiquitous Language cho đồng nhất

#### Thành phần:

* **Bounded Context**: giới hạn phạm vi nghiệp vụ (Order, Payment,...)
* **Entity**: đối tượng có identity
* **Value Object**: không có identity, chỉ chứa data
* **Aggregate**: tập hợp các Entity/VO thống nhất
* **Repository**: interface lưu trữ, query aggregate
* **Factory**: tạo Aggregate

#### Ưu điểm:

* Mã nguồn phản ánh đúng nghiệp vụ
* Phân chia context rõ ràng, dễ maintain
* Hỗ trợ microservices tốt

#### Khi nào nên dùng:

* Nghiệp vụ phức tạp, hay thay đổi
* Dự án dài hạn
* Microservices

#### Không nên dùng:

* Dự án MVP, ngắn hạn
* Yêu cầu build nhanh

### 3.3. Clean Architecture vs DDD

* **Clean Architecture** là cấu trúc tầng kỹ thuật.
* **DDD** là phương pháp tổ chức business logic.
* Cả hai kết hợp rất tốt với nhau:

  * Entities/UseCase của Clean Arch có thể được mô hình hóa theo DDD.
  * DDD cung cấp nội dung cho tầng Domain.

---

## 4. Kết Luận

* Nắm vững Git là yêu cầu cơ bản để làm việc nhóm hiệu quả.
* Các framework như NestJS, ReactJS, Docker,... cần sử dụng linh hoạt tùy dự án.
* Clean Architecture giúp viết code maintainable, dễ test.
* DDD hỗ trợ mô hình hóa logic nghiệp vụ rõ ràng, phù hợp hệ thống lớn.
* Làm việc nhóm hiệu quả cần có quy trình giao tiếp rõ ràng, công cụ hỗ trợ phù hợp và tinh thần trách nhiệm cao.
