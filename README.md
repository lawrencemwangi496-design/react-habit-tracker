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
- CI/CD pipeline runs on PRs and merges

**Additions:**
- CI/CD pipeline with Docker builds and VPS deployment
- Security scanning via Trivy
- GitHub Container Registry integration
- Documentation for deployment and security processes

---

## CI/CD Pipeline

### GitHub Actions Workflow

On every push to `main` or `master`:

1. **Build:** Docker image built from source
2. **Push:** Image pushed to GitHub Container Registry
3. **Deploy:** Container deployed to VPS on port 8080
4. **Scan:** Security vulnerabilities scanned with Trivy

### Deployment Target

Production instance: `http://38.242.140.239:8080`

Container registry: `ghcr.io/lawrencemwangi496-design/react-habit-tracker`

### Security

- Trivy scans run on every build
- Vulnerability reports tracked in [security_reports](https://github.com/lawrencemwangi496-design/security_reports)
- Images use minimal Alpine base (nginx:stable-alpine, node:20-alpine)

---

## Manual Deployment

```bash
# Build
npm run build
docker build -t react-habit-tracker .

# Run
docker run -d -p 8080:80 --name habit-tracker react-habit-tracker
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
└── Dockerfile          # Container configuration
```

---

## Contributing to Upstream

Changes intended for the original repository should be submitted via Pull Request to [nicopanozo/habit-tracker](https://github.com/nicopanozo/habit-tracker). This fork is primarily for CI/CD experimentation and personal deployment.

---

## License

MIT — see original repository for details.

---

*Maintained as part of DevOps learning journey*