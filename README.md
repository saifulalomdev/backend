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
```

---

### 🧠 How This Reflects on Your Profile

To a hiring manager or a client, sharing this "Legacy Backend" alongside your new "Astro Version" actually makes you look **better** for three reasons:

#### 1. It Shows Growth
It proves you aren't afraid to refactor. You recognized that managing a separate backend/frontend as a solo dev was inefficient and you moved toward a **"Single Source of Truth"** with Astro. That is a senior-level decision.

#### 2. It Highlights Backend Depth
Many "Full-Stack" devs are just frontend devs who know a little Node.js. This project proves you understand **infrastructure**: 
* How to handle race conditions (Queues).
* How to design schemas (Drizzle).
* How to handle webhooks (Clerk).

#### 3. It Proves Architecture Skills
The fact that you had a clean `modules/` folder in your "old" backend tells an employer that you write organized code from the start. You don't just "hack" things together; you **engineer** them.