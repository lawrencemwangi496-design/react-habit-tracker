# Habit Tracker

**Forked from:** [nicopanozo/habit-tracker](https://github.com/nicopanozo/habit-tracker)

A habit tracking application built with React and TypeScript. Track daily habits, monitor progress, and build consistency.

---

## Fork Purpose

This fork exists to practice and implement CI/CD pipelines while maintaining the ability to sync with upstream changes. The goal is to build production-grade automation without modifying the original project structure.

**Workflow:**
- All changes are submitted via Pull Requests
- No direct pushes to `main` branch
- `main` remains syncable with upstream
- CI/CD pipeline runs on merges to `main`

---

## CI/CD Pipeline

The GitHub Actions workflow (`deploying.yml`) runs on every push to `main`:

### Jobs

| Job | Description |
|-----|-------------|
| **build_push** | Build Docker image, scan with Trivy (fails on CRITICAL/HIGH), push to GHCR |
| **sync** | Rsync docker-compose.yml to VPS via SSH |
| **deploy** | Pull latest image and restart container on VPS |

### Flow

```
push to main → build image → scan → push to GHCR → sync compose file → deploy
```

### Deployment

- **Image Registry:** `ghcr.io/lawrencemwangi496-design/habit_tracker`
- **Deployment:** Docker Compose on VPS
- **Auto-restart:** `docker compose up -d` on deploy
- **Cleanup:** `docker image prune -f` after deployment

### Secrets Required

| Secret | Purpose |
|--------|---------|
| `GITHUB_TOKEN` | Built-in, used for GHCR auth |
| `SSH_PRIVATE_KEY` | SSH key for VPS access |
| `SERVER_IP` | VPS IP address |
| `SERVER_USERNAME` | VPS username |

---

## Manual Deployment

```bash
# Build
npm run build
docker build -t habit_tracker .

# Run with docker-compose
docker compose up -d
```

---

## Development

### Prerequisites
- Node.js 20+
- npm or pnpm

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
| `npm run format` | Format code with Prettier |

---

## Project Structure

```
habit-tracker/
├── src/
│   ├── components/     # React components
│   ├── constants/      # Application constants
│   ├── styles/         # CSS modules
│   ├── types/          # TypeScript definitions
│   └── utils/          # Helper functions
├── public/             # Static assets
├── Dockerfile          # Container configuration
└── docker-compose.yml  # Production deployment
```

---

## Contributing to Upstream

Changes intended for the original repository should be submitted via Pull Request to [nicopanozo/habit-tracker](https://github.com/nicopanozo/habit-tracker). This fork is primarily for CI/CD experimentation and personal deployment.

---

## License

MIT — see original repository for details.

---
*Maintained as part of DevOps learning journey*