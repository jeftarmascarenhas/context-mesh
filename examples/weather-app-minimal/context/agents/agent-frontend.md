# Agent: Frontend - Weather App

## Purpose
Implement the weather UI components and API integration.

## Context Files to Load
- @context/intent/feature-weather-display.md
- @context/knowledge/patterns/component-structure.md
- @context/decisions/001-tech-stack.md

## Scope
- **Allowed directories:** `frontend/src/`
- **Prohibited:** Don't modify backend

## Execution Steps

1. **Create API Client**
   - Create `frontend/src/services/api.ts`
   - Configure Axios with base URL `http://localhost:3000/api`
   - Create `getWeather(city)` function

2. **Create Types**
   - Create `frontend/src/types/weather.ts`
   - Define Weather interface

3. **Create Weather Components**
   - Create `frontend/src/components/WeatherForm.tsx` (search input + button)
   - Create `frontend/src/components/WeatherCard.tsx` (display weather data)
   - Create `frontend/src/components/WeatherDisplay.tsx` (main container)

4. **Update App.tsx**
   - Import and use WeatherDisplay component
   - Add app title and styling

## Expected Output

```
frontend/src/
├── components/
│   ├── ui/                    # shadcn-ui components
│   ├── WeatherForm.tsx
│   ├── WeatherCard.tsx
│   └── WeatherDisplay.tsx
├── services/
│   └── api.ts
├── types/
│   └── weather.ts
├── App.tsx (updated)
└── main.tsx
```

## Component Behavior

**WeatherForm**:
- Input field for city name
- Search button
- Triggers search on Enter key or button click

**WeatherCard**:
- Displays city name and country
- Shows temperature (°C)
- Shows weather description
- Shows weather icon
- Shows humidity and wind speed

**WeatherDisplay**:
- Contains WeatherForm and WeatherCard
- Manages state: loading, error, weather data
- Shows loading spinner while fetching
- Shows error message if search fails

## Definition of Done
- [ ] API client calls backend correctly
- [ ] WeatherForm accepts city input
- [ ] WeatherCard displays weather data
- [ ] Loading state shows spinner
- [ ] Error state shows message
- [ ] UI uses shadcn-ui components (Card, Input, Button)
- [ ] `pnpm run dev` starts frontend on port 5173
- [ ] Search works end-to-end (type city → see weather)

## After Completion
Test the complete flow:
1. Start backend: `cd backend && pnpm run dev`
2. Start frontend: `cd frontend && pnpm run dev`
3. Open http://localhost:5173
4. Search for "London" and verify weather displays

Project complete! Update @context/evolution/changelog.md with what was built.

