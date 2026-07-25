# Chat App

A real-time chat application built with the MERN stack and Socket.IO.

## Project overview

This repository contains two separate applications:

- `backend/` — Express server with MongoDB, JWT authentication, Cloudinary image uploads, and Socket.IO for real-time messaging.
- `frontend/` — React + Vite client with a chat UI, auth flow, protected routes, and live user status.

## Key features

- Email/password signup and login
- JWT authentication with HTTP-only cookies
- Real-time chat using Socket.IO
- User presence / online user list
- One-on-one messaging between authenticated users
- Profile picture upload via Cloudinary
- Protected API routes for auth and messaging

## Prerequisites

- Node.js 18+ or compatible
- npm
- MongoDB instance or MongoDB Atlas cluster
- Cloudinary account (for image upload)

## Backend setup

1. Open a terminal and navigate to `backend/`

```bash
cd backend
```

2. Install dependencies

```bash
npm install
```

3. Create a `.env` file in `backend/` with the following values:

```env
PORT=5001
MONGODB_URL=<your-mongodb-connection-string>
JWT_SECRET=<your-jwt-secret>
CLOUDINARY_CLOUD_NAME=<your-cloudinary-cloud-name>
CLOUDINARY_API_KEY=<your-cloudinary-api-key>
CLOUDINARY_API_SECRET=<your-cloudinary-api-secret>
NODE_ENV=development
```

4. Start the backend server

```bash
npm run dev
```

The backend will listen on the port configured in `PORT`, typically `5001`.

## Frontend setup

1. Open a terminal and navigate to `frontend/`

```bash
cd frontend
```

2. Install dependencies

```bash
npm install
```

3. Start the frontend development server

```bash
npm run dev
```

4. Open the client in your browser at the URL shown by Vite, usually `http://localhost:5173`

## Development workflow

- Backend API base URL is configured in `frontend/src/lib/axios.js` as `http://localhost:5001/api`
- The frontend expects the backend server to use CORS and credentials for cookie-based authentication
- The backend socket server also allows connections from `http://localhost:5173`

## API endpoints

### Auth routes

- `POST /api/auth/signup` — create a new account
- `POST /api/auth/login` — sign in
- `POST /api/auth/logout` — log out
- `PUT /api/auth/update-profile` — update profile picture
- `GET /api/auth/check` — check current user session

### Messaging routes

- `GET /api/messages/users` — list other users for sidebar
- `GET /api/messages/:id` — get messages for a conversation
- `POST /api/messages/send/:id` — send a message to a user

## Notes

- Make sure the backend server is running before using the frontend client.
- If authentication fails, verify that cookies are allowed in the browser and that `withCredentials: true` is enabled.
- The project currently includes client-side state management with Zustand and uses `react-router-dom` for page routing.

## License

This project is provided as-is.
