# Learning Roadmap — HyAn / AnHysen Backend

> Lộ trình học cá nhân hoá cho nền tảng Java/Spring + auth, hướng tới làm backend cho nền tảng AnHysen (Rust engine, Onion architecture, async workers, Kubernetes).
>
> Nguyên tắc tuyển chọn: cô đọng — chất lượng cao — kiến thức/trang lớn nhất. Tránh tài liệu lê thê.
>
> Độ dài: [Ngắn] · [Vừa] · [Dài] (chỉ dùng tra cứu / để dành)

---

## 3 gap chính cần lấp (theo thứ tự ưu tiên)

1. Rust ở mức production — gap lớn nhất
2. Async messaging — RabbitMQ, transactional outbox, worker pattern
3. Kubernetes & IaC — học sau cùng, đọc dần là đủ

> Onion architecture & Auth gần như đã biết (nền Spring layered + 4 repo auth) → chỉ cần "lật tư duy".

---

## 1. Rust — đầu tư nhiều nhất

- [ ] [Ngắn] A Half-Hour to Learn Rust — đọc ĐẦU TIÊN (~30 phút), cô đọng nhất cho người đã biết lập trình
  https://fasterthanli.me/articles/a-half-hour-to-learn-rust
- [ ] [Vừa] Comprehensive Rust (Google) — súc tích, slide-style, có bài tập
  https://google.github.io/comprehensive-rust/
- [ ] Rustlings — bài tập làm song song (học bằng tay, không phải đọc)
  https://github.com/rust-lang/rustlings
- [ ] [Dài] The Rust Book — CHỈ tra cứu ch. 1–10 + 13 khi bí, đừng đọc tuần tự hết
  https://doc.rust-lang.org/book/

Trọng tâm bắt buộc: `ownership` & `borrowing` (không có GC như Java), `Option<T>` (thay `null`/`Optional`), `Result<T,E>` + toán tử `?` (thay `try/catch`), `trait` (≈ `interface`).

| Java (đã quen) | Rust |
|---|---|
| `null` / `Optional<T>` | `Option<T>` |
| `try/catch`, exceptions | `Result<T,E>` + `?` |
| Garbage Collector | Ownership & Borrowing |
| `interface` | `trait` |
| Spring Boot | Axum / Actix |

---

## 2. Async / Tokio — sau khi nắm Rust cơ bản

- [ ] [Vừa] Tokio Tutorial (chính thức) — async runtime backend HyAn dùng
  https://tokio.rs/tokio/tutorial
- [ ] [Vừa] Understanding Async Rust (fasterthanli.me) — giải thích vì sao async Rust khó
  https://fasterthanli.me/articles/understanding-rust-futures-by-going-way-too-deep

---

## 3. Onion / Clean Architecture — gần như đã biết, chỉ "lật tư duy"

- [ ] [Ngắn] Herberto Graça — "DDD, Hexagonal, Onion, Clean, CQRS… How I put it all together" — bức tranh tổng hay nhất
  https://herbertograca.com/2017/11/16/explicit-architecture-01-ddd-hexagonal-onion-clean-cqrs-how-i-put-it-all-together/
- [ ] [Ngắn] Jeffrey Palermo — "The Onion Architecture" (4 phần gốc, ngắn)
  https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/
- [ ] [Vừa] Clean Architecture (đã có PDF trong repo) — chỉ cần ch. 22 "The Clean Architecture"

Điểm khác Spring: trong Onion, domain (lõi) KHÔNG biết gì về DB/HTTP/framework; dependency chỉ hướng vào trong.

| Spring (đã quen) | Onion |
|---|---|
| `@RestController` | Infrastructure (vòng ngoài) |
| `@Service` | Application |
| Entity + business rules | Domain (lõi) |
| `@Repository` / JPA | Infrastructure (vòng ngoài) |

---

## 4. Async messaging / Outbox / RabbitMQ — gap thật, chưa từng làm

- [ ] [Ngắn] microservices.io — Transactional Outbox pattern (Chris Richardson) — đúng pattern HyAn đang viết
  https://microservices.io/patterns/data/transactional-outbox.html
- [ ] [Vừa] RabbitMQ Official Tutorials (ch. 1–3) — hands-on: queue / exchange / ack
  https://www.rabbitmq.com/tutorials

---

## 5. Kubernetes — đọc dần, học sau cùng

- [ ] [Ngắn] The Illustrated Children's Guide to Kubernetes (CNCF, ~7') — hiểu khái niệm bằng hình
  https://www.cncf.io/phippy/the-childrens-illustrated-guide-to-kubernetes/
- [ ] [Vừa] Learn Kubernetes Basics (interactive, không cần cài gì)
  https://kubernetes.io/docs/tutorials/kubernetes-basics/
- [ ] [Dài] The Kubernetes Book — Nigel Poulton — để dành khi cần đi sâu

Khái niệm tối thiểu cần nắm: pod, deployment, namespace, node, cluster, Day-2 ops (provision/heal/scale).

---

## 6. Auth nâng cao — củng cố thế mạnh sẵn có

- [ ] [Ngắn] passkeys.dev — HyAn dùng passkeys (bạn đã giỏi JWT, đây là phần mới)
  https://passkeys.dev/
- [ ] [Vừa] Zitadel Docs — Concepts — identity provider HyAn dùng
  https://zitadel.com/docs

---

## Tuần này — chỉ cần 5 thứ (theo thứ tự)

1. [ ] A Half-Hour to Learn Rust (30')
2. [ ] Herberto Graça — Onion/Clean all together (1 bài)
3. [ ] microservices.io — Transactional Outbox (1 trang)
4. [ ] Illustrated Children's Guide to Kubernetes (7')
5. [ ] Bắt đầu Comprehensive Rust + Rustlings (làm dần cả tuần)

---

## Dự án thực hành đề xuất

Nâng cấp repo `auth-management` (Rust) từ starter 1-commit thành auth service tử tế:
Axum + tokio + JWT + RBAC + test, tổ chức theo Onion.
Học Rust qua đúng thế mạnh auth, tạo sample khớp với mảng identity của HyAn.

---

## Sách có sẵn trong repo này

- `Clean Architecture A Craftsman Guide to Software Structure and Design.pdf`
- `Clean Code.pdf`
- `Spring Boot.pdf`
