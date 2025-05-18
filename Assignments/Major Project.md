# 🧠 Second Brain

## 👥 Team Structure

Group Project (4 members):

- 2 Backend Developers (Node.js + Hono + PostgreSQL + Prisma)
- 2 Frontend Developers (React/Next.js + TanStack + Vercel)

## 📌 Objective

Create a full-stack AI-powered memory assistant that helps users store, organize, and retrieve personal knowledge (text, links, etc.) — and interact with these “memories” via natural language using LLMs.

## 🔍 Core Features

### 📝 Memory Management

- Add memory (text, URLs, notes)
- Tag and categorize memories
- View recent and historical memories
- Edit/delete individual memories

### 🔎 Semantic Search (RAG)

- Ask questions like:
  - “What do I know about startups?”
  - “Show me all notes related to marketing.”
- AI engine (Mistral + Pinecone) retrieves relevant notes and builds a coherent answer
- References: Show list of memory snippets used in the response

### 💬 AI Chat Interface

- Ask follow-up questions
- Display conversational UI in chat format

### 👤 Auth & Personalization

- Sign up / login with BetterAuth (JWT)
- Personalized memory vault per user
- Session persistence and secure cookie handling across frontend/backend

## 🧱 Tech Stack

### 🖥 Frontend

- **Framework**: Next.js (with SSR/CSR/SSG as needed)
- **State Management**: Zustand
- **Data Fetching**: TanStack Query
- **Styling**: Tailwind CSS / ShadCN UI
- **Deployment**: Vercel

### 🛠 Backend

- **Framework**: Node.js + Hono + TypeScript
- **Database**: PostgreSQL via Prisma
- **Auth**: BetterAuth
- **RESTful API development** (CRUD, Search, RAG endpoints)
- **File Uploads** (optional + via Supabase)
- **Middleware**: Logging, Rate Limiting, Zod Validation

### 🤖 AI Stack

- **Mistral LLM** for inference
- **Pinecone** for embedding storage + semantic search
- **Embedding model**: text-embedding-mistral (or equivalent)
- **Retrieval Augmented Generation (RAG)** pipeline
- **Chunking, deduplication, context-aware ranking**

### 🐳 DevOps

- **Docker**
- **Deployment**:
  - **Backend**: Azure Container Apps (Dockerized + ACR)
  - **Frontend**: Vercel
- **CI/CD**: GitHub Actions + Secrets for env management

## 🧾 API Requirements

### Authentication

```
POST /auth/signup
POST /auth/login
GET /auth/session
```

### Memories

```
POST /memories         // Add memory
GET /memories          // List all memories (pagination, filter, tags)
GET /memories/:id      // Single memory
PUT /memories/:id      // Edit memory
DELETE /memories/:id   // Delete memory
```

### RAG Search

```
POST /ai/search
Body: { query: string }

Returns:
{
  answer: string,
  references: Memory[]
}
```

## 🗃 Database Schema (Sample)

- `users`

  - id (UUID)
  - name
  - email
  - passwordHash
  - createdAt

- `memories`
  - id (UUID)
  - userId (FK)
  - content (TEXT)
  - title (optional)
  - tags (string[])
  - createdAt

## ✅ Success Criteria

- ✅ Authenticated users can store and retrieve memories.
- ✅ Memories persist in database and support full CRUD.
- ✅ Semantic RAG search returns relevant memories using Pinecone.
- ✅ AI-generated response shown with references.
- ✅ Live deployments on Vercel (frontend) and Azure (backend).
- ✅ Fully documented APIs (OpenAPI spec or Swagger UI).
- ✅ Chat interface feels intuitive and real-time.

## 🚀 Stretch Goals (Optional)

- Upload PDFs and extract memory chunks via OpenAI or Claude
- Chrome extension to save highlights as memories
- Visualize memory clusters via embeddings
- Add reminders or revisit prompts ("Show me what I learned last month")
