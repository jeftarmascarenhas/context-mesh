# Agent: CI/CD - Todo App

## Purpose
Create GitHub Actions workflows for continuous integration and deployment.

## Context Files to Load
- @context/intent/feature-ci-cd.md
- @context/decisions/006-ci-cd-pipeline.md
- @context/decisions/007-deployment-platforms.md
- @context/knowledge/patterns/github-actions.md

## Scope
- **Allowed:** `.github/workflows/`, root config files
- **Prohibited:** Modify application code

## Execution Steps

1. **Create Backend Workflow**
   - Create `.github/workflows/backend.yml`
   - Trigger on push/PR to main
   - Steps: checkout, setup Node, install, lint, test
   - Optional: deploy to Railway on main push

2. **Create Frontend Workflow**
   - Create `.github/workflows/frontend.yml`
   - Trigger on push/PR to main
   - Steps: checkout, setup Node, install, lint, test, build
   - Optional: deploy to Vercel on main push

## Expected Output

**.github/workflows/backend.yml**
```yaml
name: Backend CI

on:
  push:
    branches: [main]
    paths: ['backend/**']
  pull_request:
    branches: [main]
    paths: ['backend/**']

jobs:
  test:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: backend
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
          cache-dependency-path: backend/package-lock.json
      - run: npm ci
      - run: npm run lint
      - run: npm test -- --coverage
```

**.github/workflows/frontend.yml**
```yaml
name: Frontend CI

on:
  push:
    branches: [main]
    paths: ['frontend/**']
  pull_request:
    branches: [main]
    paths: ['frontend/**']

jobs:
  test:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: frontend
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json
      - run: npm ci
      - run: npm run lint
      - run: npm test -- --coverage
      - run: npm run build
```

## Definition of Done
- [ ] Backend workflow created
- [ ] Frontend workflow created
- [ ] Workflows trigger on push/PR
- [ ] Tests run in CI
- [ ] Build step passes

## Verification
```bash
# Test locally with act (if installed)
act -W .github/workflows/backend.yml -j test
act -W .github/workflows/frontend.yml -j test

# Or push to GitHub and check Actions tab
git push origin main
# Check: https://github.com/YOUR_USER/YOUR_REPO/actions
```

## GitHub Secrets Required

For deployment (optional):
- `RAILWAY_TOKEN` - Railway API token
- `VERCEL_TOKEN` - Vercel API token
- `VERCEL_ORG_ID` - Vercel organization ID
- `VERCEL_PROJECT_ID` - Vercel project ID
- `VITE_API_URL` - Backend API URL

## After Completion
All phases complete! Run final tests and deploy.

