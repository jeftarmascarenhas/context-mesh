# Weather App Minimal - Context Mesh Example

This is a **minimal end-to-end example** demonstrating how to use Context Mesh in a simple, practical project. This example shows the complete workflow from Intent to Build to Learn with a Weather App.

## 📋 Overview

**Project**: Simple Weather Application  
**Tech Stack**: Vite + React + TypeScript + shadcn-ui (Frontend) | Node.js + Fastify + Swagger (Backend)  
**Duration**: 45-60 minutes complete workflow demonstration  
**Complexity**: Minimal - Happy path only

## 🎯 What You'll Learn

- How to structure Context Mesh for a minimal project
- How to create intent documents (project, features)
- How to document technical decisions
- How to use Context Mesh workflow (Intent → Build → Learn)
- How to build a full-stack app with modern tools
- How AI can generate code from context

## 📁 Project Structure

```
weather-app-minimal/
├── README.md                    # This file
├── AGENTS.md                    # Router for AI agents (references Context Mesh)
├── context/                     # Context Mesh structure
│   ├── intent/
│   │   ├── project-intent.md   # Overall project intent
│   │   └── feature-weather-display.md # Feature: Weather display
│   ├── decisions/
│   │   ├── 001-tech-stack.md    # Decision: Technology stack
│   │   └── 002-api-integration.md # Decision: API integration
│   ├── knowledge/
│   │   └── patterns/
│   │       ├── api-design.md   # Pattern: API design
│   │       └── component-structure.md # Pattern: Component structure
│   └── evolution/
│       └── changelog.md         # Project changelog
└── [code/]                      # Generated code (will be created during Build)
    ├── frontend/
    └── backend/
```

## 🚀 Complete Workflow Demonstration

This example demonstrates the complete Context Mesh workflow:

### Phase 1: Intent (Planning) - 10-15 minutes
1. **Project Intent** → `context/intent/project-intent.md`
2. **Feature Intent** → `context/intent/feature-weather-display.md`
3. **Technical Decisions** → `context/decisions/001-*.md`, `002-*.md`

### Phase 2: Build (Construction) - 30-45 minutes
1. **AI generates code** based on context
2. **Decisions documented** (already done in Intent phase)
3. **Context updated** with implementation details (if needed)

### Phase 3: Learn (Learning) - 5 minutes
1. **Context updated** to reflect actual code
2. **Changelog updated** → `context/evolution/changelog.md`
3. **Reflection** on what was learned

## 🤖 Building with AI Agents (Cursor/Copilot)

This example is designed to be built using AI agents like Cursor or GitHub Copilot. The context provided is sufficient for an AI agent to generate the complete application.

**Recommended**: Use `AGENTS.md` as the entry point. It acts as a router that references all Context Mesh files automatically.

### Step 1: Load Context into AI Agent

**Option A: Using AGENTS.md (Recommended)**
- Open Cursor/Copilot Chat
- Load `AGENTS.md` - it automatically references all Context Mesh files
- AI agents will load the relevant context files automatically

**Option B: Direct Context Loading**

**In Cursor:**
1. Open Cursor Chat (`Cmd/Ctrl + L` or click the chat icon)
2. Click "Attach Files" or drag and drop the entire `context/` folder
3. Or reference specific files: `@context/intent/project-intent.md`

**In GitHub Copilot Chat:**
1. Open Copilot Chat (View → Copilot Chat)
2. Reference files using: `# context/intent/project-intent.md`
3. Load multiple files by referencing them in sequence

**Recommended Context Loading Order:**
1. `@context/intent/project-intent.md` - Overall project goals
2. `@context/decisions/001-tech-stack.md` - Technology choices
3. `@context/decisions/002-api-integration.md` - API integration approach
4. `@context/intent/feature-weather-display.md` - Feature requirements
5. `@context/knowledge/patterns/api-design.md` - API patterns
6. `@context/knowledge/patterns/component-structure.md` - Component patterns

---

## 📖 Step-by-Step Guide

### Prerequisites

Before starting, ensure you have:

