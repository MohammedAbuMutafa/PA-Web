# PA-Web

A modern React-based web application for the Precision Agriculture ecosystem, providing an intuitive user interface for managing drone sessions, visualizing agricultural data, and monitoring crop health analysis results.

## Overview

PA-Web serves as the frontend interface for the Precision Agriculture system, built with React and TypeScript. It provides farmers, agricultural researchers, and data analysts with a comprehensive dashboard for managing drone flight sessions, viewing processing results, and analyzing crop health metrics through interactive visualizations.

## Features

### Session Management
- **Session Creation**: Create and manage new drone flight sessions
- **Session Dashboard**: View all sessions with status, dates, and image counts
- **Session Details**: Detailed view of individual sessions with metrics
- **Session History**: Historical data and trends analysis

### Image Processing Visualization
- **Image Gallery**: Browse processed drone imagery with metadata
- **Processing Status**: Real-time status updates for image processing
- **Before/After Comparison**: Side-by-side comparison of original and processed images
- **Thumbnail Navigation**: Quick navigation through large image datasets

### Data Visualization
- **Interactive Charts**: Crop health metrics with interactive charts and graphs
- **NDVI Visualization**: Vegetation index heatmaps and overlays
- **Geographic Mapping**: Field mapping with processing results overlay
- **Export Capabilities**: Export data and visualizations in multiple formats

### User Interface
- **Responsive Design**: Mobile-friendly interface for field use
- **Dark/Light Theme**: Customizable interface themes
- **Real-time Updates**: Live data updates and notifications
- **Accessibility**: WCAG-compliant interface design

## Project Structure

```
PA-Web/
├── public/                    # Static assets
│   ├── index.html            # Main HTML template
│   ├── favicon.ico           # Site favicon
│   └── images/               # Static images
├── src/                      # Source code
│   ├── components/           # React components
│   │   ├── Dashboard/        # Dashboard components
│   │   ├── Session/          # Session management
│   │   ├── ImageGallery/     # Image display components
│   │   ├── Charts/           # Data visualization
│   │   └── Common/           # Shared components
│   ├── pages/               # Page components
│   │   ├── HomePage.tsx     # Home page
│   │   ├── SessionsPage.tsx # Sessions management
│   │   ├── AnalyticsPage.tsx # Analytics dashboard
│   │   └── SettingsPage.tsx # Application settings
│   ├── services/            # API services
│   │   ├── api.ts          # API client
│   │   ├── sessionService.ts # Session API calls
│   │   └── imageService.ts  # Image API calls
│   ├── hooks/              # Custom React hooks
│   │   ├── useSession.ts   # Session management hook
│   │   └── useImages.ts    # Image management hook
│   ├── types/              # TypeScript type definitions
│   │   ├── session.ts      # Session types
│   │   ├── image.ts        # Image types
│   │   └── api.ts          # API response types
│   ├── utils/              # Utility functions
│   │   ├── formatters.ts   # Data formatting
│   │   └── validators.ts   # Input validation
│   ├── styles/             # CSS and styling
│   │   ├── globals.css     # Global styles
│   │   └── components.css  # Component styles
│   ├── App.tsx             # Main application component
│   ├── index.tsx           # Application entry point
│   └── setupTests.ts       # Test configuration
├── package.json            # Dependencies and scripts
├── tsconfig.json           # TypeScript configuration
└── README.md              # This file
```

## Technology Stack

### Frontend Framework
- **React 18**: Modern React with hooks and functional components
- **TypeScript**: Type-safe development with full type checking
- **Create React App**: Zero-configuration React setup

### UI and Styling
- **CSS3**: Modern CSS with flexbox and grid layouts
- **Responsive Design**: Mobile-first responsive design approach
- **Custom Components**: Reusable component library
- **Theme System**: Dark/light theme support

### Data Visualization
- **Chart.js**: Interactive charts and graphs
- **D3.js**: Advanced data visualization capabilities
- **React-Chartjs-2**: React integration for Chart.js
- **Map Integration**: Geographic data visualization

### State Management
- **React Hooks**: useState, useEffect, useContext for state management
- **Custom Hooks**: Reusable stateful logic
- **Context API**: Global state management
- **Local Storage**: Persistent user preferences

