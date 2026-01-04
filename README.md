# Polymarket Information Engine
A high-performance Decisional Executive Operating System designed to aggregate, evaluate, and act upon market-moving signals across multiple asset classes (Crypto, Equities, etc.).
## Project Overview
The Polymarket Information Engine is a production-grade intelligence platform that transforms raw data into actionable trade proposals. It employs a formal "Provably Correct" decision pipeline that gates signals through rigorous risk and liquidity invariants before presenting them in a low-latency executive terminal.
## Core Features
- **Signal Aggregation**: Real-time ingestion from Twitter/X, Telegram, Binance Listings, RSS feeds, and Reuters.
- **Risk-Aligned Evaluation**: Automated assessment of edge, confidence, and urgency.
- **Decision Invariants**: Hard-coded gates for Edge Thresholds, MRC (Marginal Risk Contribution) budgets, and Execution Feasibility.
- **Institutional Terminal**: A high-density dashboard for real-time monitoring of system posture, action queues, and portfolio impact.
- **Multi-Asset Support**: Modular architecture handling both crypto assets and traditional equities.
## Technology Stack
### Backend
- **Core Framework**: .NET 8 (C#)
- **Database**: SQLite (high-concurrency WAL mode)
- **Persistence Layer**: Dapper (Lightweight ORM)
- **Background Processing**: ASP.NET Core Background Services (Workers)
- **API**: ASP.NET Core Minimal APIs
- **Infrastructure**: Docker for containerization, Prometheus for monitoring.
### Frontend
- **Logic**: Vanilla JavaScript (Async/Await, modern DOM API)
- **Styling**: Modern CSS (CSS Variables, Flexbox/Grid)
- **Architecture**: Single Page Application (SPA) communicating with the .NET backend via REST APIs.
## Project Structure
```text
src/
├── Core/           # Domain logic, Risk Engine, Decision Evaluators, and Invariants.
├── Ingestion/      # Source-specific connectors (Twitter, Telegram, Exchange APIs).
├── Worker/         # Background ingestion and analytical processing jobs.
├── Dashboard/      # Unified API layer and the terminal frontend (wwwroot).
├── Infrastructure/ # Data persistence, caching, and external provider integrations.
├── CLI/            # Administrative and diagnostic command-line tools.
└── Tests/          # Unit and integration testing suites.
```
## Getting Started
### Prerequisites
- .NET 8 SDK
- Docker & Docker Compose (optional for local deployment)
### Running Locally
1. Clone the repository.
2. Open `PolymarketEngine.sln` in your preferred IDE or use the terminal.
3. Start the dashboard:
   ```bash
   dotnet run --project src/Dashboard/Polymarket.InformationEngine.Dashboard.csproj
   ```
4. Access the terminal at `http://localhost:9001`.
## Deployment
The project is container-ready with a root `Dockerfile` and `docker-compose.yml`. It is configured for deployment on Fly.io using the provided `fly.toml`.
---
*This system implements the v1.2.1-SEALED protocol for institutional decision purity.*

## On "Provably Correct"
The term "Provably Correct" refers to deterministic, testable decision
pipelines governed by explicit invariants and verifiable constraints.
It does not imply formal mathematical proofs, but reproducible and
auditable system behavior.

