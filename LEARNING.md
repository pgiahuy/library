# Note backend Rust

Ba chỗ còn yếu, xếp theo độ ưu tiên:
1. Rust production - yếu nhất nên cày trước.
2. Async messaging (RabbitMQ, transactional outbox, worker).
3. Kubernetes và IaC - để sau cùng, đọc dần là đủ.

Onion và auth đã quen (từng làm Spring layered và vài project auth), chỉ cần chỉnh lại tư duy một chút.

Ký hiệu độ dài: [ngắn] [vừa] [dài = chỉ để tra cứu]

---

## 1. Rust - cày nhiều nhất ở đây

- [ ] [ngắn] A Half-Hour to Learn Rust — đọc cái này đầu tiên, khoảng 30 phút, cô đọng nhất cho người đã biết code
  https://fasterthanli.me/articles/a-half-hour-to-learn-rust
- [ ] [vừa] Comprehensive Rust (Google) - trình bày gọn kiểu slide, có kèm bài tập
  https://google.github.io/comprehensive-rust/
- [ ] Rustlings - bài tập, làm song song cho quen tay
  https://github.com/rust-lang/rustlings
- [ ] [dài] The Rust Book - chỉ mở chương 1-10 và 13 khi cần tra, đừng đọc hết từ đầu tới cuối
  https://doc.rust-lang.org/book/

Mấy điểm phải nhớ kỹ vì khác Java:
- Ownership và borrowing - không có GC, đây là chỗ dễ tẩu hỏa nhất.
- Option<T> dùng thay cho null hoặc Optional.
- Result<T,E> kèm dấu ? dùng thay cho try/catch.
- Trait thì gần giống interface.
- Web framework hay dùng là Axum hoặc Actix, vai trò như Spring Boot.

| Java | Rust |
|---|---|
| null / Optional<T> | Option<T> |
| try/catch | Result<T,E> + ? |
| GC | ownership và borrowing |
| interface | trait |
| Spring Boot | Axum / Actix |

---

## 2. Async / Tokio - học sau khi nắm Rust cơ bản

- [ ] [vừa] Tokio Tutorial - async runtime hay dùng nhất của Rust
  https://tokio.rs/tokio/tutorial
- [ ] [vừa] Understanding Async Rust (fasterthanli.me) - đọc khi thấy async/await rối, nó giải thích vì sao async Rust khó
  https://fasterthanli.me/articles/understanding-rust-futures-by-going-way-too-deep

---

## 3. Onion / Clean Architecture - gần như biết rồi, chỉ lật lại tư duy

- [ ] [ngắn] Herberto Graça - "DDD, Hexagonal, Onion, Clean, CQRS… all together" - bài hay nhất để thấy bức tranh tổng
  https://herbertograca.com/2017/11/16/explicit-architecture-01-ddd-hexagonal-onion-clean-cqrs-how-i-put-it-all-together/
- [ ] [ngắn] Jeffrey Palermo - "The Onion Architecture" (4 phần gốc, ngắn)
  https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/
- [ ] [vừa] Clean Architecture (có sẵn PDF trong books/) - chỉ cần đọc chương 22 "The Clean Architecture"

Khác Spring ở chỗ: trong Onion thì domain (lõi) không biết gì về DB, HTTP hay framework cả. Dependency luôn hướng vào trong.

| Spring | Onion |
|---|---|
| @RestController | infra (ngoài cùng) |
| @Service | application |
| entity và business rule | domain (lõi) |
| @Repository / JPA | infra (ngoài cùng) |

---

## 4. Async messaging / Outbox / RabbitMQ - cái này chưa làm bao giờ

- [ ] [ngắn] microservices.io - Transactional Outbox - cách ghi DB và phát message mà không bị lệch nhau
  https://microservices.io/patterns/data/transactional-outbox.html
- [ ] [vừa] RabbitMQ Tutorials (chương 1-3) - làm tay cho hiểu queue, exchange, ack
  https://www.rabbitmq.com/tutorials

---

## 5. Kubernetes - để cuối, đọc dần thôi

- [ ] [ngắn] Illustrated Children's Guide to Kubernetes (CNCF, ~7 phút) - hiểu khái niệm qua hình minh hoạ
  https://www.cncf.io/phippy/the-childrens-illustrated-guide-to-kubernetes/
- [ ] [vừa] Learn Kubernetes Basics - nghịch trực tiếp trên web, không cần cài gì
  https://kubernetes.io/docs/tutorials/kubernetes-basics/
- [ ] [dài] The Kubernetes Book (Nigel Poulton) - để dành khi cần đào sâu

Tối thiểu nhớ được: pod, deployment, namespace, node, cluster. Day-2 ops nghĩa là provision/heal/scale.

---

## 6. Auth nâng cao - bồi thêm

- [ ] [ngắn] passkeys.dev - passwordless, phần này mới so với JWT
  https://passkeys.dev/
- [ ] [vừa] Zitadel docs (Concepts) - một identity provider open-source, đọc để tham khảo
  https://zitadel.com/docs

---

## Tuần này làm 5 cái thôi (theo thứ tự)

1. [ ] A Half-Hour to Learn Rust (30 phút)
2. [ ] Herberto Graça - Onion/Clean all together
3. [ ] microservices.io - Transactional Outbox
4. [ ] Children's Guide to Kubernetes (7 phút)
5. [ ] Bắt đầu Comprehensive Rust và Rustlings (cày dần cả tuần)

---

## Project để thực hành

Nâng cái auth service Rust từ starter lên cho tử tế: Axum + tokio + JWT + RBAC + test, xếp theo Onion.
Như vậy vừa học Rust vừa thực hành mảng auth.

---

## Sách có sẵn (thư mục books/)

- Clean Architecture A Craftsman Guide to Software Structure and Design.pdf
- Clean Code.pdf
- Spring Boot.pdf
