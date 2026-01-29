# Frontend Configuration Guide

## Backend API URL

Your RentMyCar backend is deployed on Vercel at:

**Production URL:** `https://rent-chi-eight.vercel.app`

## Configuring Your Frontend

To connect your frontend application to this backend, you need to configure the API base URL in your frontend code.

### Common Configuration Locations

Depending on your frontend framework and HTTP client, you'll need to update the API base URL in one of these locations:

#### 1. **Environment Variables** (Recommended)
Create or update your frontend's `.env` file based on your framework:

**For Vite-based projects** (Vite, Vue, etc.):
```env
VITE_API_URL=https://rent-chi-eight.vercel.app
```

**For Create React App:**
```env
REACT_APP_API_URL=https://rent-chi-eight.vercel.app
```

**For Next.js:**
```env
NEXT_PUBLIC_API_URL=https://rent-chi-eight.vercel.app
```

Then use it in your API client:
```javascript
// For Vite
const API_URL = import.meta.env.VITE_API_URL || 'http://localhost:3000';

// For Create React App
const API_URL = process.env.REACT_APP_API_URL || 'http://localhost:3000';

// For Next.js
const API_URL = process.env.NEXT_PUBLIC_API_URL || 'http://localhost:3000';
```

#### 2. **Axios Configuration**
If you're using Axios, update your API instance:

```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: 'https://rent-chi-eight.vercel.app',
  withCredentials: true
});

export default api;
```

#### 3. **Fetch API**
If you're using native fetch:

```javascript
const API_BASE_URL = 'https://rent-chi-eight.vercel.app';

fetch(`${API_BASE_URL}/api/user/login`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(credentials),
});
```

#### 4. **Configuration File**
Create a `config.js` or `constants.js` file:

```javascript
export const API_CONFIG = {
  baseURL: process.env.NODE_ENV === 'production' 
    ? 'https://rent-chi-eight.vercel.app'
    : 'http://localhost:3000',
  timeout: 10000,
};
```

### API Endpoints

All API endpoints are prefixed with `/api`:

- **User Routes**: `https://rent-chi-eight.vercel.app/api/user`
  - POST `/api/user/login`
  - POST `/api/user/register`
  - GET `/api/user/cars`
  - etc.

- **Owner Routes**: `https://rent-chi-eight.vercel.app/api/owner`
- **Booking Routes**: `https://rent-chi-eight.vercel.app/api/bookings`

### CORS Configuration

The backend is configured to accept requests from your frontend. Make sure your frontend URL is set in the backend's `CLIENT_URL` environment variable in Vercel.

### Troubleshooting

If you're still getting `ERR_CONNECTION_REFUSED` errors:

1. **Check your frontend code** for hardcoded `localhost:3000` references
2. **Search your codebase** for:
   ```bash
   grep -r "localhost:3000" src/
   grep -r "http://localhost" src/
   ```
3. **Clear your browser cache** and rebuild your frontend application
4. **Verify the backend is running** by visiting: https://rent-chi-eight.vercel.app

### Development vs Production

For local development, you can use different URLs:

```javascript
const API_URL = process.env.NODE_ENV === 'production'
  ? 'https://rent-chi-eight.vercel.app'
  : 'http://localhost:3000';
```

This allows you to run the backend locally during development and use the Vercel deployment in production.
