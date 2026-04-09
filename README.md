# 🚀 TrackFlow API (Backend)

This is the original, high-performance backend for **TrackFlow**, a privacy-focused analytics engine. Designed specifically for the **Cloudflare Edge**, this API handles high-concurrency event ingestion using a modern, type-safe architecture.

## ⚙️ Technical Highlights

* **Runtime:** Cloudflare Workers (Edge Computing)
* **Framework:** Hono (OpenAPI/Zod integrated)
* **Persistence:** Cloudflare D1 (SQL) + Cloudflare Queues
* **Security:** Middleware-based Auth & Clerk Webhook Integration
* **Philosophy:** Modular Monolith for solo-developer maintainability.

## 🏗 System Architecture

The API was designed to solve the "Ingestion Bottleneck." Instead of writing directly to the database during a tracking hit, the system uses an asynchronous event-driven flow:

1. **Ingestion:** Hono receives the tracking payload and validates it via Zod.
2. **Buffering:** Events are immediately pushed to **Cloudflare Queues**.
3. **Processing:** A background consumer pulls batches of messages and performs a bulk insert into **D1**.



## 📂 Design Patterns

- **Repository Pattern:** Abstracted database logic for easier testing.
- **Contract-First API:** Auto-generated OpenAPI documentation ensures a reliable contract for any frontend consumer.
- **Global Context:** Leverages Cloudflare's `cf` object to enrich event data with geographic metadata at the edge.