### API Integration
- **Fetch API**: Modern HTTP client for API communication
- **Axios**: HTTP client with interceptors and error handling
- **WebSocket**: Real-time data updates
- **RESTful APIs**: Integration with PA-Backend services

## Installation and Setup

### Prerequisites
- Node.js 16.0 or higher
- npm or yarn package manager
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Development Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/MohammedAbuMutafa/PA-Web.git
   cd PA-Web
   ```

2. **Install dependencies**:
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Environment Configuration**:
   Create a `.env` file in the root directory:
   ```env
   REACT_APP_API_BASE_URL=http://localhost:5000/api
   REACT_APP_WS_URL=ws://localhost:5000/ws
   REACT_APP_VERSION=1.0.0
   ```

4. **Start development server**:
   ```bash
   npm start
   # or
   yarn start
   ```

5. **Open in browser**:
   Navigate to [http://localhost:3000](http://localhost:3000)

### Production Build

1. **Build for production**:
   ```bash
   npm run build
   # or
   yarn build
   ```

2. **Serve the build**:
   ```bash
   npm install -g serve
   serve -s build
   ```

## API Integration

### Session Management API
```typescript
// Session service integration
import { sessionService } from './services/sessionService';

// Create new session
const newSession = await sessionService.createSession({
  session_name: 'Drone Flight 001'
});

// Get all sessions
const sessions = await sessionService.getAllSessions();

// Get session details
const sessionDetails = await sessionService.getSessionById(sessionId);
```

### Image Management API
```typescript
// Image service integration
import { imageService } from './services/imageService';

// Upload image
const uploadedImage = await imageService.uploadImage(imageFile, sessionId);

// Get session images
const sessionImages = await imageService.getSessionImages(sessionId);

// Get image details
const imageDetails = await imageService.getImageDetails(imageId);
```

## Component Usage

### Session Dashboard
```tsx
import { SessionDashboard } from './components/Dashboard/SessionDashboard';

function App() {
  return (
    <div className="App">
      <SessionDashboard 
        sessions={sessions}
        onSessionSelect={handleSessionSelect}
        onNewSession={handleNewSession}
      />
    </div>
  );
}
```

### Image Gallery
```tsx
import { ImageGallery } from './components/ImageGallery/ImageGallery';

function SessionPage({ sessionId }) {
  return (
    <div>
      <ImageGallery 
        sessionId={sessionId}
        onImageSelect={handleImageSelect}
        showMetadata={true}
      />
    </div>
  );
}
```

### Data Visualization
```tsx
import { CropHealthChart } from './components/Charts/CropHealthChart';

function AnalyticsPage() {
  return (
    <div>
      <CropHealthChart 
        data={analyticsData}
        type="ndvi"
        interactive={true}
      />
    </div>
  );
}
```

## Configuration

### Environment Variables
```env
# API Configuration
REACT_APP_API_BASE_URL=http://localhost:5000/api
REACT_APP_WS_URL=ws://localhost:5000/ws

# Application Settings
REACT_APP_VERSION=1.0.0
REACT_APP_THEME=light

# Feature Flags
REACT_APP_ENABLE_ANALYTICS=true
REACT_APP_ENABLE_EXPORT=true
```

### Theme Configuration
```typescript
// Theme configuration
export const theme = {
  light: {
    primary: '#2E7D32',
    secondary: '#4CAF50',
    background: '#FFFFFF',
    text: '#212121'
  },
  dark: {
    primary: '#4CAF50',
    secondary: '#66BB6A',
    background: '#121212',
    text: '#FFFFFF'
  }
};
```

## Development

### Adding New Components

1. **Create component**:
   ```tsx
   // src/components/NewComponent/NewComponent.tsx
   import React from 'react';
   
   interface NewComponentProps {
     data: any;
     onAction: (action: string) => void;
   }
   
   export const NewComponent: React.FC<NewComponentProps> = ({ data, onAction }) => {
     return (
       <div className="new-component">
         {/* Component implementation */}
       </div>
     );
   };
   ```

2. **Add styles**:
   ```css
   /* src/styles/components/NewComponent.css */
   .new-component {
     /* Component styles */
   }
   ```

3. **Export from index**:
   ```tsx
   // src/components/NewComponent/index.ts
   export { NewComponent } from './NewComponent';
   ```

### Custom Hooks
```tsx
// src/hooks/useAnalytics.ts
import { useState, useEffect } from 'react';

