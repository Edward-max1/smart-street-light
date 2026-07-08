# Smart Street Lighting and Vehicle Monitoring System

A modern smart-city web application that combines IoT sensor data, a Node/Express API, Supabase storage, and a responsive admin dashboard for monitoring and controlling street lighting.

## Features

- Real-time monitoring of vehicle detections
- Admin dashboard for controlling street lights
- Traffic summaries with approaching/outgoing totals
- Exportable system logs
- Express backend for privileged Supabase operations
- ESP32 integration for hardware-based detection

## Tech Stack

- Frontend: Vite + JavaScript + Bootstrap
- Backend: Node.js + Express
- Database: Supabase
- Hardware: ESP32 + HC-SR04 ultrasonic sensor

## Local Setup

1. Install dependencies:
   ```bash
   npm install
   ```
2. Create a local environment file:
   ```bash
   cp .env.example .env
   ```
3. Fill in your own Supabase values in `.env`.
4. Start the API and frontend together:
   ```bash
   npm run dev:full
   ```

The Express API runs on `http://localhost:3000`. Vite proxies `/api` requests to it during development.

## Environment Variables

Create a `.env` file with:

```env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_API_BASE_URL=/api

SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
SESSION_SECRET=replace-with-a-long-random-string
PORT=3000
```

The service role key is used only by the Express backend. Do not expose it with a `VITE_` prefix.

## Backend API

- `GET /api/health`
- `POST /api/auth/login`
- `GET /api/lights`
- `PATCH /api/lights/:id`
- `PATCH /api/lights`
- `GET /api/vehicles/history`
- `GET /api/vehicles/today-count`
- `GET /api/vehicles/yesterday-count`
- `GET /api/vehicles/chart-data`
- `GET /api/vehicles/logs`
- `DELETE /api/vehicles/logs`

## Deployment

This project includes a Vite frontend and an Express API. The Express server can serve the built `dist` folder after `npm run build`.

Use a Node.js host such as Render, Railway, Fly.io, or a VPS. Make sure your deployed environment contains the same Supabase environment variables.
