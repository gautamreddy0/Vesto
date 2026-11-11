# Vesto

## What this is
Vesto is an applied AI "thesis desk" for learning to invest with real market data.
I'm the portfolio manager. I write trade pitches (buy/sell, why, what would prove me wrong).
An AI fund manager scores every pitch with structured output, and a trade (paper money only)
executes only if it's approved. Three fixed analyst agents (value, momentum, contrarian) pitch
their own trades through the same review gate. A scorecard tracks whose theses actually work
(5-day hit rate vs the S&P 500, plus cost and latency per pitch).

Full product details: docs/product.md, docs/research.md. My walkthrough log: docs/walkthrough.md.

## How I want you to help (most important section)
I'm a student learning full stack + applied AI by building this. I have to explain everything in interviews.

PLUMBING: you can write it directly.
Docker/compose, Dockerfiles, configs, .gitignore, .env.example, scaffolding, CI files, copying docs, installing packages.
After writing, give me a short explanation of each file (what it does, why it's set up that way)
and ask me 2 to 3 questions to make sure I understand it.

PRODUCT: I write it, you coach.
Database schema, SQL/queries, API routes, data fetching, server vs client components, UI logic,
LLM calls, structured output, agents and tool calling, RAG, evals.
For these: explain concepts, give the smallest useful hint first, review my code and point out
problems, but don't write the code unless I explicitly say "write it".

Always:
- Keep answers short.
- Never commit keys, passwords, or .env files.
- Commit after each finished step with a clear message.

## Stack
- Frontend + API: Next.js (App Router, TypeScript, Tailwind, shadcn/ui) in web/
- Database: Postgres 16 in Docker
- Local dev: docker compose (services: web, db)
- Later: Python agent service, LLM calls through my own LLM Gateway (Go), pgvector for RAG,
  evals in CI, tracing per agent run, GitHub Actions CI, deployed

## Repo layout
- web/            Next.js app
- docs/           product, research, walkthrough notes
- docker-compose.yml
- .env            local secrets (never committed), .env.example is the committed template

## Data (planned)
- Prices: Massive (formerly Polygon.io) free plan, end-of-day, 5 requests/min, grouped daily endpoint
- Fundamentals: Finnhub free tier
- Benchmark: SPY
- 20 tickers: NVDA, AAPL, MSFT, AMZN, GOOGL, AVGO, META, MU, TSLA, LLY, BRK.B, AMD, JPM, XOM,
  V, JNJ, WMT, ABBV, MA, INTC
- Gotcha: BRK.B vs BRK-B differs across APIs. Handle it in one place.

## Schema (planned)
users, agents, tickers, prices_daily, pitches (author = me or an agent), reviews, trades, positions

## Current ticket
Tue 11/10: repo + docs/ + docker compose with Next.js and Postgres.
Done when `docker compose up` brings both up, localhost:3000 loads, and psql can SELECT 1.
Next: Thu 11/12 schema + migrations, done when a page reads a row from Postgres.

## Commands
- Run everything: docker compose up --build
- DB shell: docker compose exec db psql -U vesto -d vesto
- Stop: docker compose down (add -v to wipe the database volume)

## Rules I follow
- Commit every session with a real message.
- A ticket is done when it works, it's committed, and I can explain it out loud in 2 min.
- Resume numbers only come from things I actually measured.
