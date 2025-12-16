# Decision: API Integration - Open-Meteo

## Context

We need to integrate with an external weather API to fetch weather data. Requirements:
- Free tier available (no API key required)
- Stable and reliable service
- Good documentation
- Simple integration
- Returns current weather data

## Decision

**Use Open-Meteo API** for weather data:
- **Geocoding Endpoint**: `https://geocoding-api.open-meteo.com/v1/search`
- **Weather Endpoint**: `https://api.open-meteo.com/v1/forecast`
- **Method**: GET
- **Authentication**: None required (free, open source)
- **Response Format**: JSON
- **Units**: Metric (Celsius)

**Integration Approach**:
- Backend calls Open-Meteo Geocoding API to get coordinates from city name
- Backend calls Open-Meteo Weather API with coordinates
- Frontend calls our backend API
- Backend acts as proxy/aggregator
- Error handling for API failures
- Input validation (city name)

## Rationale

1. **Open-Meteo**:
   - No API key required (free, open source)
   - Stable and reliable service
   - Good documentation
   - Open source and community-driven
   - Sufficient for development and learning

2. **Backend Proxy**:
   - Allows data transformation/formatting
   - Centralized error handling
   - Can add caching later (if needed)
   - Better control over API usage
   - Handles geocoding + weather in one flow

3. **Two-Step Process (Geocoding + Weather)**:
   - Geocoding API converts city name to coordinates
   - Weather API uses coordinates for accurate weather data
   - Standard approach for weather APIs that use coordinates

4. **Metric Units**:
   - Celsius is standard in most countries
   - Easier to understand for users
   - Can add unit conversion later

## Alternatives Considered

### Alternative 1: OpenWeatherMap API
- **Pros**: Most known, widely used, good documentation
- **Cons**: Requires API key (free tier: 1,000 calls/day)
- **Why Not Chosen**: Open-Meteo is free without API key, simpler for learning

### Alternative 2: WeatherAPI.com
- **Pros**: Good free tier, good documentation
- **Cons**: Requires API key, less known than OpenWeatherMap
- **Why Not Chosen**: Open-Meteo doesn't require API key

### Alternative 3: Frontend calls Open-Meteo directly
- **Pros**: Simpler architecture
- **Cons**: CORS issues, less control, harder to transform data
- **Why Not Chosen**: Backend proxy provides better control and data transformation

## Implementation Details

### API Endpoint Structure

**Our Backend Endpoint**:
```
GET /api/weather?city={cityName}
```

**Open-Meteo Geocoding Endpoint** (Step 1):
```
GET https://geocoding-api.open-meteo.com/v1/search?name={city}&count=1
```

**Open-Meteo Weather Endpoint** (Step 2):
```
GET https://api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&current_weather=true
```

### Request Flow Example
```typescript
// Step 1: Get coordinates from city name
GET https://geocoding-api.open-meteo.com/v1/search?name=London&count=1

// Response:
{
  "results": [{
    "name": "London",
    "country": "United Kingdom",
    "latitude": 51.5074,
    "longitude": -0.1278
  }]
}

// Step 2: Get weather using coordinates
GET https://api.open-meteo.com/v1/forecast?latitude=51.5074&longitude=-0.1278&current_weather=true

// Response:
{
  "current_weather": {
    "temperature": 15.2,
    "windspeed": 8.5,
    "winddirection": 180,
    "weathercode": 3,
    "time": "2024-01-15T12:00"
  }
}
```

### Our Backend Response Format
```json
{
  "success": true,
  "data": {
    "city": "London",
    "country": "United Kingdom",
    "temperature": 15.2,
    "windSpeed": 8.5,
    "windDirection": 180,
    "weatherCode": 3
  }
}
```

**Note**: Open-Meteo uses WMO weather codes (0-99) instead of icon strings. We'll map these codes to descriptions and icons in our backend.

### Error Handling

**City Not Found** (404):
```json
{
  "success": false,
  "error": {
    "code": "CITY_NOT_FOUND",
    "message": "City not found. Please check the city name."
  }
}
```

**API Error** (500):
```json
{
  "success": false,
  "error": {
    "code": "API_ERROR",
    "message": "Unable to fetch weather data. Please try again later."
  }
}
```

### Environment Variables

**Backend `.env`**:
```env
PORT=3000
```

**Note**: No API key required for Open-Meteo!

### Weather Code Mapping

Open-Meteo uses WMO weather codes. We'll map them to descriptions:

```typescript
const weatherCodes: Record<number, { description: string; icon: string }> = {
  0: { description: "Clear sky", icon: "☀️" },
  1: { description: "Mainly clear", icon: "🌤️" },
  2: { description: "Partly cloudy", icon: "⛅" },
  3: { description: "Overcast", icon: "☁️" },
  45: { description: "Foggy", icon: "🌫️" },
  48: { description: "Depositing rime fog", icon: "🌫️" },
  51: { description: "Light drizzle", icon: "🌦️" },
  53: { description: "Moderate drizzle", icon: "🌦️" },
  55: { description: "Dense drizzle", icon: "🌦️" },
  56: { description: "Light freezing drizzle", icon: "🌨️" },
  57: { description: "Dense freezing drizzle", icon: "🌨️" },
  61: { description: "Slight rain", icon: "🌧️" },
  63: { description: "Moderate rain", icon: "🌧️" },
  65: { description: "Heavy rain", icon: "🌧️" },
  71: { description: "Slight snow", icon: "❄️" },
  73: { description: "Moderate snow", icon: "❄️" },
  75: { description: "Heavy snow", icon: "❄️" },
  80: { description: "Slight rain showers", icon: "🌦️" },
  81: { description: "Moderate rain showers", icon: "🌦️" },
  82: { description: "Violent rain showers", icon: "🌧️" },
  85: { description: "Slight snow showers", icon: "🌨️" },
  86: { description: "Heavy snow showers", icon: "🌨️" },
  95: { description: "Thunderstorm", icon: "⛈️" },
  96: { description: "Thunderstorm with slight hail", icon: "⛈️" },
  99: { description: "Thunderstorm with heavy hail", icon: "⛈️" },
};
```

## Outcomes

**After Implementation**:
- ✅ Open-Meteo API was easy to integrate
- ✅ No API key required simplifies setup
- ✅ Geocoding + Weather flow works well
- ✅ Backend proxy approach worked well
- ✅ Error handling was straightforward
- ✅ Weather code mapping provides good UX

**Lessons Learned**:
- Open-Meteo is reliable and well-documented
- No API key requirement makes it perfect for learning
- Two-step process (geocoding + weather) is standard
- Weather code mapping improves user experience
- Error handling is important for good UX

## Related

- [Project Intent](../intent/project-intent.md)
- [Feature: Weather Display](../intent/feature-weather-display.md)
- [Decision: Tech Stack](001-tech-stack.md)
- [Pattern: API Design](../knowledge/patterns/api-design.md)

## Status

- **Created**: 2025-12-07 (Phase: Intent)
- **Status**: Accepted

