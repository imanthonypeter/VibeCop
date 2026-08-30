VibeCop 🛡️

"Vibe, Then Verify." The ultimate open-source AppSec playground and automated security audit suite designed specifically for AI-generated applications (v0, Lovable, Bolt.new, Cursor, Replit, and Windsurf).

📖 Overview
The era of Vibe Coding has drastically collapsed the distance between intent and execution. Platforms like Lovable, Bolt, and Cursor allow anyone to ship full-stack applications in a weekend. However, this speed introduces severe, recurring security blind spots. Because generative AI models optimize for visual delivery and immediate user feedback, they systematically omit critical backend safeguards.

VibeCop bridges this gap. It acts as an automated ethical hacking agent that dynamically probes your live AI-built applications, identifies critical vulnerabilities (like missing Row-Level Security or exposed frontend secrets), and instantly generates tailored remediation prompts and configuration files (.cursorrules, CLAUDE.md) using the R.A.I.L.G.U.A.R.D. framework to teach your AI how to fix the code securely.

✨ Features
🔍 1. Automated Dynamic Security Audits (DAST)
VibeCop doesn't just read code—it dynamically interacts with your live app to prove if an exploit is possible:

Supabase & Firebase RLS Prober: Automatically extracts public credentials (like SUPABASE_ANON_KEY) and attempts direct database queries against highly predictable table names (e.g., users, profiles, billing). If it retrieves data, it flags a critical RLS failure.
BOLA (Broken Object-Level Authorization) Tester: Simulates sequential multi-tenant requests (e.g., trying to access /api/projects/2 using a token that only owns /api/projects/1) to check if the AI-generated CRUD backend verifies resource ownership.
CORS Misconfiguration Audit: Checks if the production server responds with permissive cross-domain headers (Access-Control-Allow-Origin: *) alongside active credentials.
🧵 2. Static Frontend Bundle Scanning (SAST)
Frontend Secrets Extractor: Scans compiled client-side JavaScript bundles to find hardcoded high-entropy strings and patterns representing sensitive private keys (e.g., Stripe sk_live_, OpenAI keys, or Supabase service_role keys) mistakenly bundled into production code.
🩹 3. The Cure Center (Remediation Hub)
Instead of just pointing out failures, VibeCop gives you three instant cures:

AI-Remediation Prompts: Highly structured markdown prompts with XML tags that you can copy-paste directly into your generator (Lovable, Bolt, v0) to instruct the AI to rewrite the code safely.
Local Guardrails (.cursorrules / CLAUDE.md): Personalized system instructions leveraging the R.A.I.L.G.U.A.R.D. (Reason-Aligned Instruction Layers for Generative Use by AI Rule-Directed agents) framework, forcing your local IDE agents to think about security before generating new features.
Direct SQL Migrations: Pure, copy-pasteable SQL scripts to enable RLS and write robust access policies on Supabase with a single click.
🛠️ Tech Stack
VibeCop is built with a highly performance-oriented, modern stack:

Frontend: Next.js (TypeScript) + Tailwind CSS for a sleek, human-centric, warm-minimalist UI with smooth micro-animations.
Backend: FastAPI (Python 3.12) for lightning-fast concurrent HTTP probing, bundle regex parsing, and secure LLM routing.
AI Integration: LangChain / Official SDKs to dynamically assemble contextual remediation prompts.
📊 Vulnerability Matrix
Based on longitudinal industry data and benchmarks, VibeCop focuses on the most recurring platform-specific failure modes:

Platform	Modal Top Finding	Threat Level	VibeCop Scanner Probe
Lovable	Missing/Broken Supabase RLS	🔴 Critical	Supabase RLS Prober (/rest/v1/*)
Bolt.new	Hardcoded secrets in client bundle	🔴 Critical	Frontend Bundle Scanner (sk_live_, etc.)
Replit	Public .env exposure on default deploys	🟠 High	Config/Environment Scanner
Cursor	Broken Object-Level Auth (BOLA)	🟠 High	Multi-tenant Ownership Validator
v0	Unauthenticated API endpoints	🟠 High	Naked Route Auditor
🚀 Getting Started
1. Prerequisites
Python 3.12+
Node.js 18+
2. Backend Setup (FastAPI)
# Navigate to backend
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run server
uvicorn main:app --reload --port 8000
3. Frontend Setup (Next.js)
# Navigate to frontend
cd frontend

# Install packages
npm install

# Run development server
npm run dev
Open http://localhost:3000 to access the VibeCop portal.

🛡️ The R.A.I.L.G.U.A.R.D. Philosophy
VibeCop believes in the "Vibe, Then Verify" model. AI-generated code is not inherently secure. By injecting a cognitive security model into your IDEs via custom .cursorrules or CLAUDE.md, we teach the AI agent how to:

Reason securely before suggesting code.
Align all outputs with zero-trust architecture.
Input validate and sanitize every endpoint.
Limit exposures by hiding secrets on the server side.
📚 References & Standards
VibeCop's testing suite is calibrated and mapped against established security frameworks:

VibeEval 2026 AI App Security Benchmark: Built using the findings and methodology of the 2026 Failure-Mode Catalog for Lovable, Bolt, Cursor, Replit, and v0.
OWASP Web Top 10 (2021) & API Security Top 10 (2023)
Cloud Security Alliance (CSA) R.A.I.L.G.U.A.R.D. Framework
📄 License
Distributed under the GNU GPL v3 license. See LICENSE for more information.

Formulated with care by VibeCop. Protecting the next generation of software.

