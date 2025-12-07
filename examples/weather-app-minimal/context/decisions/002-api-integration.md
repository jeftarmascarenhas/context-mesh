# Decision: API Integration - OpenWeatherMap

## Context

We need to integrate with an external weather API to fetch weather data. Requirements:
- Free tier available
- Stable and reliable service
- Good documentation
- Simple integration
- Returns current weather data

## Decision

**Use OpenWeatherMap API** for weather data:
- **Endpoint**: `https://api.openweathermap.org/data/2.5/weather`
- **Method**: GET
- **Authentication**: API key (free tier: 1,000 calls/day)
- **Response Format**: JSON
- **Units**: Metric (Celsius)
- **Language**: Portuguese (pt_br) for descriptions

**Integration Approach**:
- Backend calls OpenWeatherMap API
- Frontend calls our backend API
- Backend acts as proxy/aggregator
- Error handling for API failures
- Input validation (city name)

## Rationale

1. **OpenWeatherMap**:
   - Most stable and known weather API
   - Free tier: 1,000 calls/day (sufficient for development)
   - Excellent documentation
   - Reliable uptime
   - Used by millions of applications

2. **Backend Proxy**:
   - Hides API key from frontend (security)
   - Allows data transformation/formatting
   - Centralized error handling
   - Can add caching later (if needed)
   - Better control over API usage

3. **Metric Units**:
   - Celsius is standard in most countries
   - Easier to understand for users
   - Can add unit conversion later

4. **Portuguese Language**:
   - Better UX for Portuguese speakers
   - Can be made configurable later

## Alternatives Considered

### Alternative 1: Open-Meteo API
- **Pros**: No API key needed, open source
- **Cons**: Less known, smaller community
- **Why Not Chosen**: OpenWeatherMap is more stable and widely used

### Alternative 2: WeatherAPI.com
- **Pros**: Good free tier, good documentation
- **Cons**: Less known than OpenWeatherMap
- **Why Not Chosen**: OpenWeatherMap is the industry standard

### Alternative 3: Frontend calls OpenWeatherMap directly
- **Pros**: Simpler architecture
- **Cons**: API key exposed in frontend (security risk)
- **Why Not Chosen**: Security best practice is to keep API keys on backend

## Implementation Details

### API Endpoint Structure

**Our Backend Endpoint**:
```
GET /api/weather?city={cityName}
```

**OpenWeatherMap Endpoint**:
```
GET https://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_KEY}&units=metric&lang=pt_br
```

### Request Example
```typescript
// Our backend calls OpenWeatherMap
GET https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY&units=metric&lang=pt_br
```

### Response Structure (OpenWeatherMap)
```json
{
  "name": "London",
  "main": {
    "temp": 15.5,
    "feels_like": 14.2,
    "temp_min": 13.0,
    "temp_max": 17.0,
    "pressure": 1013,
    "humidity": 65
  },
  "weather": [
    {
      "main": "Clear",
      "description": "céu limpo",
      "icon": "01d"
    }
  ],
  "wind": {
    "speed": 3.5,
    "deg": 180
  },
  "sys": {
    "country": "GB"
  }
}
```

### Our Backend Response Format
```json
{
  "success": true,
  "data": {
    "city": "London",
    "country": "GB",
    "temperature": 15.5,
    "feelsLike": 14.2,
    "description": "céu limpo",
    "icon": "01d",
    "humidity": 65,
    "windSpeed": 3.5
  }
}
```

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
OPENWEATHER_API_KEY=your_api_key_here
PORT=3000
```

### API Key Setup

1. Create account at https://openweathermap.org/api
2. Get free API key (1,000 calls/day)
3. Add to backend `.env` file
4. Never commit `.env` to Git

## Outcomes

**After Implementation**:
- ✅ OpenWeatherMap API was easy to integrate
- ✅ Free tier sufficient for development
- ✅ Response format was clear and well-documented
- ✅ Backend proxy approach worked well
- ✅ Error handling was straightforward

**Lessons Learned**:
- OpenWeatherMap is reliable and well-documented
- Backend proxy is the right approach for API keys
- Free tier is sufficient for learning/development
- Error handling is important for good UX

## Related

- [Project Intent](../intent/project-intent.md)
- [Feature: Weather Display](../intent/feature-weather-display.md)
- [Decision: Tech Stack](001-tech-stack.md)
- [Pattern: API Design](../knowledge/patterns/api-design.md)

## Status

- **Created**: 2024-01-20 (Intent phase)
- **Status**: Accepted

