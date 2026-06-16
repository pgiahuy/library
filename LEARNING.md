# Note học backend (Rust)

Cần lấp 3 chỗ yếu, theo thứ tự:
1. Rust ở mức làm thật — yếu nhất, ưu tiên
2. Async messaging (RabbitMQ, transactional outbox, worker)
3. K8s + IaC — để sau, đọc dần thôi

Onion với auth coi như biết rồi (đã làm Spring layered + mấy project auth) → chỉ cần lật lại tư duy.

(Đánh dấu độ dài: [Ngắn] [Vừa] [Dài=Chỉ tra cứu])

---

## 1. Rust — cày nhiều nhất ở đây

- [ ] [Ngắn] A Half-Hour to Learn Rust — đọc cái này TRƯỚC, ~30p, cô đọng nhất cho người đã biết code
  https://fasterthanli.me/articles/a-half-hour-to-learn-rust
- [ ] [Vừa] Comprehensive Rust (Google) — gọn, kiểu slide, có bài tập
  https://google.github.io/comprehensive-rust/
- [ ] Rustlings — bài tập, làm song song cho quen tay
  https://github.com/rust-lang/rustlings
- [ ] [Dài] The Rust Book — chỉ mở ch.1-10 + 13 khi bí, đừng đọc hết tuần tự
  https://doc.rust-lang.org/book/

Nhớ kỹ mấy cái này (khác Java):
- ownership & borrowing — ko có GC, đây là chỗ dễ khùng nhất
- Option<T> thay cho null / Optional
- Result<T,E> + dấu ? thay cho try/catch
- trait ~ interface
- web framework: Axum / Actix (kiểu Spring Boot)

| Java | Rust |
|---|---|
| null / Optional<T> | Option<T> |
| try/catch | Result<T,E> + ? |
| GC | ownership & borrowing |
| interface | trait |
| Spring Boot | Axum / Actix |

---

## 2. Async / Tokio — học sau khi nắm Rust cơ bản

- [ ] [vừa] Tokio Tutorial — async runtime hay dùng nhất của Rust
  https://tokio.rs/tokio/tutorial
- [ ] [vừa] Understanding Async Rust (fasterthanli.me) — đọc khi thấy async/await rối, giải thích vì sao nó khó
  https://fasterthanli.me/articles/understanding-rust-futures-by-going-way-too-deep

---

## 3. Onion / Clean Architecture — gần như biết rồi, chỉ lật tư duy

- [ ] [ngắn] Herberto Graça — "DDD, Hexagonal, Onion, Clean, CQRS… all together" — bài hay nhất, thấy bức tranh tổng
  https://herbertograca.com/2017/11/16/explicit-architecture-01-ddd-hexagonal-onion-clean-cqrs-how-i-put-it-all-together/
- [ ] [ngắn] Jeffrey Palermo — "The Onion Architecture" (4 phần gốc, ngắn)
  https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/
- [ ] [vừa] Clean Architecture (có PDF trong books/) — chỉ cần ch.22 "The Clean Architecture"

khác Spring chỗ nào: trong Onion thì domain (lõi) KO biết gì về DB/HTTP/framework. dependency chỉ hướng vào trong.

| Spring | Onion |
|---|---|
| @RestController | infra (ngoài cùng) |
| @Service | application |
| entity + business rule | domain (lõi) |
| @Repository / JPA | infra (ngoài cùng) |

---

## 4. Async messaging / Outbox / RabbitMQ — cái này chưa làm bao giờ

- [ ] [ngắn] microservices.io — Transactional Outbox — để ghi DB + phát message mà ko bị lệch
  https://microservices.io/patterns/data/transactional-outbox.html
- [ ] [vừa] RabbitMQ Tutorials (ch.1-3) — làm tay cho hiểu queue / exchange / ack
  https://www.rabbitmq.com/tutorials

---

## 5. Kubernetes — để cuối, đọc dần

- [ ] [ngắn] Illustrated Children's Guide to Kubernetes (CNCF, ~7p) — hiểu khái niệm bằng hình
  https://www.cncf.io/phippy/the-childrens-illustrated-guide-to-kubernetes/
- [ ] [vừa] Learn Kubernetes Basics — nghịch trực tiếp trên web, ko cần cài
  https://kubernetes.io/docs/tutorials/kubernetes-basics/
- [ ] [dài] The Kubernetes Book (Nigel Poulton) — để dành khi cần đào sâu

tối thiểu nhớ: pod, deployment, namespace, node, cluster. Day-2 ops = provision/heal/scale.

---

## 6. Auth nâng cao — chỗ mình mạnh sẵn, bồi thêm

- [ ] [ngắn] passkeys.dev — passwordless, mình giỏi JWT rồi thì cái này là phần mới
  https://passkeys.dev/
- [ ] [vừa] Zitadel docs (Concepts) — identity provider open-source, đọc tham khảo
  https://zitadel.com/docs

---

## tuần này làm 5 cái thôi (theo thứ tự)

1. [ ] A Half-Hour to Learn Rust (30p)
2. [ ] Herberto Graça — Onion/Clean all together
3. [ ] microservices.io — Transactional Outbox
4. [ ] Children's Guide to Kubernetes (7p)
5. [ ] bắt đầu Comprehensive Rust + Rustlings (cày dần cả tuần)

---

## project để thực hành

nâng cái auth service Rust từ starter lên cho tử tế: Axum + tokio + JWT + RBAC + test, xếp theo Onion.
=> học Rust qua đúng cái mình mạnh (auth).

---

## sách có sẵn (thư mục books/)

- Clean Architecture A Craftsman Guide to Software Structure and Design.pdf
- Clean Code.pdf
- Spring Boot.pdf
