# Evalify - Evaluation Driven Learning & Assessment Platform

Evalify is a secure, smart digital assessment and skill development Learning Management System (LMS) tailored for software engineering courses. It features an interactive, AI-integrated IDE, automated attendance tracking, and comprehensive academic integrity/proctoring controls to ensure secure evaluations.

---

## 🚀 Key Features

### 💻 Interactive Coding IDE
- Integrated with the Monaco Editor in the frontend.
- Backend code execution engine powered by the **Glot.io API** supporting **JavaScript**, **Python**, **C++**, and **Java** runs securely with input (stdin) handling.

### 🛡️ Secure Proctoring & Academic Integrity
- Logs tab switches, clipboard actions (copy-pasting), and window focus changes (blurring) during assessments.
- Integrates integrity monitoring logs visible directly to instructors inside their dashboard.

### 📋 Automated Attendance Tracking
- Automatically records a student's attendance when they access specific learning materials.
- Provides visual attendance logs for both students (to track their presence) and teachers (to view class-wide metrics).

### 📢 Class Announcements & Materials
- Teachers can publish learning materials, download links, and general/urgent class-wide announcements.
- Materials and announcements are dynamically delivered to student dashboards.

### 📊 Interactive Dashboards
- **Teacher Dashboard**: Manage classes, invite/enroll students, generate assessments, grade submissions, view global and per-student attendance reports, check proctoring logs, and distribute course materials.
- **Student Dashboard**: Browse enrolled classes, review announcements, view and complete assignments/quizzes, access learning resources, run code in the editor, and track personal attendance history.

---

## 🛠️ Tech Stack

### Frontend ([evalify-frontend](file:///d:/Projects/Evalify-main/evalify-frontend))
*   **Framework:** React (v19)
*   **Build Tool & Bundler:** Vite
*   **Routing:** React Router (v7)
*   **Styling:** Tailwind CSS & Vanilla CSS
*   **Code Editor:** Monaco Editor (`@monaco-editor/react`)
*   **Services & Auth:** Supabase Auth UI / Supabase JS Client

### Backend ([evalify-backend](file:///d:/Projects/Evalify-main/evalify-backend))
*   **Runtime Environment:** Node.js (ES Modules)
*   **Framework:** Express.js
*   **Database:** PostgreSQL (hosted on Supabase)
*   **Database Client:** `pg` (node-postgres)
*   **Integrations:** Glot.io API (via Axios)

---

## 📁 Repository Structure

```text
Evalify/
├── evalify-backend/                # Express API Backend
│   ├── src/
│   │   ├── config/                 # Configurations (e.g., PostgreSQL Pool)
│   │   ├── controllers/            # Route Controllers (business logic)
│   │   ├── middleware/             # Express Middlewares (e.g., auth checks)
│   │   ├── models/                 # SQL Schema, setup & migration scripts
│   │   └── routes/                 # Express API Endpoint routes
│   ├── index.js                    # Backend Entry Point
│   ├── package.json                # Dependencies and backend scripts
│   └── .env.example                # Template for backend variables
│
└── evalify-frontend/               # React Web App Frontend
    ├── components/                 # React UI Components
    ├── services/                   # Frontend integrations (Supabase config)
    ├── App.jsx                     # Core application layout, routing & UI
    ├── index.html                  # HTML Shell
    ├── index.jsx                   # React DOM Rendering Entry Point
    ├── package.json                # Dependencies and build scripts
    └── .env                        # Frontend environment variables configuration
```

---

## 🌐 Deployment Guide

This project is configured as a monorepo containing a React frontend and a Node.js Express backend. Follow these instructions to deploy them to **Vercel** and **Render** respectively.

### 1. Backend Deployment on Render ([evalify-backend](file:///d:/Projects/Evalify-main/evalify-backend))

Render can deploy Node.js applications manually as a Web Service (recommended for this monorepo layout to keep the root clean) or using the blueprint file located at [render.yaml](file:///d:/Projects/Evalify-main/evalify-backend/render.yaml).

#### Option A: Manual Web Service Setup (Recommended)
1. On the Render Dashboard, click **New +** and select **Web Service**.
2. Connect your GitHub repository.
3. Configure the following settings:
   - **Name**: `evalify-backend`
   - **Environment**: `Node`
   - **Root Directory**: `evalify-backend` (Must point to the backend subdirectory)
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
4. Expand **Advanced** and add the following **Environment Variables**:
   - `PORT`: `5000`
   - `NODE_ENV`: `production`
   - `FRONTEND_URL`: The URL of your deployed Vercel frontend (e.g. `https://evalify-main.vercel.app`)
   - `DATABASE_URL`: Your PostgreSQL database connection string.
   - `SUPABASE_URL`: Your Supabase project URL.
   - `SUPABASE_ANON_KEY`: Your Supabase public anonymous API key.
   - `GLOT_TOKEN`: Your Glot.io API execution engine token (optional).

#### Option B: Using the Render Blueprint
*Note: Render Blueprint specifications normally expect the blueprint file to be at the root of the repository. Since we moved it to the backend subdirectory, you would only use this option if you are deploying the backend subdirectory as a standalone repository.*
1. Use the [render.yaml](file:///d:/Projects/Evalify-main/evalify-backend/render.yaml) file inside the `evalify-backend` folder.
2. Log in to [Render Dashboard](https://dashboard.render.com).
3. Click **New +** and select **Blueprint**.
4. Connect your repository and deploy.

---

### 2. Frontend Deployment on Vercel ([evalify-frontend](file:///d:/Projects/Evalify-main/evalify-frontend))

Vercel hosts the React frontend. The codebase already includes [vercel.json](file:///d:/Projects/Evalify-main/evalify-frontend/vercel.json) to handle routing rewrites correctly.

1. Log in to the [Vercel Dashboard](https://vercel.com/dashboard).
2. Click **Add New** -> **Project** and select your GitHub repository.
3. Configure the project settings:
   - **Project Name**: `evalify-main` (or your choice)
   - **Framework Preset**: Select **Vite**
   - **Root Directory**: Click *Edit* and select **`evalify-frontend`**
4. Expand **Build and Output Settings**:
   - **Build Command**: Set to `npm run build` (override enabled)
   - **Output Directory**: Set to **`dist`** (override enabled)
   - **Install Command**: Leave as default (override disabled)
5. Expand **Environment Variables** and add:
   - `VITE_SUPABASE_URL`: Your Supabase project URL.
   - `VITE_SUPABASE_ANON_KEY`: Your Supabase public anonymous API key.
   - `VITE_API_URL`: Your deployed **Render backend API URL** (e.g., `https://evalify-backend.onrender.com/api`). Notice it must end with `/api`.
6. Click **Deploy**.
