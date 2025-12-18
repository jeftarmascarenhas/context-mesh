# Decision: Technology Stack

## Context

We need to choose the technology stack for the Weather App minimal example. The stack must:
- Support rapid development with AI assistance
- Be modern and maintainable
- Work well with TypeScript
- Be minimal (no database, no complex setup)
- Use current, stable packages
- Demonstrate best practices

## Decision

**Frontend**:
- **Vite**: Fast build tool, excellent DX, great for React
- **React 18+**: Industry standard, great ecosystem
- **TypeScript**: Type safety, better AI code generation
- **shadcn-ui**: Modern, accessible component library
- **Tailwind CSS**: Utility-first CSS (via shadcn-ui)
- **Axios**: HTTP client for API calls

**Backend**:
- **Node.js 20+**: Latest LTS version
- **Fastify**: Fast, low overhead web framework
- **@fastify/swagger**: API documentation
- **@fastify/swagger-ui**: Swagger UI interface
- **@fastify/cors**: CORS support for frontend
- **Axios**: HTTP client for external API calls
- **TypeScript**: Type safety throughout

**External Services**:
- **Open-Meteo API**: Weather data provider (free, no API key required)

**Development Tools**:
- **TypeScript**: For both frontend and backend
- **tsx**: TypeScript execution for backend
- **Git**: Version control (optional but recommended)

## Rationale

1. **Vite**: 
   - Fastest build tool available
   - Excellent HMR (Hot Module Replacement)
   - Simple configuration
   - Great for learning and development

2. **React + TypeScript**:
   - Industry standard
   - Excellent AI tool support
   - Type safety prevents errors
   - Great ecosystem

3. **shadcn-ui**:
   - Modern, accessible components
   - Copy-paste components (not a dependency)
   - Built on Radix UI primitives
   - Tailwind CSS integration
   - Perfect for quick, beautiful UIs

4. **Fastify**:
   - Faster than Express
   - Built-in TypeScript support
   - Excellent plugin ecosystem
   - Low overhead
   - Great for APIs

5. **Swagger**:
   - Automatic API documentation
   - Interactive testing interface
   - Great for learning and development
   - Industry standard

6. **Open-Meteo**:
   - Free and open source weather API
   - No API key required
   - Good documentation
   - Reliable service
   - Perfect for learning and development

## Alternatives Considered

### Alternative 1: Next.js (Full-stack)
- **Pros**: Built-in API routes, SSR, great DX
- **Cons**: More complex, might be overkill for minimal example
- **Why Not Chosen**: Vite + Fastify is simpler and shows separation of concerns

### Alternative 2: Express instead of Fastify
- **Pros**: More popular, larger ecosystem
- **Cons**: Slower, more boilerplate
- **Why Not Chosen**: Fastify is faster and has better TypeScript support

### Alternative 3: Material-UI or Ant Design
- **Pros**: Complete component libraries
- **Cons**: Heavy dependencies, less flexible
- **Why Not Chosen**: shadcn-ui is lighter, more flexible, copy-paste approach

### Alternative 4: Fetch API instead of Axios
- **Pros**: Native, no dependency
- **Cons**: Less features, more boilerplate
- **Why Not Chosen**: Axios is simpler and more feature-rich

## Implementation Details

### Frontend Package Versions
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "axios": "^1.6.7"
  },
  "devDependencies": {
    "@types/react": "^18.2.48",
    "@types/react-dom": "^18.2.18",
    "@vitejs/plugin-react": "^4.2.1",
    "typescript": "^5.3.3",
    "vite": "^5.0.11",
    "tailwindcss": "^3.4.1",
    "autoprefixer": "^10.4.17",
    "postcss": "^8.4.33"
  }
}
```

### Backend Package Versions
```json
{
  "dependencies": {
    "fastify": "^4.26.0",
    "@fastify/swagger": "^8.15.0",
    "@fastify/swagger-ui": "^2.1.0",
    "@fastify/cors": "^9.0.1",
    "axios": "^1.6.7"
  },
  "devDependencies": {
    "@types/node": "^20.11.0",
    "typescript": "^5.3.3",
    "tsx": "^4.7.1"
  }
}
```
```ts
export default async function corsPlugin(fastify: FastifyInstance) {
  await fastify.register(cors, {
    origin: "*", // Allow all origins in development
  });
}
// use the plugins in app.ts in right order
sweggerPlugin(fastify)
corsPlugin(fastify)
````

### Project Structure
```
weather-app-minimal/
├── frontend/          # Vite + React + shadcn-ui
│   ├── src/
│   │   ├── components/
│   │   ├── services/
│   │   ├── types/
│   │   └── App.tsx
│   └── package.json
└── backend/           # Fastify + Swagger
    ├── src/
    │   ├── routes/
    │   ├── services/
    │   ├── plugins/
    │   └── app.ts
    └── package.json
```

## Outcomes

**After Implementation**:
- ✅ Vite provided fast development experience
- ✅ shadcn-ui made UI development quick and beautiful
- ✅ Fastify was fast and easy to use
- ✅ Swagger made API testing simple
- ✅ TypeScript caught errors early
- ✅ Stack worked well with AI code generation

**Lessons Learned**:
- Minimal stack is perfect for learning Context Mesh
- shadcn-ui is excellent for quick, modern UIs
- Fastify + Swagger is great for API development
- TypeScript is essential for AI-assisted development

## Related

- [Project Intent](../intent/project-intent.md)
- [Feature: Weather Display](../intent/feature-weather-display.md)
- [Decision: API Integration](002-api-integration.md)

## Status

- **Created**: 2025-12-07 (Phase: Intent)
- **Status**: Accepted