export const useAnalytics = (sessionId: string) => {
  const [analytics, setAnalytics] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchAnalytics = async () => {
      try {
        const data = await analyticsService.getSessionAnalytics(sessionId);
        setAnalytics(data);
      } catch (error) {
        console.error('Failed to fetch analytics:', error);
      } finally {
        setLoading(false);
      }
    };

    fetchAnalytics();
  }, [sessionId]);

  return { analytics, loading };
};
```

### API Service Integration
```tsx
// src/services/analyticsService.ts
import { apiClient } from './api';

export const analyticsService = {
  getSessionAnalytics: async (sessionId: string) => {
    const response = await apiClient.get(`/session/metric/${sessionId}`);
    return response.data;
  },

  getCropHealthData: async (imageId: string) => {
    const response = await apiClient.get(`/image/${imageId}`);
    return response.data;
  }
};
```

## Testing

### Unit Tests
```bash
# Run unit tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode
npm run test:watch
```

### Integration Tests
```bash
# Run integration tests
npm run test:integration

# Run E2E tests
npm run test:e2e
```

### Test Examples
```tsx
// src/components/__tests__/SessionDashboard.test.tsx
import { render, screen } from '@testing-library/react';
import { SessionDashboard } from '../Dashboard/SessionDashboard';

describe('SessionDashboard', () => {
  it('renders session list correctly', () => {
    const mockSessions = [
      { id: '1', name: 'Test Session', date: '2024-01-15' }
    ];
    
    render(<SessionDashboard sessions={mockSessions} />);
    
    expect(screen.getByText('Test Session')).toBeInTheDocument();
  });
});
```

## Deployment

### Build Optimization
```bash
# Analyze bundle size
npm run analyze

# Build with optimizations
npm run build:prod
```

### Docker Deployment
```dockerfile
# Dockerfile
FROM node:16-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Nginx Configuration
```nginx
# nginx.conf
server {
    listen 80;
    server_name localhost;
    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    location /api {
        proxy_pass http://pa-backend:5000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## Integration

### With PA Components
- **PA-Backend**: RESTful API integration for data management
- **PA-MultispectralProcessing**: Real-time processing status updates
- **PA-Utils**: Visualization of processing results and thresholds
- **PA-Components**: Shared UI components and utilities

### External Services
- **WebSocket**: Real-time data streaming
- **File Upload**: Image and data file handling
- **Authentication**: User session management (future enhancement)
- **Analytics**: Usage tracking and performance monitoring

## Performance Optimization

### Code Splitting
```tsx
// Lazy loading components
import React, { lazy, Suspense } from 'react';

const AnalyticsPage = lazy(() => import('./pages/AnalyticsPage'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <AnalyticsPage />
    </Suspense>
  );
}
```

### Image Optimization
```tsx
// Optimized image component
import { useState } from 'react';

const OptimizedImage = ({ src, alt, ...props }) => {
  const [loaded, setLoaded] = useState(false);
  
  return (
    <img
      src={src}
      alt={alt}
      onLoad={() => setLoaded(true)}
      style={{ opacity: loaded ? 1 : 0 }}
      {...props}
    />
  );
};
```

## Troubleshooting

### Common Issues

1. **Build Failures**:
   ```bash
   # Clear cache and reinstall
   rm -rf node_modules package-lock.json
   npm install
   ```

2. **API Connection Issues**:
   - Check API_BASE_URL in environment variables
   - Verify CORS configuration in backend
   - Check network connectivity

3. **Performance Issues**:
   - Enable React DevTools Profiler
   - Check bundle size with `npm run analyze`
   - Implement code splitting for large components

### Debug Mode
Enable debug logging:
```typescript
// Add to environment variables
REACT_APP_DEBUG=true

// Use in components
const debug = process.env.REACT_APP_DEBUG === 'true';
if (debug) console.log('Debug info:', data);
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Implement your changes with tests
4. Update documentation
5. Submit a pull request

### Code Style
- Follow React best practices
- Use TypeScript for type safety
- Implement proper error handling
- Write comprehensive tests

## License

This project is part of the Precision Agriculture ecosystem and is developed for research and educational purposes.

## Support

For issues and questions:
- Create an issue in the repository
- Check the browser console for errors
- Review the API documentation
- Check the component documentation

---

*Part of the Precision Agriculture ecosystem - Empowering farmers with intuitive technology*