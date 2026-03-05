# Senior Backend Engineer Technical Assessment

_Last updated: March 4, 2026_

Please do not redistribute this assessment outside your application process.

## Overview

Build a **hosted backend microservice** with a **minimal AI-generated user interface** that demonstrates backend engineering fundamentals, asynchronous processing, and effective use of modern developer tooling.

Your final solution must include:

- A running **hosted backend service**
- A **hosted UI** demonstrating backend capabilities
- A **public Git repository** with code, documentation, and Docker setup

---

## Important Notes

This assessment is designed to give you exposure to key parts of our tech stack. We’d like you to complete as much as you can.

The more you add, the better it will demonstrate your skills.

However, it is absolutely fine if you can’t implement certain parts. If so, please explain in your documentation or submission email which areas you did not cover or are less familiar with, and how AI assisted you in those areas. This will **not** negatively affect your application.

You are explicitly **allowed and encouraged** to use AI tools such as ChatGPT, Claude, Copilot, CLI AI tools, and similar tools. However, AI should be used as an **engineering assistant**, not as an unquestioned code generator.

We are interested in evaluating:

- How you guide AI with prompts
- Your architecture reasoning
- How you validate and refine AI output
- AI-assisted refactors or improvements
- Your judgment when accepting or rejecting AI suggestions

## Required Stack

You must use **NestJS (preferred)** or **Node.js**.

---

## Time & Submission

- **Time allocation:** 4–5 hours of focused work
- **Deadline:** Per email

### Submission Requirements

Please submit the following:

- Hosted Backend URL
- Hosted UI URL
- Public Git repository link

---

# Core System Requirements

You are building a **File Upload & Intelligent Processing Service**.

## 1) Authentication

### Backend
- Implement **login-only authentication**
- Users may be **hardcoded**
- Secure all endpoints with **JWT**

### Required Endpoint
- `POST /auth/login`  
  Returns a JWT token

---

## 2) File Upload & Intelligent Processing

### Required Endpoint
- `POST /upload`

### Functional Requirements
- Accept **one or multiple files**
- Validate allowed file types:
  - PDF
  - PNG
  - JPG
- Detect file characteristics:
  - Text-based
  - Image-based
  - Mixed
- Extract:
  - Text content (real or simulated extraction is acceptable)
- Extract and persist metadata:
  - File name
  - Size
  - Type
  - Number of pages (if applicable)
  - Upload timestamp

### Intelligent Enhancements (Required)
After extraction, enrich the file using AI-augmented logic to do **at least two** of the following:

- Summarize extracted text using an LLM
- Classify uploaded documents (for example: invoice, resume, contract)
- Extract structured fields using an LLM prompt
- Generate embeddings (can be mocked)
- Use AI to decide processing strategy (OCR vs text vs hybrid)

### Design Considerations
Please keep the following in mind and document your approach where relevant:

- Prompt design
- Error handling
- Cost and latency
- Fallback strategies

### Persistence
Persist all extracted and enriched data in a database and associate it with the authenticated user.

---

## 3) Asynchronous Processing & Queueing

File processing must be handled **asynchronously**.

### Acceptable queue options
- Redis / BullMQ
- RabbitMQ
- In-memory queue (acceptable)

### Requirements
- Upload requests should return immediately
- Background workers should handle processing
- Failed jobs should be retried or logged

---

## 4) Streaming & Event Simulation

After processing completes:

- Send results to **two mock HTTP endpoints**
- Log structured events to stdout or to a file
- Include basic retry or failure handling

---

## 5) Data Access

### Required Endpoints
- `GET /files`
- `GET /files/:id`

### Requirements
Return only files belonging to the authenticated user.

Each file response should include:
- Metadata
- Extracted content
- Enriched output (for example: summary, tags, type)

---

## 6) Minimal AI-Generated UI (Required)

You must provide a **hosted UI** that demonstrates your backend functionality.

### UI Requirements
- The UI must be **fully generated using AI tools**
- It should be **simple and minimal**
- No significant design effort is expected

### Acceptable frontend options
- Plain HTML / CSS / JS
- React
- Next.js
- Any lightweight frontend stack

### Required UI Features
- Login screen
- File upload form
- List uploaded files
- View file details (summary, metadata, tags)

The UI is only for demonstration purposes and does not require complex styling or advanced state management.

---

## 7) Architecture & Documentation — AI Transparency (Required)

Include a `/docs` directory with the following files:

### `ARCHITECTURE.md`
Include:
- High-level system overview
- Component interactions
- Queue and processing flow
- Data storage approach

### `DECISIONS.md`
Include:
- Key technical decisions
- Tradeoffs and constraints
- Areas intentionally simplified or deferred

### `AI_USAGE.md`
Include:
- How AI was used
- Example prompts or workflows
- Key prompts you used
- Where automation improved speed or clarity
- Where AI helped most
- Where AI output was incorrect or incomplete
- What you changed manually
- Final architectural decisions

---

## 8) Containerization & Deployment

### Requirements
- A `Dockerfile` for the backend
- A `docker-compose.yml` for local setup
- Hosted deployment of:
  - Backend service
  - UI
- Deployment instructions in the `README`

---

## 9) Security & Reliability (Bonus)

Examples include:
- Rate limiting
- Input validation
- Secure file handling
- Authentication guard coverage

---

## 10) Observability (Bonus)

Examples include:
- Structured logging
- Clear error responses
- Monitoring or tracing plan (in code or documentation)

---

## 11) Optional Enhancements

Optional additions may include:
- Swagger / OpenAPI documentation
- Unit or end-to-end tests
- Postman collection
- Background job monitoring endpoint

---

# Repository Requirements

Your repository must be **public** and include:

- Clear commit history with meaningful commit messages
- A `README` with:
  - Setup instructions
  - Environment variables
  - API usage
  - Deployment steps

---

## Final Note

We are excited to see the results of your work and how you approach both engineering and AI-assisted development.

If anything is unclear, please reach out and ask clarifying questions.
