# React Frontend

## Purpose
A web frontend for [Project Name], interacting with REST services exposed by a FastAPI backend.

Replace `[Project Name]` with the name of your application throughout this file. Add or remove sections as needed once the project structure is finalized.

## Features
- Responsive layout using **Tailwind CSS** or **Material-UI**
- REST API integration via Axios
- Authentication support (e.g., JWT)
- Error and loading UI states
- `.env` based configuration for base URLs and API keys

## Getting Started
1. Install dependencies with `npm install`.
2. Create a `.env` file in the project root. Specify `VITE_API_URL` or other environment variables required for your backend.
3. Run the development server with `npm run dev`.
4. Build the production bundle using `npm run build`.

## API Endpoints Used
Update this table with endpoints from your FastAPI backend.

| Method | Path          | Description        |
|--------|---------------|--------------------|
| GET    | /api/users    | Fetch user list    |
| POST   | /api/login    | Authenticate user  |

## Directory Structure
```
src/
├── components/         # Reusable UI components
├── pages/              # Route-level components
├── services/           # Axios wrappers for API calls
├── utils/              # Helper functions
├── App.tsx             # Root React component
└── main.tsx            # Application entry point
```

## Non-Functional Requirements
- Code must pass linting and formatting checks before commit.
- Provide unit tests for critical components.
- Ensure the UI is accessible and responsive.

## Global Standards

### Security Standards
- Use `.env` files for secrets and never check them into source control.
- Recommend dependency scanning (e.g., `npm audit`, `pip-audit`).
- Define secure CORS policies.
- Enforce HTTPS and secure headers (via Helmet for React, FastAPI middleware, or a PostgREST proxy).

### Logging Specifications
- Use structured logging (e.g., JSON logs).
- Define log levels (`DEBUG`, `INFO`, `WARN`, `ERROR`).
- Provide centralized logging support (e.g., integrate with Fluentd, Loki, or the ELK stack).

### Error Handling
- Define a uniform error schema: `{"error_code": "...", "message": "...", "details": {...}}`.
- Provide sample responses for common failure scenarios.
- Include retry/backoff logic where appropriate.

## Customization Notes
- Replace placeholder API endpoints above with your actual routes.
- Extend the directory structure section if additional folders are added.
- Add instructions for deployment (Docker, Vercel, etc.) if required by your project.

