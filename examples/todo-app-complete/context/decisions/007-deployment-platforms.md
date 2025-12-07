# Decision: Deployment Platforms

## Context

We need to deploy the Todo application to production. Requirements:
- Free tier available (budget constraint)
- Easy setup and configuration
- Automatic deployments from GitHub
- Support for Node.js backend and React frontend
- PostgreSQL database support
- Environment variable management
- Custom domains (optional)

## Decision

**Deployment Platforms**:

1. **Backend**: Railway
   - **Why**: Free tier, easy setup, automatic deployments, PostgreSQL support
   - **Features**: GitHub integration, environment variables, logs, metrics
   - **Database**: Railway PostgreSQL or external (Supabase, Neon)

2. **Frontend**: Vercel
   - **Why**: Free tier, excellent React support, automatic deployments, CDN
   - **Features**: GitHub integration, preview deployments, analytics
   - **Build**: Automatic from GitHub, supports Vite

3. **Database Options**:
   - **Option A**: Railway PostgreSQL (included, easy)
   - **Option B**: External PostgreSQL (Supabase, Neon) - more features, separate service
   - **Decision**: Start with Railway PostgreSQL, can migrate later

## Rationale

1. **Railway for Backend**:
   - Free tier: $5 credit/month (sufficient for MVP)
   - One-click deploy from GitHub
   - Built-in PostgreSQL option
   - Environment variables management
   - Logs and metrics included
   - Simple pricing model

2. **Vercel for Frontend**:
   - Free tier: Unlimited for personal projects
   - Optimized for React/Next.js
   - Automatic CDN and optimizations
   - Preview deployments for PRs
   - Excellent developer experience
   - Fast global CDN

3. **Separate Services**:
   - Backend and frontend can scale independently
   - Different deployment strategies if needed
   - Clear separation of concerns

## Alternatives Considered

### Alternative 1: Heroku
- **Pros**: Well-known, easy setup
- **Cons**: No free tier anymore, more expensive
- **Why Not Chosen**: Railway is free and simpler

### Alternative 2: Render
- **Pros**: Free tier, good features
- **Cons**: Slower free tier, more complex setup
- **Why Not Chosen**: Railway has better free tier and simpler setup

### Alternative 3: AWS/GCP/Azure
- **Pros**: Very powerful, scalable
- **Cons**: Complex setup, no free tier for production, overkill for MVP
- **Why Not Chosen**: Too complex for MVP, Railway/Vercel are simpler

### Alternative 4: Vercel for Both (Full-Stack)
- **Pros**: Single platform, simpler
- **Cons**: Backend functions have limitations, not ideal for Express apps
- **Why Not Chosen**: Railway is better for Express backend, Vercel for frontend

## Implementation Details

### Railway Setup (Backend)

**Step 1: Create Railway Account**
1. Go to https://railway.app
2. Sign up with GitHub
3. Create new project

**Step 2: Deploy Backend**
1. Click "New Project"
2. Select "Deploy from GitHub repo"
3. Choose repository and `backend` directory
4. Railway detects Node.js and auto-configures

**Step 3: Add PostgreSQL**
1. Click "New" → "Database" → "Add PostgreSQL"
2. Railway creates database and sets `DATABASE_URL` automatically

**Step 4: Environment Variables**
Set in Railway dashboard:
- `NODE_ENV=production`
- `JWT_SECRET=<generate-secure-secret>`
- `JWT_EXPIRES_IN=7d`
- `PORT=3000` (Railway sets this automatically)
- `DATABASE_URL` (set automatically by Railway)

**Step 5: Custom Domain (Optional)**
1. Go to Settings → Domains
2. Add custom domain
3. Railway provides SSL certificate automatically

**Railway CLI (Optional)**:
```bash
# Install
npm i -g @railway/cli

# Login
railway login

# Link project
railway link

# Deploy
railway up

# View logs
railway logs
```

### Vercel Setup (Frontend)

**Step 1: Create Vercel Account**
1. Go to https://vercel.com
2. Sign up with GitHub
3. Import repository

**Step 2: Configure Project**
1. Select repository
2. Root directory: `frontend`
3. Framework preset: Vite
4. Build command: `npm run build`
5. Output directory: `dist`

**Step 3: Environment Variables**
Set in Vercel dashboard:
- `VITE_API_URL=https://your-backend.railway.app/api/v1`

**Step 4: Deploy**
1. Vercel automatically deploys on push to `main`
2. Preview deployments for PRs
3. Production URL: `https://your-project.vercel.app`

**Vercel CLI (Optional)**:
```bash
# Install
npm i -g vercel

# Login
vercel login

# Deploy
vercel

# Deploy to production
vercel --prod
```

### Database Options

**Option A: Railway PostgreSQL** (Recommended for MVP)
- Included with Railway project
- Automatic `DATABASE_URL` configuration
- Easy to manage
- Sufficient for MVP

**Option B: External PostgreSQL** (For production)
- **Supabase**: Free tier, 500MB database, good features
- **Neon**: Free tier, serverless PostgreSQL, good performance
- Requires separate setup and connection string

### Environment Variables Summary

**Backend (Railway)**:
```
NODE_ENV=production
DATABASE_URL=<auto-set-by-railway>
JWT_SECRET=<your-secret-key>
JWT_EXPIRES_IN=7d
PORT=3000
```

**Frontend (Vercel)**:
```
VITE_API_URL=https://your-backend.railway.app/api/v1
```

### Deployment Flow

1. **Developer pushes to `main` branch**
2. **GitHub Actions runs CI** (tests, lint, build)
3. **If CI passes**:
   - Backend: Railway auto-deploys (via GitHub integration)
   - Frontend: Vercel auto-deploys (via GitHub integration)
4. **Deployment completes** in ~2-5 minutes
5. **Application is live**

### Monitoring and Logs

**Railway**:
- View logs in Railway dashboard
- Metrics: CPU, memory, requests
- Alerts: Email notifications on errors

**Vercel**:
- View logs in Vercel dashboard
- Analytics: Page views, performance
- Alerts: Email notifications on build failures

## Outcomes

**After Implementation**:
- ✅ Railway deployment was straightforward
- ✅ Vercel deployment was automatic and fast
- ✅ Free tiers sufficient for MVP
- ✅ Automatic deployments from GitHub work well
- ✅ Environment variables easy to manage
- ⚠️ Railway free tier has limits (acceptable for MVP)

**Lessons Learned**:
- Railway is excellent for Node.js backends
- Vercel is perfect for React frontends
- Separate services allow independent scaling
- Free tiers are sufficient for MVP and small projects

## Related

- [Decision: CI/CD Pipeline](006-ci-cd-pipeline.md)
- [Decision: Dev Environment](004-dev-environment.md)
- [Project Intent](../intent/project-intent.md)

## Status

- **Created**: 2025-12-06 (Phase: Intent)
- **Status**: Accepted

