Here's your prompt:

---

> Create a professional PowerPoint presentation titled **"OPEN SQL — Text to SQL Query Generator"** with the following structure and content:
>
> **Slide 1 — Title Slide**
> Title: OPEN SQL
> Subtitle: Text to SQL Query Generator using RAG Pipeline & DB Schema Semantic Search
> Add a tagline: *"Ask in English. Get SQL. Instantly."*
>
> **Slide 2 — The Problem**
> Title: The Problem with SQL in Organisations
> Content: Non-technical teams (finance, ops, product) need data but can't write SQL. Engineers become bottlenecks for every data request. Ad-hoc queries are slow, error-prone, and undocumented. No audit trail on who queried what sensitive data.
>
> **Slide 3 — What is OPEN SQL?**
> Title: Introducing OPEN SQL
> Content: A company-internal Text-to-SQL engine powered by RAG (Retrieval-Augmented Generation). Users type a natural language question. The system retrieves the relevant DB schema context. An LLM generates the correct SQL. The query executes and returns results — all in one click. Built on top of PostgreSQL + pgvector + Spring Boot.
>
> **Slide 4 — Approach 1: Schema in Excel + Analytics Tool (e.g. ChatGPT)**
> Title: Approach 1 — Schema Upload via Excel
> Content: Export DB schema to Excel manually. Upload to ChatGPT or an analytics tool. Ask natural language questions. Copy the generated SQL and run it manually in a DB client.
> Include a simple left-to-right flow diagram: `Excel Schema → Upload to ChatGPT → Natural Language Query → Generated SQL (text only) → Manual Execution`
> Callout box: *"Works for one person, once. Breaks at scale."*
>
> **Slide 5 — Approach 1: Limitations**
> Title: Why Approach 1 Fails at Enterprise Scale
> Bullet points:
> - Schema goes stale the moment a column is added or a table changes
> - No row-level security — any user can query any data
> - SQL must be copy-pasted and run manually — no direct execution
> - No audit trail — who queried what, when?
> - Sensitive schema and queries leave the organisation (data residency risk)
> - Context window overflow for schemas with 100+ tables
> - No saved queries, no approval workflows, no access control
>
> **Slide 6 — Approach 2: Enterprise RAG Pipeline (OPEN SQL)**
> Title: Approach 2 — Enterprise Vector Semantic Search
> Content: The OPEN SQL way. Schema is chunked (one chunk per table with columns, PKs, FKs, business description), embedded into vectors, and stored in pgvector. On every user query, only the semantically relevant tables are retrieved. The LLM generates SQL using only that context. SQL is validated, executed with user scoping, and results returned as JSON.
> Include a two-lane architecture diagram:
> - Offline lane: `PostgreSQL → Schema Extractor → Chunker → Embedding Model → pgvector`
> - Online lane: `User Query → Query Embedder → Similarity Search → LLM API → SQL Validator → Execute on PostgreSQL → Results`
>
> **Slide 7 — Schema Change Sync (Flyway Integration)**
> Title: Always in Sync — Automatic Schema Updates
> Content: Every Flyway migration triggers a re-embedding of only the changed tables on Spring Boot startup. Three cases handled automatically — ALTER TABLE (upsert embedding), CREATE TABLE (insert new embedding), DROP TABLE (delete stale embedding). No manual intervention. No stale context. Embeddings always reflect the live schema.
> Include a flow diagram: `git push → CI/CD → Spring Boot starts → Flyway runs → ApplicationReadyEvent → Parse changed tables → Re-embed → pgvector upserted → Ready`
>
> **Slide 8 — Head-to-Head Comparison**
> Title: Approach 1 vs OPEN SQL — Side by Side
> Include a comparison table with these rows: Schema Freshness, Token Cost, Row-Level Security, Direct Execution, Audit Trail, Data Privacy, Handles 100+ Tables, Semantic Search, Multi-User Access, Enterprise Ready.
> Columns: Factor | Approach 1 (Excel + ChatGPT) | Approach 2 (OPEN SQL)
> Use ✅ / ❌ / ⚠ symbols. OPEN SQL should win on every enterprise factor.
>
> **Slide 9 — Use Cases in the Organisation**
> Title: Who Uses OPEN SQL and How?
> Four use case cards:
> 1. *Finance Team* — "Show total liabilities above ₹10L this quarter" → gets live data without waiting for engineering
> 2. *Product Manager* — "How many users added a SIP plan in the last 30 days?" → self-serve analytics
> 3. *Operations* — "List all failed transactions this week by payment method" → instant operational queries
> 4. *Compliance / Audit* — Full query log with user, timestamp, generated SQL, and row count for every execution
>
> **Slide 10 — Key Advantages of Building Internal**
> Title: Why Build OPEN SQL Internally?
> Five advantages with icons:
> 1. 🔒 Row-Level Security — every generated SQL is scoped to the authenticated user automatically
> 2. 📋 Full Audit Trail — every query logged with user, SQL, timestamp, result count
> 3. 🏠 Data stays internal — schema and queries never leave your infrastructure
> 4. ⚡ Always fresh — Flyway integration keeps embeddings in sync with every deployment
> 5. 🏢 Scales to enterprise — semantic search handles thousands of tables, not just 50
>
> **Slide 11 — Tech Stack**
> Title: OPEN SQL — Technology Stack
> Include a layered stack diagram with these layers:
> - API Layer: Spring Boot REST (Java)
> - AI Layer: OpenAI Embeddings + Claude / GPT-4o for SQL generation
> - Vector Layer: pgvector (PostgreSQL extension)
> - DB Layer: PostgreSQL with Flyway migrations
> - Security Layer: JWT auth + user_id scoped query execution
> - Observability: Prometheus + Grafana
>
> **Slide 12 — Closing Slide**
> Title: OPEN SQL
> Tagline: *"Your database. Your schema. Your queries. No SQL knowledge required."*
> Three closing points: Secure by design. Always in sync. Enterprise ready.
>
> **Design instructions:**
> Use a dark navy and blue colour scheme (#0F172A background, #3B82F6 accent, white text). Use bold section headers. Keep bullet points concise — max 8 words per bullet. All diagrams should be clean left-to-right or top-to-bottom flow boxes with arrows. Slide layout should feel like a modern SaaS product pitch deck — not a corporate template. Use consistent iconography throughout.

---

Paste this directly into Claude with the PowerPoint skill, or use it with any AI presentation tool (Gamma, Beautiful.ai, or just tell me and I'll generate the PPTX right now).
