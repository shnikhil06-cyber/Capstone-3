# 🏥 Hospital Management System

> A modern, full-stack web application designed to streamline hospital operations, manage patient records, schedule appointments, and coordinate doctor-patient workflows seamlessly.

[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Vite](https://img.shields.io/badge/Vite-5.x-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.x-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Node.js](https://img.shields.io/badge/Node.js-18.x-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-4.x-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.x-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-Educational-blue.svg?style=for-the-badge)](#license)

---

## 📌 Table of Contents

- [Overview](#overview)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [User Roles & Permissions](#-user-roles--permissions)
- [Project Structure](#-project-structure)
- [Database Schemas & Collections](#-database-schemas--collections)
- [API Endpoints](#-api-endpoints)
- [Installation & Setup](#-installation--setup)
- [Application Workflow](#-application-workflow)
- [Future Improvements](#-future-improvements)
- [Learning Objectives](#-learning-objectives)
- [License](#license)

---  

## 📖 Overview

The **Hospital Management System** is an end-to-end web platform tailored for healthcare institutions. It connects patients, doctors, and hospital administrators in a unified interface, facilitating efficient appointment scheduling, electronic medical record (EMR) management, user authorization, and system management.

---

## ✨ Key Features

- 🔐 **Authentication & Authorization**: Secure user registration & login using JWT (JSON Web Tokens).
- 👤 **Patient Management**: Profile management, medical history tracking, and doctor search.
- 👨‍⚕️ **Doctor Management**: Availability scheduling, patient consultation history, and prescription logging.
- 📅 **Appointment System**: Dynamic booking, status updates (Pending/Approved/Completed/Cancelled).
- 📋 **Medical Records (EMR)**: Diagnostic notes, prescriptions, and historical patient consultations.
- 🎛️ **Admin Dashboard**: Comprehensive control panel to manage doctors, patients, appointments, and users.
- 🔍 **Search & Filter**: Fast filtering across doctors, departments, and appointment schedules.
- 🛡️ **Role-Based Access Control (RBAC)**: Custom views and API restrictions tailored per role.

---

## 🛠️ Tech Stack

### **Frontend**
| Technology | Description |
| :--- | :--- |
| **React.js** | Frontend UI Library |
| **Vite** | Fast Build Tool & Dev Server |
| **Tailwind CSS** | Utility-first CSS Framework |
| **React Router** | Client-side Routing |
| **Axios** | HTTP Client for API Requests |

### **Backend**
| Technology | Description |
| :--- | :--- |
| **Node.js** | JavaScript Runtime Environment |
| **Express.js** | Backend Web Application Framework |
| **REST API** | Standardized Architecture |
| **JWT** | Secure Token-Based Authentication |

### **Database**
| Technology | Description |
| :--- | :--- |
| **MongoDB** | NoSQL Database |
| **Mongoose** | Object Data Modeling (ODM) for MongoDB |

---

## 👥 User Roles & Permissions

```
                     ┌───────────────────────┐
                     │   User Access Roles   │
                     └───────────┬───────────┘
        ┌────────────────────────┼────────────────────────┐
        ▼                        ▼                        ▼
  👑 Admin                👨‍⚕️ Doctor                🤒 Patient
  - Manage Doctors        - View Appointments      - Profile Management
  - Manage Patients       - View Patient Details   - Search Doctors
  - Manage Appointments    - Update Medical Records - Book Appointments
  - Manage All Users      - Manage Availability    - View Records & History
  - System Overview
```

---

## 📁 Project Structure

```text
hospital-management-system/
│
├── frontend/                  # React Frontend Application
│   ├── src/
│   │   ├── components/        # Reusable UI Components
│   │   ├── pages/             # Page Components (Home, Dashboard, etc.)
│   │   ├── layouts/           # Layout wrappers (Navbar, Sidebar, Footer)
│   │   ├── services/          # Axios API service calls
│   │   ├── context/           # React Context (Auth, Global State)
│   │   ├── routes/            # App Routing configuration
│   │   └── App.jsx            # Main App Component
│   ├── package.json           # Frontend Dependencies
│   └── vite.config.js         # Vite Configuration
│
├── backend/                   # Node.js / Express API Server
│   ├── controllers/           # Request Handlers & Business Logic
│   ├── models/                # Mongoose Database Models
│   ├── routes/                # Express API Route Definitions
│   ├── middleware/             # Auth & Error Handling Middlewares
│   ├── config/                # DB Connection & App Configuration
│   ├── utils/                 # Utility & Helper Functions
│   ├── server.js              # Server Entry Point
│   └── package.json           # Backend Dependencies
│
├── .gitignore                 # Ignored files & folders
└── README.md                  # Project Documentation
```

---

## 🗄️ Database Schemas & Collections

The MongoDB database maintains the following primary collections:
`Users`, `Doctors`, `Patients`, `Appointments`, `MedicalRecords`, `Departments`.

### 📌 Core Data Schemas

#### **1. Appointment Schema**
```text
Appointment
├── patient     : ObjectId (Ref -> User/Patient)
├── doctor      : ObjectId (Ref -> User/Doctor)
├── date        : Date
├── time        : String
├── status      : String [Pending, Approved, Completed, Cancelled]
└── reason      : String
```

#### **2. Medical Record Schema**
```text
MedicalRecord
├── patient     : ObjectId (Ref -> User/Patient)
├── doctor      : ObjectId (Ref -> User/Doctor)
├── diagnosis   : String
├── prescription: String
├── notes       : String
└── date        : Date
```

---

## 🔌 API Endpoints

### 🔑 Authentication
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/register` | Register a new user | Public |
| `POST` | `/api/auth/login` | User authentication & JWT generation | Public |

### 🤒 Patients
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/patients` | Fetch all patient records | Admin / Doctor |
| `GET` | `/api/patients/:id` | Fetch patient details by ID | Admin / Doctor / Self |
| `POST` | `/api/patients` | Create a new patient profile | Admin / Patient |
| `PUT` | `/api/patients/:id` | Update patient information | Admin / Self |
| `DELETE` | `/api/patients/:id` | Remove a patient profile | Admin |

### 👨‍⚕️ Doctors
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/doctors` | Fetch list of all doctors | Public / Auth |
| `GET` | `/api/doctors/:id` | Fetch doctor profile details | Public / Auth |
| `POST` | `/api/doctors` | Add a new doctor profile | Admin |
| `PUT` | `/api/doctors/:id` | Update doctor details & schedule | Admin / Self |
| `DELETE` | `/api/doctors/:id` | Remove doctor entry | Admin |

### 📅 Appointments
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/appointments` | List all appointments | Admin / Doctor / Patient |
| `GET` | `/api/appointments/:id` | Get appointment details | Authenticated |
| `POST` | `/api/appointments` | Book a new appointment | Patient / Admin |
| `PUT` | `/api/appointments/:id` | Update appointment status | Doctor / Admin |
| `DELETE` | `/api/appointments/:id` | Cancel/Delete appointment | Patient / Admin |

### 📋 Medical Records
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/medical-records` | Retrieve medical records | Doctor / Patient / Admin |
| `GET` | `/api/medical-records/:id` | Retrieve specific record | Doctor / Patient / Admin |
| `POST` | `/api/medical-records` | Add diagnosis & prescription | Doctor |
| `PUT` | `/api/medical-records/:id` | Edit medical record | Doctor |
| `DELETE` | `/api/medical-records/:id` | Delete medical record | Admin |

---

## 🚀 Installation & Setup

Follow these steps to set up and run the project locally on your machine.

### 📋 Prerequisites
- **Node.js** (v18.x or later)
- **npm** or **yarn**
- **MongoDB** (Local instance or MongoDB Atlas cluster)
- **Git**

---

### 1. Clone the Repository
```bash
git clone https://github.com/smokzzzPanther/Hospital-Management.git
cd Hospital-Management
```

---

### 2. Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install
```

#### Environment Configuration
Create a `.env` file in the `backend/` directory:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
```

#### Run Backend Server
```bash
npm run dev
```
> The API server will start at: `http://localhost:5000`

---

### 3. Frontend Setup

Open a new terminal window/tab:

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```
> The client app will be live at: `http://localhost:5173`

---

## 🔄 Application Workflow

```text
Patient Journey:
[ Patient Register/Login ] ──► [ Browse Doctors ] ──► [ Select Schedule ] ──► [ Book Appointment ]
                                                                                   │
                                                                                   ▼
Doctor Workflow:                                                            [ Notification ]
[ View Schedule ] ◄── [ Review Patient Details ] ◄── [ Manage Appointments ] ◄──────┘
        │
        ▼
[ Create Diagnosis & Prescription ] ──► [ Save Medical Record ] ──► [ Patient Accesses History ]

Admin Oversight:
[ System Overview ] ──► [ User & Role Management ] ──► [ Monitor All Hospital Operations ]
```

---

## 🔮 Future Improvements

- 💳 **Payment Gateway Integration**: Online consultation & appointment fee processing (Stripe / Razorpay).
- 📄 **PDF Prescription Generator**: Instant download of official digital prescriptions.
- 📩 **Automated Notifications**: Email & SMS alerts for appointment reminders and updates.
- 💬 **Doctor-Patient Live Chat**: Real-time communication portal.
- 🩺 **Telemedicine Platform**: Video consultation integration.
- 🏥 **Pharmacy & Billing Management**: Inventory tracking & automated invoicing.
- 🧪 **Lab Report Integration**: Upload and view blood work, X-rays, and diagnostics.
- 📊 **Analytics Dashboard**: Graphical insights into patient turnover and revenue.

---

## 🎯 Learning Objectives

This project showcases key full-stack software development practices:
- Modern **React component design** and state management.
- Designing modular **REST APIs with Express.js**.
- Database schema design & indexing with **MongoDB and Mongoose**.
- Robust **Authentication & Authorization** using JWT and password hashing.
- Implementing **Role-Based Access Control (RBAC)** across full stack.
- Effective API communication using **Axios** and asynchronous handling.

---

## 📜 License

This project is created for educational and learning purposes. Feel free to fork and customize it!