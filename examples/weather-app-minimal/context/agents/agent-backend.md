# Agent: Backend - Weather App

## Purpose
Implement the weather service and API route with Open-Meteo integration (geocoding + weather).

## Context Files to Load
- @context/intent/feature-weather-display.md
- @context/decisions/002-api-integration.md
- @context/knowledge/patterns/api-design.md

## Scope
- **Allowed directories:** `backend/src/`
- **Prohibited:** Don't modify frontend

## Execution Steps

1. **Create Weather Service**
   - Create `backend/src/services/weather.service.ts`
   - Implement Open-Meteo Geocoding API call (city name → coordinates)
   - Implement Open-Meteo Weather API call (coordinates → weather)
   - Map WMO weather codes to descriptions and icons
   - Handle API errors gracefully
   - Transform response to simplified format

2. **Create Weather Route**
   - Create `backend/src/routes/weather.routes.ts`
   - Implement `GET /api/weather?city={city}`
   - Add Swagger schema documentation
   - Register route in `app.ts`

3. **Create Types**
   - Create `backend/src/types/weather.ts`
   - Define request/response interfaces
   - Define geocoding and weather API response types

## Expected Output

```
backend/src/
├── services/
│   └── weather.service.ts
├── routes/
│   └── weather.routes.ts
├── types/
│   └── weather.ts
├── plugins/
│   ├── swagger.ts
│   └── cors.ts
└── app.ts (updated with routes)
```

## API Response Format

```typescript
// GET /api/weather?city=London
{
  "success": true,
  "data": {
    "city": "London",
    "country": "United Kingdom",
    "temperature": 15.2,
    "description": "Overcast",
    "icon": "☁️",
    "windSpeed": 8.5,
    "windDirection": 180
  }
}
```

## Implementation Notes

1. **Geocoding First**: Call `https://geocoding-api.open-meteo.com/v1/search?name={city}&count=1`
2. **Weather Second**: Use coordinates from geocoding to call `https://api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&current_weather=true`
3. **Weather Code Mapping**: Map WMO weather codes (0-99) to descriptions and icons (see 002-api-integration.md)
4. **Error Handling**: Handle cases where city is not found or API fails

## Definition of Done
- [ ] Weather service calls Open-Meteo Geocoding API
- [ ] Weather service calls Open-Meteo Weather API
- [ ] Weather codes are mapped to descriptions and icons
- [ ] Weather route returns weather data
- [ ] Swagger documentation shows at `/docs`
- [ ] Error handling for invalid city
- [ ] `pnpm run dev` starts server on port 3000
- [ ] Test: `curl "http://localhost:3000/api/weather?city=London"` returns data

## After Completion
Test the API in Swagger UI: http://localhost:3000/docs

Then proceed to: **@context/agents/agent-frontend.md**