- [ ] **Node.js 20+** installed (`node --version`)
- [ ] **npm** or **pnpm** installed (`npm --version` or `pnpm --version`)
- [ ] **Cursor IDE** or **GitHub Copilot** enabled
- [ ] **Git** installed (optional, for version control)
- [ ] **OpenWeatherMap API Key** (free - get at https://openweathermap.org/api)

**Note**: You don't need Docker, database, or any other complex setup. This is a minimal example!

---

## Step 1: Intent (Planning) - 10-15 minutes

**Objective**: Understand what to build and why, and make technical decisions before coding.

### 1.1 Read Project Intent

Read `context/intent/project-intent.md` to understand:
- **What**: Weather App that searches and displays weather
- **Why**: Learn Context Mesh with a practical, minimal project
- **Scope**: Frontend + Backend + API integration
- **Success Criteria**: What makes this project successful

**Key Points**:
- This is a minimal example (no database, no auth, no tests)
- Focus on happy path only
- Modern stack: Vite, Fastify, shadcn-ui
- Quick implementation (45-60 minutes)

### 1.2 Read Feature Intent

Read `context/intent/feature-weather-display.md` to understand:
- **What**: Weather display feature requirements
- **Scope**: Search by city, display weather info
- **Success Criteria**: What the feature must do

**Key Points**:
- Search input for city name
- Display: temperature, description, icon
- Loading and error states
- Clean UI with shadcn-ui

### 1.3 Read Technical Decisions

Read `context/decisions/001-tech-stack.md` to understand:
- **Frontend**: Vite + React + TypeScript + shadcn-ui
- **Backend**: Node.js + Fastify + Swagger
- **Why**: Fast, modern, minimal setup

Read `context/decisions/002-api-integration.md` to understand:
- **API**: OpenWeatherMap (free tier)
- **Approach**: Backend calls API (hides API key)
- **Response Format**: How data is structured

### 1.4 Read Patterns

Read `context/knowledge/patterns/api-design.md` to understand:
- API endpoint structure
- Request/response format
- Error handling pattern

Read `context/knowledge/patterns/component-structure.md` to understand:
- Component organization
- TypeScript types
- shadcn-ui usage

### Intent Phase Checklist

```
✅ Intent Phase Checklist
├── ☐ Read project-intent.md (understand overall goals)
├── ☐ Read feature-weather-display.md (understand feature requirements)
├── ☐ Read 001-tech-stack.md (understand technology choices)
├── ☐ Read 002-api-integration.md (understand API approach)
├── ☐ Read api-design.md (understand API patterns)
├── ☐ Read component-structure.md (understand component patterns)
└── ☐ Ready to start Build phase!
```

**Progress**: [ ] 0/7 completed

**Time**: ~10-15 minutes

---

## Step 2: Build (Implementation) - 30-45 minutes

**Objective**: AI generates code based on context, human supervises and validates.

### 2.1 Setup Backend Structure

**Prompt 1: Create Backend Structure**
```
Create the backend project structure following @context/decisions/001-tech-stack.md
Use Fastify with TypeScript, setup Swagger documentation following @context/knowledge/patterns/api-design.md
```

**What AI should generate**:
- `backend/` directory
- `backend/package.json` with Fastify, Swagger, TypeScript dependencies
- `backend/tsconfig.json`
- `backend/src/app.ts` (Fastify server setup)
- `backend/src/plugins/swagger.ts` (Swagger configuration)
- `backend/src/plugins/cors.ts` (CORS configuration)
- `.env.example` file

**After generation, manually**:
1. Create `backend/.env` file:
   ```env
   OPENWEATHER_API_KEY=your_api_key_here
   PORT=3000
   ```
2. Get API key from https://openweathermap.org/api (free tier)
3. Install dependencies: `cd backend && npm install`

### 2.2 Implement Weather Service

**Prompt 2: Create Weather Service**
```
Implement weather service following @context/decisions/002-api-integration.md
Create weather.service.ts that calls OpenWeatherMap API
Use Axios for HTTP requests, handle errors properly
```

**What AI should generate**:
- `backend/src/services/weather.service.ts`
- Integration with OpenWeatherMap API
- Error handling
- Data transformation (format response)

### 2.3 Create Weather Route

**Prompt 3: Create Weather Route**
```
Create weather route following @context/intent/feature-weather-display.md
and @context/knowledge/patterns/api-design.md
Route: GET /api/weather?city={city}
Add Swagger documentation for the endpoint
```

**What AI should generate**:
- `backend/src/routes/weather.routes.ts`
- GET `/api/weather` endpoint
- Query parameter validation (city)
- Swagger schema documentation
- Integration with weather service
- Error handling following API design pattern

**After generation**:
1. Register route in `backend/src/app.ts`
2. Test endpoint: `npm run dev` (backend should start on port 3000)
3. Check Swagger docs: http://localhost:3000/docs
4. Test endpoint in Swagger UI with a city (e.g., "London")

### 2.4 Setup Frontend Structure

**Prompt 4: Create Frontend Structure**
```
Create the frontend project structure following @context/decisions/001-tech-stack.md
Use Vite + React + TypeScript, setup shadcn-ui following @context/knowledge/patterns/component-structure.md
```

**What AI should generate**:
- `frontend/` directory
- `frontend/package.json` with Vite, React, TypeScript dependencies
- `frontend/vite.config.ts`
- `frontend/tsconfig.json`
- `frontend/tailwind.config.js` (for shadcn-ui)
- `frontend/postcss.config.js`
- `frontend/src/main.tsx`
- `frontend/src/App.tsx`
- Basic shadcn-ui setup

**After generation, manually**:
1. Install dependencies: `cd frontend && npm install`
2. Initialize shadcn-ui: `npx shadcn-ui@latest init`
   - Choose: TypeScript, Default style, App directory: `src`
3. Add shadcn-ui components:
   ```bash
   npx shadcn-ui@latest add button
   npx shadcn-ui@latest add card
   npx shadcn-ui@latest add input
   ```

### 2.5 Create Weather Components

**Prompt 5: Create Weather Components**
```
Create weather components following @context/intent/feature-weather-display.md
and @context/knowledge/patterns/component-structure.md
Components needed: WeatherCard, WeatherForm, WeatherDisplay
Use shadcn-ui components (Card, Input, Button)
```

**What AI should generate**:
- `frontend/src/components/WeatherCard.tsx` - Display weather info
- `frontend/src/components/WeatherForm.tsx` - Search form
- `frontend/src/components/WeatherDisplay.tsx` - Main component
- TypeScript types in `frontend/src/types/weather.ts`
- Proper use of shadcn-ui components

### 2.6 Create API Client

**Prompt 6: Create API Client**
```
Create API client following @context/knowledge/patterns/api-design.md
Use Axios, create weatherApi service
Base URL: http://localhost:3000/api
```

**What AI should generate**:
- `frontend/src/services/api.ts`
- Axios instance configuration
- `weatherApi.getWeather(city)` function
- TypeScript types for responses

### 2.7 Integrate Frontend with Backend

**Prompt 7: Integrate Frontend**
```
Integrate frontend components with backend API following @context/knowledge/patterns/api-design.md
Connect WeatherForm to API, display results in WeatherCard
Add loading and error states
```

**What AI should generate**:
- Integration in `WeatherDisplay.tsx` or `App.tsx`
- State management (useState for weather data, loading, error)
- API calls using weatherApi service
- Loading state UI
- Error state UI
- Success state (display weather)

**After generation**:
1. Update `App.tsx` to use WeatherDisplay component
2. Test the complete flow

### Build Phase Checklist

```
✅ Build Phase Checklist
├── ☐ Backend structure created
├── ☐ Backend dependencies installed
├── ☐ Weather service implemented
├── ☐ Weather route created with Swagger docs
├── ☐ Backend running on port 3000
├── ☐ Swagger docs accessible at /docs
├── ☐ Frontend structure created
├── ☐ Frontend dependencies installed
├── ☐ shadcn-ui initialized and components added
├── ☐ Weather components created
├── ☐ API client created
├── ☐ Frontend integrated with backend
├── ☐ Frontend running on port 5173
├── ☐ Weather search working end-to-end
└── ☐ Loading and error states working
```

**Progress**: [ ] 0/15 completed

**Time**: ~30-45 minutes

---

## Step 3: Learn (Learning) - 5 minutes

**Objective**: Update context to reflect what was actually built, document learnings.

### 3.1 Update Changelog

Update `context/evolution/changelog.md` with what was implemented:

```markdown
## [Unreleased]

### Added
- Backend: Fastify server with Swagger documentation
- Weather service: OpenWeatherMap API integration
- Weather route: GET /api/weather endpoint
- Frontend: Vite + React + TypeScript setup
- shadcn-ui: Weather components (Card, Form, Display)
- API client: Axios-based service
- Complete weather search and display functionality
```

### 3.2 Verify Implementation Matches Decisions

Check that the implementation follows the decisions:
- ✅ Frontend uses Vite + React + TypeScript + shadcn-ui
- ✅ Backend uses Fastify + Swagger
- ✅ API integration uses OpenWeatherMap
- ✅ API design follows the pattern
- ✅ Components follow the structure pattern

### 3.3 Document Learnings (Optional)

If you learned something during implementation, document it:

```markdown
## Learnings

- shadcn-ui setup was straightforward with Vite
- Fastify Swagger integration was simple
- OpenWeatherMap API was easy to integrate
- TypeScript types helped catch errors early
```

### Learn Phase Checklist

```
✅ Learn Phase Checklist
├── ☐ Changelog updated with implemented features
├── ☐ Implementation verified against decisions
├── ☐ Code follows patterns from knowledge/
├── ☐ Learnings documented (if any)
└── ☐ Context reflects actual implementation
```

**Progress**: [ ] 0/5 completed

**Time**: ~5 minutes

---

## 🧪 Testing the Application

### 1. Start Backend

```bash
cd backend
npm run dev
```

Backend should start on `http://localhost:3000`

**Verify**:
- ✅ Server starts without errors
- ✅ Swagger docs accessible at http://localhost:3000/docs
- ✅ Test endpoint in Swagger UI with city "London"

### 2. Start Frontend

```bash
cd frontend
npm run dev
```

Frontend should start on `http://localhost:5173`

**Verify**:
- ✅ Frontend loads without errors
- ✅ Search form is visible
- ✅ Can search for a city (e.g., "London")
- ✅ Weather information displays correctly
- ✅ Loading state shows while fetching
- ✅ Error state shows if city not found

### 3. Test Complete Flow

1. Open http://localhost:5173
2. Enter a city name (e.g., "London", "São Paulo", "New York")
3. Click search or press Enter
4. Verify weather information displays:
   - City name
   - Temperature
   - Description
   - Icon
5. Try invalid city name to see error state

---

## 📚 Key Takeaways

- **Intent drives everything**: Clear intent makes Build faster
- **Decisions in Intent phase**: Planning decisions early speeds up Build
- **Context is primary**: All details in context files, prompts are simple
- **Simple prompts work**: AI reads complete context, no need for long prompts
- **Learn phase is quick**: Just update changelog and verify

## 🎓 Context Mesh Workflow Summary

1. **Intent** (10-15 min): Read context, understand what to build
2. **Build** (30-45 min): AI generates code, you supervise
3. **Learn** (5 min): Update changelog, verify implementation

**Total Time**: 45-60 minutes

## 📖 How to Use This Example

### For Learning Context Mesh

1. **Read the files in order**:
   - Start with `context/intent/project-intent.md`
   - Then read feature intent
   - Review decisions
   - Check patterns

2. **Follow the workflow**:
   - See how Intent → Build → Learn flows
   - Notice how context drives code generation
   - Observe simple prompts referencing context

3. **Adapt to your project**:
   - Use as a template
   - Modify structure as needed
   - Keep it simple

### For Building the App

Follow the "Step-by-Step Guide" section above to actually build the application using the context provided.

## 🔗 Related Documentation

- [FRAMEWORK.md](../../FRAMEWORK.md) - Complete framework structure
- [GETTING_STARTED.md](../../GETTING_STARTED.md) - Getting started guide
- [EXAMPLES.md](../../EXAMPLES.md) - More examples
- [todo-app-complete](../todo-app-complete/) - Complete example with database, tests, CI/CD

---

**Note**: This is a minimal demonstration example. In a real project, you would have actual code files. The structure and workflow shown here are what you would follow in your own projects.

**Ready to build?** Start with [Step 1: Intent](#step-1-intent-planning---10-15-minutes) above!

