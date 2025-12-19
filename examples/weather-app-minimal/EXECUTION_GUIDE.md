# Weather App Minimal - Execution Guide

A minimal Weather App demonstrating Context Mesh workflow in 45-60 minutes.

**Tech Stack**: Vite + React + TypeScript + shadcn-ui | Fastify + Swagger

---

## Prerequisites

- Node.js 20+
- pnpm (or npm)
- Cursor IDE or GitHub Copilot

**Note**: No API key required! We use Open-Meteo, which is free and open source.

---

## How to Execute an Agent

When you see `Execute @context/agents/agent-*.md` in this guide, follow these steps:

1. **Open your AI assistant** (Cursor Chat, GitHub Copilot Chat, or similar)
2. **Type the command**: `Execute @context/agents/agent-setup.md` (replace with the agent name for each phase)
3. **Review the generated code** before accepting
4. **Run verification commands** after accepting the changes
5. **Check the Definition of Done (DoD)** to ensure everything is complete

**Note**: The `@context/` syntax works in Cursor. For other IDEs, you may need to:
- Use the full file path: `context/agents/agent-setup.md`
- Or copy the agent file content and paste it into your AI chat

---

## Execution Flow

```
1. Load Context
   ↓
2. Execute Agent 1: Setup
   → Verify → Approve
   ↓
3. Execute Agent 2: Backend
   → Verify → Approve
   ↓
4. Execute Agent 3: Frontend
   → Verify → Approve
   ↓
5. Final Test
```

---

## Phase 1: Setup

### Execute Agent
```
Execute @context/agents/agent-setup.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-setup.md` for complete criteria.

**Quick reference:**
- [ ] Backend structure created (Fastify + Swagger)
- [ ] Frontend structure created (Vite + React + TypeScript)
- [ ] shadcn-ui initialized (button, card, input)
- [ ] Environment variables template created
- [ ] `pnpm install` runs in both directories
- [ ] `pnpm run dev` starts both servers

### Verification
```bash
# Backend
cd backend && pnpm install && pnpm run dev
# Should start on port 3000

# Frontend
cd frontend && pnpm install && pnpm run dev
# Should start on port 5173
```

### After Setup
1. Copy `backend/.env.example` to `backend/.env`
2. No API key needed! Open-Meteo is free and open source.

✅ All DoD criteria met → Proceed to Phase 2

---

## Phase 2: Backend

### Execute Agent
```
Execute @context/agents/agent-backend.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-backend.md` for complete criteria.

**Quick reference:**
- [ ] Weather service implemented
- [ ] Weather route created (`GET /api/weather?city={city}`)
- [ ] Swagger documentation at `/docs`
- [ ] Error handling for invalid city
- [ ] Server runs on port 3000

### Verification
```bash
cd backend && pnpm run dev

# Test API
curl "http://localhost:3000/api/weather?city=London"

# Check Swagger
open http://localhost:3000/docs
```

✅ All DoD criteria met → Proceed to Phase 3

---

## Phase 3: Frontend

### Execute Agent
```
Execute @context/agents/agent-frontend.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-frontend.md` for complete criteria.

**Quick reference:**
- [ ] API client created
- [ ] WeatherForm component (search input)
- [ ] WeatherCard component (weather display)
- [ ] WeatherDisplay container
- [ ] Loading and error states
- [ ] UI uses shadcn-ui components

### Verification
```bash
cd frontend && pnpm run dev

# Test
open http://localhost:5173
# Search for "London" and verify weather displays
```

✅ All DoD criteria met → Project Complete!

---

## Final Test

1. **Start both servers**:
   ```bash
   # Terminal 1
   cd backend && pnpm run dev
   
   # Terminal 2
   cd frontend && pnpm run dev
   ```

2. **Open** http://localhost:5173

3. **Test scenarios**:
   - [ ] Search "London" → Weather displays
   - [ ] Search "São Paulo" → Weather displays
   - [ ] Search "InvalidCity123" → Error message shows
   - [ ] Loading spinner appears during search

---

## Project Structure

```
weather-app-minimal/
├── EXECUTION_GUIDE.md      # This file
├── AGENTS.md               # Router for AI agents
├── context/
│   ├── intent/
│   │   ├── project-intent.md
│   │   └── feature-weather-display.md
│   ├── decisions/
│   │   ├── 001-tech-stack.md
│   │   └── 002-api-integration.md
│   ├── knowledge/patterns/
│   │   ├── api-design.md
│   │   └── component-structure.md
│   ├── agents/
│   │   ├── agent-setup.md
│   │   ├── agent-backend.md
│   │   └── agent-frontend.md
│   └── evolution/
│       └── changelog.md
├── backend/
│   └── src/
├── frontend/
│   └── src/
└── README.md
```

---

## Troubleshooting

### Backend doesn't start
- Check port 3000 is available
- Verify `.env` file exists (even if empty, no API key needed)

### Frontend can't connect to backend
- Ensure backend is running on port 3000
- Check CORS is configured in backend

### API returns error
- Check city name spelling
- Verify Open-Meteo API is accessible (no API key needed)

---

## Learn More

- [Framework Documentation](../../FRAMEWORK.md)
- [Getting Started](../../GETTING_STARTED.md)
- [Complete Example: Todo App](../todo-app-complete/)

---

**Time**: 45-60 minutes | **Complexity**: Minimal

