#  Digital Life Lessons — Backend API

This is the backend service for the **Digital Life Lessons** platform.
It provides secure REST APIs for lesson management, analytics, authentication, reporting, and admin controls.

---

##  Backend Overview

The backend is designed using a **modular REST architecture** with a focus on scalability, performance, and maintainability.

It supports:

* User lesson publishing system
* Admin moderation workflows
* Analytics aggregation for dashboards
* Contributor ranking engine
* Secure authentication flow
* Soft delete & audit tracking system

---

### 2️ Service Layer Pattern

Business logic is separated from routes:

```
routes → controllers → services → database
```

Benefits:

* Easier testing
* Cleaner logic
* Reusable query functions
* Prevents bloated route handlers

---

### 3️ Aggregation-Based Analytics Engine

Admin dashboard statistics are generated using **MongoDB aggregation pipelines** instead of multiple queries.

This allows:

* Single API for all dashboard data
* Reduced server load
* Faster analytics response
* Real-time platform insights

---

### 4️ Soft Delete & Audit Tracking System

Lessons are never immediately removed.

Instead:

```
isDeleted: true
deletedBy: email
deletedAt: timestamp
existStatus: "deleted"
```

Benefits:

* Recovery support
* Moderator accountability
* User activity tracking
* Historical analytics accuracy

---

### 5️ Role-Based Access Control (RBAC)

Each protected route verifies:

* Firebase token
* User role from database

Roles supported:

* user
* contributor
* admin

This ensures secure access to moderation and analytics endpoints.

---

##  Tech Stack

* **Node.js** – Runtime environment
* **Express.js** – REST API framework
* **MongoDB** – Database
* **Firebase Admin SDK** – Authentication verification
* **JWT Middleware** – Token validation
* **MongoDB Aggregation Pipelines** – Analytics engine

---

##  Security Features

* Firebase token verification middleware
* Role-based route protection
* Input validation & sanitization
* Rate limiting ready structure
* Soft-delete instead of hard delete
* Secure environment variable management

---

##  Core API Modules

### Lessons API

* Create lesson
* Edit lesson
* Soft delete lesson
* Feature lesson (admin)
* Review workflow

### Users API

* User profile
* Contributor stats
* Role management
* Activity tracking

### Admin API

* Dashboard analytics
* Report moderation
* Contributor ranking
* Featured lesson management

### Public API

* Home page data aggregation
* Featured lessons
* Top contributors
* Most saved lessons

---

##  Environment Variables

```
PORT=3000
MONGODB_URI=your_database_url
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_CLIENT_EMAIL=your_email
FIREBASE_PRIVATE_KEY=your_private_key
JWT_SECRET=your_secret
```

---

##  Running the Backend

```bash
npm install
npm run dev
```

Server will start at:

```
http://localhost:3000
```

---

##  Future Improvements

* Redis caching for analytics endpoints
* Message queue for heavy reporting workflows
* Search indexing with ElasticSearch
* API documentation using Swagger
* Automated moderation scoring system

