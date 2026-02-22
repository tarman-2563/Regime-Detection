                                      Deployment Plan Document

Project: Market / Time Series Regime Detection using Hidden Markov Models
Tech Stack: React, FastAPI, PostgreSQL, Docker


1. Deployment Architecture Overview

The system follows a containerized deployment architecture separating frontend, backend, and database services. The frontend communicates with the FastAPI backend via REST APIs. The backend interacts with PostgreSQL for persistent storage and executes the ML pipeline for regime detection.

2. Components

• Frontend: React + Tailwind CSS + Recharts
• Backend: FastAPI + ML Pipeline (Pandas, NumPy, Scikit-learn, hmmlearn)
• Database: PostgreSQL
• Containerization: Docker
• Optional Hosting: Render / AWS / Railway

3. Dockerization Plan

Frontend Container:
- Build React application
- Serve production build using Nginx
- Expose port 3000

Backend Container:
- Use Python 3.10 base image
- Install dependencies from requirements.txt
- Run FastAPI using Uvicorn
- Expose port 8000

Database Container:
- Use official PostgreSQL image
- Configure environment variables for DB credentials
- Expose port 5432

4. Docker Compose Configuration

Docker Compose orchestrates frontend, backend, and database services. It ensures inter-service networking and environment variable configuration.

5. Environment Configuration

Environment variables stored securely in .env file:
- DATABASE_URL
- SECRET_KEY
- JWT_ALGORITHM
- ACCESS_TOKEN_EXPIRE_MINUTES

6. Cloud Deployment Options

Option 1: Render (Easy deployment)
Option 2: AWS (EC2 + RDS + S3)
Option 3: Railway (Quick prototype deployment)

7. Production Readiness Checklist

- Enable HTTPS (SSL)
- Configure CORS properly
- Use secure JWT expiration
- Add logging and monitoring
- Apply database indexing
- Handle file size limits

8. Deployment Flow Summary

User → Frontend (React)
Frontend → Backend API (FastAPI)
Backend → ML Pipeline Execution
Backend → PostgreSQL Database
Results → Stored and returned to Frontend for visualization


