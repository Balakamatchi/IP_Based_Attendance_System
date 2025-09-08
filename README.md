# IP_Based_Attendance_System
A secure MERN-based attendance system with IP validation to prevent proxy logins.

**A secure MERN-based attendance system with IP validation to prevent proxy/VPN logins.**

---

## 📌 Project Overview

This is a **MERN stack** (MongoDB, Express, React, Node.js) based attendance management system. It ensures that users can only mark attendance from authorized IP addresses, reducing the chances of proxy logins or fraudulent check-ins.

The project is divided into two main parts:

* **client/** → React frontend for employees/admins to log in and interact with the system.
* **server/** → Node.js + Express backend with MongoDB models for users and attendance.

## 🚀 Features

* Secure login system with JWT authentication.
* IP-based validation to allow attendance only from registered/authorized IPs.
* Employee dashboard for marking attendance.
* Admin dashboard to view/manage attendance records and users.
* MongoDB models for `User` and `Attendance`.
* JSON-based IP mapping (`localIPMap.json`) for quick configuration.

## 🛠️ Tech Stack

* **Frontend:** React, Axios, React Router
* **Backend:** Node.js, Express.js
* **Database:** MongoDB (Mongoose ODM)
* **Auth:** JWT + bcrypt
* **IP Validation:** Custom logic using `localIPMap.json`

## ⚙️ Prerequisites

* Node.js (>= 16)
* MongoDB (local or Atlas)
* npm or yarn

## 🔧 Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/IP_Based_Attendance_System.git
cd Attendance
```

### 2. Backend setup

```bash
cd server
npm install
```

Create a `.env` file inside `server/` with the following:

```
PORT=5000
MONGO_URI=mongodb://localhost:27017/attendance_db
JWT_SECRET=your_secret_key
```

Start the backend:

```bash
npm start
```

### 3. Frontend setup

```bash
cd client
npm install
```

Start the frontend:

```bash
npm start
```

Frontend runs on [http://localhost:3000](http://localhost:3000)
Backend runs on [http://localhost:5000](http://localhost:5000)

## 🔑 IP Validation

* The file `server/localIPMap.json` contains allowed IP addresses.
* When a user tries to mark attendance, the system checks the client IP against this file.
* If the IP is authorized → attendance is recorded.
* If not → request is rejected with a `403 Forbidden`.

## 📡 API Endpoints (Basic)

### Auth

* `POST /api/auth/register` → Register new user
* `POST /api/auth/login` → Login and receive JWT

### Attendance

* `POST /api/attendance/mark` → Mark attendance (only from allowed IP)
* `GET /api/attendance/me` → Get current user’s attendance records

## 🗄️ Database Models

### User.js

* `name`
* `email`
* `passwordHash`
* `role` (admin/employee)

### Attendance.js

* `user`
* `date`
* `time`
* `ip`
* `userAgent`

## 🔒 Security Notes

* All passwords are hashed with bcrypt.
* JWT used for authentication.
* Allowed IPs configurable via `localIPMap.json`.
* Recommended: Run backend behind HTTPS.

## 🐳 Deployment

* Supports Docker (add your `docker-compose.yml`).
* Ensure `X-Forwarded-For` headers are set if behind reverse proxy.

##

---

✅ Now your README matches your project (`client/` + `server/` + IP validation with `localIPMap.json`).
