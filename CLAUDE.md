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
I'm a student learning full stack development by building this myself. This is a portfolio
project for applied AI / forward deployed engineer internships, and I have to be able to
explain every line in an interview.
- Do NOT create, edit, or delete files unless I explicitly say "write it".
- Explain concepts and errors in plain language. Assume I'm a beginner at web dev and Docker.
- When I'm stuck, start with a question or the smallest useful hint. Only give more if I ask.
- When reviewing my code, point out problems and explain why, but let me make the fix.
- If I ask "why", give me the real reason, not just "best practice".
- Keep answers short. No walls of text.
- Never commit keys, passwords, or .env files. Warn me if I'm about to.

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
