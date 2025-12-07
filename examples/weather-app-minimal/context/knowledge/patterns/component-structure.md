# Pattern: Component Structure

## Description

React component structure pattern for the Weather App using shadcn-ui. This pattern defines how to organize components, use TypeScript, and structure the frontend code.

## Pattern

### Component Organization

```
src/
├── components/
│   ├── ui/              # shadcn-ui components (Button, Card, Input, etc.)
│   ├── WeatherCard.tsx  # Weather display card
│   ├── WeatherForm.tsx  # Search form
│   └── WeatherDisplay.tsx # Main weather display component
├── services/
│   └── api.ts           # API client (Axios)
├── types/
│   └── weather.ts       # TypeScript types
├── App.tsx              # Main app component
└── main.tsx             # Entry point
```

### Component Structure

**Example Component** (`WeatherCard.tsx`):
```typescript
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';

interface WeatherCardProps {
  city: string;
  temperature: number;
  description: string;
  icon: string;
}

export function WeatherCard({ city, temperature, description, icon }: WeatherCardProps) {
  return (
    <Card>
      <CardHeader>
        <CardTitle>{city}</CardTitle>
      </CardHeader>
      <CardContent>
        <div className="flex items-center gap-4">
          <img src={`https://openweathermap.org/img/wn/${icon}@2x.png`} alt={description} />
          <div>
            <p className="text-2xl font-bold">{temperature}°C</p>
            <p className="text-muted-foreground">{description}</p>
          </div>
        </div>
      </CardContent>
    </Card>
  );
}
```

### TypeScript Types

**Weather Types** (`types/weather.ts`):
```typescript
export interface WeatherData {
  city: string;
  country: string;
  temperature: number;
  feelsLike: number;
  description: string;
  icon: string;
  humidity: number;
  windSpeed: number;
}

export interface WeatherResponse {
  success: boolean;
  data?: WeatherData;
  error?: {
    code: string;
    message: string;
  };
}
```

### API Client Pattern

**API Service** (`services/api.ts`):
```typescript
import axios from 'axios';
import type { WeatherResponse } from '@/types/weather';

const api = axios.create({
  baseURL: 'http://localhost:3000/api',
});

export const weatherApi = {
  getWeather: async (city: string): Promise<WeatherResponse> => {
    const response = await api.get<WeatherResponse>('/weather', {
      params: { city },
    });
    return response.data;
  },
};
```

### shadcn-ui Usage

1. **Install Components**: Use `npx shadcn-ui@latest add [component]`
2. **Import from `@/components/ui/`**: All shadcn-ui components
3. **Use Tailwind Classes**: For styling
4. **Follow shadcn-ui Patterns**: Components are copy-paste, customize as needed

### Component Best Practices

1. **TypeScript First**: Always define props interfaces
2. **Single Responsibility**: One component, one purpose
3. **Composition**: Build complex UIs from simple components
4. **Reusability**: Make components reusable when possible
5. **Accessibility**: shadcn-ui components are accessible by default

## When to Use

- All React components in the application
- TypeScript type definitions
- API client structure
- Component organization

## Benefits

- **Type Safety**: TypeScript catches errors early
- **Reusability**: Components can be reused
- **Maintainability**: Clear structure, easy to find code
- **Modern UI**: shadcn-ui provides beautiful, accessible components
- **Developer Experience**: Fast development with Vite

## Examples

See implementation in:
- `src/components/WeatherCard.tsx`
- `src/components/WeatherForm.tsx`
- `src/services/api.ts`
- `src/types/weather.ts`

## Related

- [Feature: Weather Display](../../intent/feature-weather-display.md)
- [Decision: Tech Stack](../../decisions/001-tech-stack.md)
- [Pattern: API Design](api-design.md)

