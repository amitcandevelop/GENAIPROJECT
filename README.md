# AI Interview Preparation Platform

A full-stack job interview preparation app that helps candidates analyze their CV/resume against a job description and generate a tailored interview report plus a polished PDF resume.

This project combines a React frontend with an Express + MongoDB backend and uses Google Gemini via the Google GenAI SDK to generate structured interview feedback and resume content.

## Features

- User registration and login with JWT authentication
- Protected routes for authenticated users only
- Resume upload support for analysis against a target job description
- AI-generated interview report with:
  - match score
  - technical questions
  - behavioral questions
  - skill gaps and severity
  - preparation plan
- AI-generated resume PDF tailored to the target role
- Recent report history for logged-in users

## Tech Stack

### Frontend
- React
- Vite
- React Router
- SCSS

### Backend
- Node.js
- Express.js
- MongoDB with Mongoose
- JWT authentication
- Cookie-based auth
- Multer for file uploads
- Puppeteer for PDF generation

### AI
- Google GenAI SDK
- Gemini model for interview analysis and resume generation

## Project Structure

```text
GENAIPROJECT/
├── Backend/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   └── app.js
│   ├── .env
│   ├── package.json
│   └── server.js
├── Frontend/
│   ├── src/
│   ├── package.json
│   ├── vite.config.js
│   └── README.md
└── README.md
```

## Prerequisites

Before running the app, make sure you have:

- Node.js 18+
- npm
- MongoDB instance or MongoDB Atlas connection string
- Google GenAI API key

## Environment Setup

Create a `.env` file inside the `Backend` folder with the following variables:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GOOGLE_GENAI_API_KEY=your_google_genai_api_key
```

Example:

```env
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/interview-master
JWT_SECRET=supersecretjwtkey
GOOGLE_GENAI_API_KEY=your_api_key_here
```

## Installation

### Backend

```bash
cd Backend
npm install
```

### Frontend

```bash
cd Frontend
npm install
```

## Running the App

### Start the backend

```bash
cd Backend
npm run dev
```

The backend runs on:
- http://localhost:3000

### Start the frontend

```bash
cd Frontend
npm run dev
```

The frontend usually runs on:
- http://localhost:5173

## API Endpoints

### Authentication

- `POST /api/auth/register` — register a new user
- `POST /api/auth/login` — login a user
- `GET /api/auth/logout` — logout and clear auth cookie
- `GET /api/auth/get-me` — fetch current authenticated user

### Interview

- `POST /api/interview/` — generate an interview report using resume, self-description, and job description
- `GET /api/interview/` — get all interview reports for the current user
- `GET /api/interview/report/:interviewId` — fetch a specific interview report
- `POST /api/interview/resume/pdf/:interviewReportId` — generate a tailored resume PDF

## Typical Workflow

1. Create an account or log in.
2. Open the interview page.
3. Fill in the job description and your self-description.
4. Upload your resume.
5. Submit the form to generate:
   - match score
   - Q&A guidance
   - skill gaps
   - day-wise preparation plan
6. Generate a tailored PDF resume for the target role.
7. Review and revisit previous reports from your dashboard.

## Notes

- The backend expects CORS requests from `http://localhost:5173`.
- Cookies are used for authentication, so the frontend and backend must run on local origins that match the configured CORS setup.
- The AI features depend on a valid `GOOGLE_GENAI_API_KEY` and a working MongoDB database connection.

## License

This project is currently not configured with a formal license declaration.
