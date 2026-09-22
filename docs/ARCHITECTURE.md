# Architecture

Counsel uses a React client and Express API split into clear product boundaries: public service content, authentication, AI chat, chat history, and payment/entitlement state. Prisma maps the server domain to PostgreSQL while middleware keeps protected operations behind JWT verification.

## Key boundaries

- **Presentation:** React pages and reusable chat/service components.
- **Identity:** registration, login, password hashing, and JWT middleware.
- **AI orchestration:** request validation, free-usage checks, streamed OpenAI output, and usage increments.
- **Persistence:** Prisma models for users, chats, and payment records.
- **Entitlements:** paid status and usage messaging kept server-side so the client cannot grant access by itself.
