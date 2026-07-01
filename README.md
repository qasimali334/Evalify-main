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

