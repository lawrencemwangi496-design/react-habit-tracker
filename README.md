# Habit Tracker

**Forked from:** [nicopanozo/habit-tracker](https://github.com/nicopanozo/habit-tracker)

A habit tracking application built with React and TypeScript.

---

## Fork Purpose

This fork implements security scanning and CI/CD pipelines as part of a DevOps learning journey. The focus is on:
- Automated security validation before merging
- Containerized deployment
- Maintaining ability to sync with upstream

---

## CI/CD Pipelines

### 1. Security Scan (PR Gate)

**Trigger:** Pull requests to `main`, daily at 06:00 UTC, or manual dispatch

| Job | Tool | Purpose |
|-----|------|---------|
| syntax_scan | ESLint, TypeScript | Code quality and type checking |
| dependency_scan | npm audit | Vulnerability check in dependencies (fails on high severity) |
| synk_scan | Snyk | Deep dependency vulnerability analysis |
| trivy_scan | Trivy | Filesystem vulnerability scan (fails on HIGH/CRITICAL) |
| secret_scan | TruffleHog | Detect exposed secrets in code |
| test | Jest | Run unit tests |

**Purpose:** Blocks merging if critical vulnerabilities or secrets are detected.

---

### 2. Deployment (Push to Main)

**Trigger:** Push to `main` branch

| Job | Description |
|-----|-------------|
| build_push | Build Docker image, scan with Trivy (fails on CRITICAL/HIGH), push to GHCR |
| sync | Rsync docker-compose.yml to VPS via SSH |
| deploy | Pull latest image, restart container, prune old images |

**Purpose:** Automated deployment after passing security gates.

**Flow:**
```
PR opened → Security scan → Merge to main → Build → Deploy to VPS
```

---

## Deployment

- **Image Registry:** `ghcr.io/lawrencemwangi496-design/habit_tracker`
- **Deployment:** Docker Compose on VPS
- **Access:** `http://38.242.140.239:8080` (configured via docker-compose)

---

## Secrets Required

| Secret | Used By | Purpose |
|--------|---------|---------|
| `GITHUB_TOKEN` | Built-in | GHCR authentication |
| `SSH_PRIVATE_KEY` | deploy workflow | SSH access to VPS |
| `SERVER_IP` | deploy workflow | VPS IP address |
| `SERVER_USERNAME` | deploy workflow | VPS username |
| `SYNK_TOKEN` | security workflow | Snyk vulnerability scanning |

---

## Development

### Prerequisites
- Node.js 20+
- npm

### Setup

```bash
git clone https://github.com/lawrencemwangi496-design/react-habit-tracker.git
cd react-habit-tracker
npm install
npm run dev
```

### Available Scripts

| Script | Purpose |
|--------|---------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run TypeScript type checking |
| `npm run test` | Run Jest tests |
| `npm run format` | Format code with Prettier |

---

## Project Structure

```
habit-tracker/
├── .github/workflows/
│   ├── security_scan.yml   # PR gate (syntax, deps, Snyk, Trivy, secrets, tests)
│   └── deploying.yml       # Push to main (build, push, deploy)
├── src/                    # React source code
├── Dockerfile              # Container configuration
└── docker-compose.yml      # Production deployment config
```

---

## Contributing to Upstream

Changes intended for the original repository should be submitted to [nicopanozo/habit-tracker](https://github.com/nicopanozo/habit-tracker). This fork adds security scanning and deployment automation not present upstream.

---

## License

MIT — see original repository.

---
*Security-first CI/CD pipeline for learning purposes*