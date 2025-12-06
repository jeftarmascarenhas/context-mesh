# Pattern: Docker Compose Configuration

## Description

Docker Compose pattern for running PostgreSQL database in development. This pattern provides a consistent database environment without requiring local PostgreSQL installation.

## Pattern

### File Structure

**File**: `docker-compose.yml` (project root)

```yaml
version: '3.8'

services:
  postgres:
    image: postgres:15-alpine
    container_name: todo-app-postgres
    environment:
      POSTGRES_USER: todoapp
      POSTGRES_PASSWORD: todoapp_password
      POSTGRES_DB: todoapp
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U todoapp"]
      interval: 10s
      timeout: 5s
      retries: 5

volumes:
  postgres_data:
```

### Key Configuration

1. **Image**: `postgres:15-alpine` - Lightweight PostgreSQL 15
2. **Container Name**: `todo-app-postgres` - Easy to identify
3. **Environment Variables**:
   - `POSTGRES_USER`: Database user
   - `POSTGRES_PASSWORD`: Database password
   - `POSTGRES_DB`: Database name
4. **Ports**: `5432:5432` - Expose PostgreSQL on default port
5. **Volumes**: `postgres_data` - Persistent data storage
6. **Health Check**: Ensures database is ready before use

### Connection String

```
DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp
```

## Commands

### Start Database
```bash
docker-compose up -d
```
- `-d`: Run in detached mode (background)
- Starts PostgreSQL container

### Stop Database
```bash
docker-compose down
```
- Stops and removes containers
- Keeps volumes (data persists)

### View Logs
```bash
docker-compose logs -f postgres
```
- `-f`: Follow logs (real-time)
- Shows PostgreSQL logs

### Reset Database
```bash
docker-compose down -v
docker-compose up -d
```
- `-v`: Remove volumes (deletes all data)
- Recreates fresh database

### Check Status
```bash
docker-compose ps
```
- Shows running containers

### Execute SQL
```bash
docker-compose exec postgres psql -U todoapp -d todoapp
```
- Opens PostgreSQL CLI
- Can run SQL commands

## When to Use

- Local development environment
- Team consistency (same database version)
- Easy database reset for testing
- No local PostgreSQL installation needed

## Benefits

- **Consistency**: Same database version for all developers
- **Simplicity**: No PostgreSQL installation required
- **Isolation**: Database runs in container, doesn't affect system
- **Easy Reset**: Remove volume to start fresh
- **Portable**: Works on macOS, Linux, Windows

## Environment Variables

Create `.env` file (optional, for customization):

```env
POSTGRES_USER=todoapp
POSTGRES_PASSWORD=todoapp_password
POSTGRES_DB=todoapp
POSTGRES_PORT=5432
```

Update `docker-compose.yml` to use variables:

```yaml
environment:
  POSTGRES_USER: ${POSTGRES_USER:-todoapp}
  POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:-todoapp_password}
  POSTGRES_DB: ${POSTGRES_DB:-todoapp}
ports:
  - "${POSTGRES_PORT:-5432}:5432"
```

## Troubleshooting

### Port Already in Use
```bash
# Check what's using port 5432
lsof -i :5432  # macOS/Linux
netstat -ano | findstr :5432  # Windows

# Change port in docker-compose.yml
ports:
  - "5433:5432"  # Use 5433 instead
```

### Container Won't Start
```bash
# Check logs
docker-compose logs postgres

# Remove and recreate
docker-compose down -v
docker-compose up -d
```

### Can't Connect to Database
```bash
# Check if container is running
docker-compose ps

# Check health status
docker-compose exec postgres pg_isready -U todoapp

# Verify connection string
# Should match docker-compose.yml values
```

## Related

- [Decision: Dev Environment](../../decisions/004-dev-environment.md)
- [Decision: Database Schema](../../decisions/003-database-schema.md)

