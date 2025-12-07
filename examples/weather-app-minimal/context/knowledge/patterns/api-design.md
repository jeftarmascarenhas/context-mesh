# Pattern: API Design

## Description

RESTful API design pattern for the Weather App. This pattern defines how we structure API endpoints, request/response formats, and error handling.

## Pattern

### Endpoint Structure

```
GET /api/weather?city={cityName}  - Get current weather for a city
GET /docs                        - Swagger documentation UI
```

### Request Format

**Query Parameters**:
- `city` (required): City name (e.g., "London", "São Paulo")

**Example Request**:
```
GET /api/weather?city=London
```

### Response Format

**Success Response** (200):
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

**Error Response** (400/404/500):
```json
{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message"
  }
}
```

### Error Codes

- `VALIDATION_ERROR` (400) - Invalid input (e.g., missing city parameter)
- `CITY_NOT_FOUND` (404) - City not found in OpenWeatherMap
- `API_ERROR` (500) - OpenWeatherMap API error
- `INTERNAL_ERROR` (500) - Server error

### Swagger Documentation

All endpoints should be documented in Swagger:
- Endpoint description
- Query parameters (with validation)
- Response schemas (success and error)
- Example requests/responses

## When to Use

- All API endpoints in the application
- Consistent error handling
- Standard request/response format
- API documentation

## Benefits

- **Consistency**: All endpoints follow same pattern
- **Predictability**: Developers know what to expect
- **Error Handling**: Clear error messages
- **Type Safety**: TypeScript types match API structure
- **Documentation**: Swagger provides interactive docs

## Examples

See implementation in:
- Backend API routes (`src/routes/weather.routes.ts`)
- Frontend API client (`src/services/api.ts`)
- Swagger configuration (`src/plugins/swagger.ts`)

## Related

- [Feature: Weather Display](../../intent/feature-weather-display.md)
- [Decision: Tech Stack](../../decisions/001-tech-stack.md)
- [Decision: API Integration](../../decisions/002-api-integration.md)

