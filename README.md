# 🏥 Hospital Management System

A full-stack web application designed to simplify and manage hospital operations such as patient management, doctor management, appointments, medical records, and user authentication.

---

## 📌 About The Project

The **Hospital Management System** is a web-based application that provides a centralized platform for managing hospital-related activities.

The system supports different users such as **Admin, Doctor, and Patient**, with separate functionalities and permissions for each role.

---

## ✨ Features

### 🔐 Authentication
- User Registration
- User Login
- JWT-based Authentication
- Role-based Authorization
- Secure Password Handling

### 👨‍⚕️ Doctor Management
- Add Doctors
- View Doctors
- Update Doctor Information
- Delete Doctors
- Manage Doctor Availability
- View Doctor Appointments

### 🧑‍🤝‍🧑 Patient Management
- Add Patients
- View Patient Information
- Update Patient Details
- Delete Patient Records
- View Medical History

### 📅 Appointment Management
- Book Appointments
- View Appointments
- Update Appointment Status
- Cancel Appointments
- Manage Doctor Availability

### 📋 Medical Records
- Create Medical Records
- View Patient Medical History
- Update Diagnosis
- Add Prescriptions
- Add Doctor Notes

### 🛠️ Admin Dashboard
- Manage Users
- Manage Doctors
- Manage Patients
- Manage Appointments
- Monitor Hospital Activities

---

## 👥 User Roles

### 👨‍💼 Admin

The Admin has complete access to the system.

- Manage Doctors
- Manage Patients
- Manage Users
- Manage Appointments
- View Hospital Records
- Manage Departments

### 👨‍⚕️ Doctor

Doctors can manage their appointments and patient information.

- View Appointments
- View Patient Details
- View Medical History
- Add Medical Records
- Update Diagnosis
- Add Prescriptions
- Manage Availability

### 🧑 Patient

Patients can manage their appointments and medical information.

- Register/Login
- Manage Profile
- Search Doctors
- View Doctor Details
- Book Appointments
- Cancel Appointments
- View Medical Records

---

## 🛠️ Tech Stack

### Frontend

- React.js
- Vite
- Tailwind CSS
- React Router
- Axios

### Backend

- Node.js
- Express.js
- REST API
- JWT Authentication
- bcrypt

### Database

- MongoDB
- Mongoose

---

## 🏗️ Project Architecture

```text
Hospital Management System
│
├── Frontend
│   ├── React.js
│   ├── Vite
│   ├── Tailwind CSS
│   ├── React Router
│   └── Axios
│
├── Backend
│   ├── Node.js
│   ├── Express.js
│   ├── REST API
│   ├── JWT
│   └── Middleware
│
└── Database
    └── MongoDB


hospital-management-system/
│
├── frontend/
│   │
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── services/
│   │   ├── context/
│   │   ├── routes/
│   │   ├── assets/
│   │   └── App.jsx
│   │
│   ├── package.json
│   └── vite.config.js
│
├── backend/
│   │
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── config/
│   ├── utils/
│   ├── server.js
│   └── package.json
│
├── .gitignore
└── README.md

🔄 Application Flow

                    Hospital Management System
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
        Admin              Doctor              Patient
          │                   │                   │
          ▼                   ▼                   ▼
     Manage Users       View Appointments    Search Doctors
     Manage Doctors     View Patients        Book Appointment
     Manage Patients    Add Records          View Records
     Manage Appointments Update Records      Manage Profile