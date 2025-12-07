# Decision: CI/CD Pipeline

## Context

We need a CI/CD pipeline that:
- Validates code quality automatically
- Runs tests on every push and pull request
- Deploys automatically to staging/production
- Works with GitHub (our version control)
- Integrates with Railway (backend) and Vercel (frontend)
- Provides clear feedback on build status

## Decision

**CI/CD Pipeline with GitHub Actions**:

1. **Continuous Integration (CI)**:
   - **Trigger**: On every push and pull request
   - **Backend Workflow**: Install dependencies → Run linter → Run tests → Check coverage
   - **Frontend Workflow**: Install dependencies → Run linter → Run tests → Check coverage → Build
   - **Status**: Shows pass/fail in GitHub PRs

2. **Continuous Deployment (CD)**:
   - **Backend**: Deploy to Railway on push to `main` branch (after CI passes)
   - **Frontend**: Deploy to Vercel on push to `main` branch (after CI passes)
   - **Conditional**: Only deploy if CI passes and branch is `main`

3. **Workflow Structure**:
   - **Separate Workflows**: One for backend (`.github/workflows/backend.yml`), one for frontend (`.github/workflows/frontend.yml`)
   - **Reusable**: Common steps can be extracted to reusable workflows
   - **Matrix Testing**: Test on multiple Node.js versions (18.x, 20.x)

4. **Secrets and Environment Variables**:
   - **GitHub Secrets**: Store sensitive data (API keys, tokens)
   - **Railway Token**: For backend deployment
   - **Vercel Token**: For frontend deployment
   - **Environment Variables**: Set in Railway and Vercel dashboards

5. **Testing CI/CD Locally**:
   - **Tool**: Use `act` (https://github.com/nektos/act) to run GitHub Actions locally
   - **Limitation**: Some actions may not work locally (deployment steps)
   - **Purpose**: Validate workflow syntax and basic functionality

## Rationale

1. **GitHub Actions**: Native to GitHub, free for public repos, excellent integration
2. **Separate Workflows**: Clear separation, easier to debug, independent execution
3. **Automated Testing**: Catches issues before deployment
4. **Automated Deployment**: Reduces manual work, faster delivery
5. **Conditional Deployment**: Only deploy stable code from main branch

## Alternatives Considered

### Alternative 1: GitLab CI/CD
- **Pros**: Powerful, integrated with GitLab
- **Cons**: Requires GitLab, not using GitLab
- **Why Not Chosen**: Using GitHub, GitHub Actions is native

### Alternative 2: Jenkins
- **Pros**: Very flexible, powerful
- **Cons**: Requires server setup, more complex
- **Why Not Chosen**: GitHub Actions is simpler and sufficient

### Alternative 3: Manual Deployment
- **Pros**: Full control, no automation complexity
- **Cons**: Error-prone, slow, no automated testing
- **Why Not Chosen**: Automation is essential for quality and speed

## Implementation Details

### Backend Workflow (`.github/workflows/backend.yml`)

**Structure**:
```yaml
name: Backend CI/CD

on:
  push:
    branches: [main, develop]
    paths:
      - 'backend/**'
      - '.github/workflows/backend.yml'
  pull_request:
    branches: [main, develop]
    paths:
      - 'backend/**'
      - '.github/workflows/backend.yml'

jobs:
  test:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: ./backend
    
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
          cache-dependency-path: backend/package-lock.json
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run linter
        run: npm run lint
      
      - name: Run tests
        run: npm test -- --coverage --ci
      
      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          file: ./backend/coverage/coverage-final.json
          flags: backend

  deploy:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '18'
      
      - name: Deploy to Railway
        uses: bervProject/railway-deploy@v1.0.0
        with:
          railway_token: ${{ secrets.RAILWAY_TOKEN }}
          service: backend
```

### Frontend Workflow (`.github/workflows/frontend.yml`)

**Structure**:
```yaml
name: Frontend CI/CD

on:
  push:
    branches: [main, develop]
    paths:
      - 'frontend/**'
      - '.github/workflows/frontend.yml'
  pull_request:
    branches: [main, develop]
    paths:
      - 'frontend/**'
      - '.github/workflows/frontend.yml'

jobs:
  test:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: ./frontend
    
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run linter
        run: npm run lint
      
      - name: Run tests
        run: npm test -- --coverage --ci
      
      - name: Build
        run: npm run build
        env:
          VITE_API_URL: ${{ secrets.VITE_API_URL }}
      
      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          file: ./frontend/coverage/coverage-final.json
          flags: frontend

  deploy:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: '--prod'
```

### Required GitHub Secrets

**Backend**:
- `RAILWAY_TOKEN`: Railway API token for deployment

**Frontend**:
- `VERCEL_TOKEN`: Vercel API token
- `VERCEL_ORG_ID`: Vercel organization ID
- `VERCEL_PROJECT_ID`: Vercel project ID
- `VITE_API_URL`: Frontend API URL (for build)

### Testing CI/CD Locally

**Install `act`**:
```bash
# macOS
brew install act

# Linux
curl https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash

# Windows (via Chocolatey)
choco install act-cli
```

**Run Workflow Locally**:
```bash
# Test backend workflow
act -W .github/workflows/backend.yml

# Test frontend workflow
act -W .github/workflows/frontend.yml

# Run specific job
act -j test -W .github/workflows/backend.yml

# Use secrets
act -W .github/workflows/backend.yml --secret RAILWAY_TOKEN=your_token
```

**Limitations**:
- Deployment steps may not work locally (require actual services)
- Some actions may not be compatible with `act`
- Use for syntax validation and basic testing

## Outcomes

**After Implementation**:
- ✅ Automated testing catches issues early
- ✅ CI/CD pipeline reduces manual deployment work
- ✅ Clear build status in GitHub PRs
- ✅ Fast feedback on code changes
- ⚠️ Some edge cases require manual testing (acceptable)

**Lessons Learned**:
- Separate workflows are easier to maintain
- Conditional deployment prevents broken deployments
- Local testing with `act` is helpful but limited
- Secrets management is critical for security

## Related

- [Feature: CI/CD](../intent/feature-ci-cd.md)
- [Decision: Testing Strategy](005-testing-strategy.md)
- [Decision: Deployment Platforms](007-deployment-platforms.md)
- [Pattern: GitHub Actions](../knowledge/patterns/github-actions.md)

## Status

- **Created**: 2025-12-06 (Phase: Intent)
- **Status**: Accepted

