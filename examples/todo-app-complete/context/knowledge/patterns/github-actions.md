# Pattern: GitHub Actions Workflows

## Description

GitHub Actions workflow pattern for CI/CD pipeline. This pattern defines how to structure workflows for automated testing, building, and deployment.

## Pattern

### Workflow Structure

**File**: `.github/workflows/[name].yml`

```yaml
name: Workflow Name

on:
  push:
    branches: [main, develop]
    paths:
      - 'path/to/watch/**'
  pull_request:
    branches: [main, develop]
    paths:
      - 'path/to/watch/**'

jobs:
  job-name:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: ./path/to/working/dir
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
          cache-dependency-path: path/to/package-lock.json
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run linter
        run: npm run lint
      
      - name: Run tests
        run: npm test -- --coverage --ci
      
      - name: Build
        run: npm run build
        env:
          ENV_VAR: ${{ secrets.ENV_VAR }}
```

### Key Components

1. **Triggers** (`on`):
   - `push`: Run on code push
   - `pull_request`: Run on PR creation/update
   - `paths`: Only run when specific paths change
   - `branches`: Only run for specific branches

2. **Jobs**:
   - Independent units of work
   - Run in parallel by default
   - Can depend on other jobs (`needs`)

3. **Steps**:
   - Individual commands or actions
   - Run sequentially within a job
   - Can use actions (reusable code) or run commands

4. **Secrets**:
   - Stored in GitHub repository settings
   - Accessed via `${{ secrets.SECRET_NAME }}`
   - Never exposed in logs

### Backend Workflow Pattern

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

### Frontend Workflow Pattern

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

## When to Use

- Automated testing on every push
- Automated deployment to production
- Quality checks (linting, coverage)
- Build validation
- Consistent deployment process

## Benefits

- **Automation**: No manual deployment steps
- **Quality**: Tests run automatically
- **Speed**: Fast feedback on code changes
- **Consistency**: Same process every time
- **Visibility**: Build status in GitHub PRs

## Best Practices

1. **Separate Workflows**: One for backend, one for frontend
2. **Path Filtering**: Only run when relevant files change
3. **Conditional Deployment**: Only deploy from `main` branch
4. **Job Dependencies**: Deploy only if tests pass (`needs: test`)
5. **Secrets Management**: Never commit secrets, use GitHub Secrets
6. **Caching**: Cache dependencies for faster builds
7. **Matrix Testing**: Test on multiple Node.js versions if needed

## Testing Locally

Use `act` to test workflows locally:

```bash
# Install act
brew install act  # macOS
# or download from https://github.com/nektos/act

# Run workflow
act -W .github/workflows/backend.yml

# Run specific job
act -j test -W .github/workflows/backend.yml

# Use secrets
act -W .github/workflows/backend.yml --secret RAILWAY_TOKEN=your_token
```

**Limitations**:
- Deployment steps may not work locally
- Some actions may not be compatible
- Use for syntax validation and basic testing

## Required Secrets

**Backend**:
- `RAILWAY_TOKEN`: Railway API token

**Frontend**:
- `VERCEL_TOKEN`: Vercel API token
- `VERCEL_ORG_ID`: Vercel organization ID
- `VERCEL_PROJECT_ID`: Vercel project ID
- `VITE_API_URL`: Frontend API URL (for build)

## Related

- [Decision: CI/CD Pipeline](../../decisions/006-ci-cd-pipeline.md)
- [Decision: Deployment Platforms](../../decisions/007-deployment-platforms.md)
- [Feature: CI/CD](../../intent/feature-ci-cd.md)

