# Life OS

Act as a Senior Systems Architect and Lead Full-Stack Developer. Your task is to draft a comprehensive, production-ready implementation plan for a new web application. 

Output the entire response as a structured Markdown document titled `technical_manifest.md`. Do not provide conversational filler; provide only the technical document.

# 1. Project Context & Constraints
I am building a lightweight, modular, self-hosted AI dashboard. It must be designed to run efficiently on a VPS (4 vCores, 8GB RAM) using Docker Compose. The system must avoid vendor lock-in, maintain high performance, and support multi-user authentication.

# 2. Core Functionality Requirements
- A "Scrape-to-Chat" bridge: Users input a URL, the system scrapes the site into clean Markdown, feeds it to an AI model, and opens a chat interface to discuss the content.
- AI Performance Metrics: The UI must intercept the AI stream to calculate and display tokens per second (t/s), total context length used, and response latency (in seconds).
- Data Exportation: Users must be able to export the AI's markdown output directly to the clipboard, Google Sheets (via API/webhook), PDF, XLSX, and DOCX.
- Multi-User: Secure account authorization system.

# 3. Required Document Structure
Please structure the `technical_manifest.md` exactly as follows:

## A. Goal
Define the primary objective, target audience (self-hosters, researchers, developers), and the core problem this software solves. 

## B. Architecture
Provide a detailed architectural breakdown. Explain how the Frontend, Backend, Scraper, and Database interact. Detail the data flow from the moment a user submits a URL to the moment the AI streams the final token. 

## C. Technologies
Outline the exact tech stack based on these strict preferences:
- Frontend: Vinext (Next.js on Vite) for lightweight deployment.
- AI Orchestration: Vercel AI SDK (Core) for provider-agnostic streaming and metric interception.
- Backend/Heavy Lifting: FastAPI (Python) to handle file conversions (PDF/XLSX/DOCX) and local API orchestration.
- Scraper: Self-hosted Firecrawl Docker container.
- Auth: Auth.js (NextAuth).
- Database: SQLite mapped with an ORM (Prisma or Drizzle).

## D. Projects (Implementation Phases)
Divide the development into strict, sequential phases. For each phase, list the core files to be created and the specific logic they must contain. 
- Phase 1: Infrastructure & Auth (Docker, DB, Login)
- Phase 2: The Scraper API Bridge (FastAPI to Firecrawl)
- Phase 3: The AI Chat UI & Metrics Engine (Vinext + Vercel AI SDK)
- Phase 4: The Export Pipeline (Format conversions and Google Sheets integration)

## E. Extra Customization Features
Propose 3-5 modular, scalable features that could be added in the future without breaking the core architecture (e.g., local RAG with vector databases, n8n webhook integrations, or local LLM failovers via Ollama).

## F. Documentation Strategy
Provide a strict standard operating procedure (SOP) for documenting the code. Specify how docstrings should be formatted in Python (FastAPI) and TypeScript (Vinext), and define the structure for the final `README.md` and deployment guide.
