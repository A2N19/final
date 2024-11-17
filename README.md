# final

# Portfolio Management System

## Table of Contents

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Setup Instructions](#setup-instructions)
5. [API Endpoints](#api-endpoints)
6. [Role-Based Access Control](#role-based-access-control)
7. [2FA Setup and Workflow](#2fa-setup-and-workflow)
8. [Postman Examples](#postman-examples)
9. [Visualization Pages](#visualization-pages)
10. [Project Structure](#project-structure)

---

## Project Overview

This project is a portfolio management system designed for users to manage portfolio items with images, descriptions, and timestamps. It includes authentication with role-based access control, 2FA, and integration of external APIs for financial data and news visualization.

---

## Features

1. **User Management**:

   - User registration with email, password, and optional 2FA setup.
   - Role-based access control for Admin and Editor roles.
   - Login with optional 2FA verification.
   - Password reset functionality via email.

2. **Portfolio Management**:

   - CRUD operations on portfolio items.
   - Carousel view for item images.
   - Timestamps for item creation, updates, and deletion.
   - Email notifications for item changes.

3. **API Integration**:

   - Fetch and visualize financial data from Alpha Vantage.
   - Fetch and display news data from NewsAPI.

4. **UI and UX**:
   - Responsive design with EJS templates and CSS.
   - Footer with "Nurseit Amir Group: BDA-2306" branding.

---

## Technologies Used

- **Backend**: Node.js, Express.js
- **Frontend**: EJS, CSS
- **Database**: MongoDB Atlas
- **Authentication**: JWT, bcrypt, speakeasy (2FA)
- **Email Service**: Nodemailer
- **External APIs**:
  - Alpha Vantage (Financial Data)
  - NewsAPI (News Data)

---

## Setup Instructions

1. **Clone the Repository**:

   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Install Dependencies**:

   ```bash
   npm install
   ```

3. **Environment Variables**:
   Create a `.env` file and add the following:

   ```
   PORT=3000
   MONGO_URI=<Your MongoDB Connection String>
   JWT_SECRET=<Your JWT Secret>
   EMAIL_USER=<Your Email Address>
   EMAIL_PASS=<Your Email Password>
   ALPHA_VANTAGE_API_KEY=<Your Alpha Vantage API Key>
   NEWS_API_KEY=<Your NewsAPI Key>
   CLIENT_URL=http://localhost:3000
   ```

4. **Run the Server**:

   ```bash
   node server.js
   ```

5. **Access Application**:
   Open `http://localhost:3000` in your browser.

---

## API Endpoints

### Auth Routes

| Method | Endpoint                    | Description                |
| ------ | --------------------------- | -------------------------- |
| POST   | `/api/auth/register`        | Register a new user.       |
| POST   | `/api/auth/login`           | Login an existing user.    |
| POST   | `/api/auth/verify-2fa`      | Verify 2FA code.           |
| POST   | `/api/auth/forgot-password` | Send password reset email. |

### Portfolio Routes

| Method | Endpoint         | Description                      |
| ------ | ---------------- | -------------------------------- |
| GET    | `/portfolio`     | View all portfolio items.        |
| POST   | `/portfolio`     | Create a new portfolio item.     |
| PUT    | `/portfolio/:id` | Update a portfolio item by ID.   |
| DELETE | `/portfolio/:id` | Delete a portfolio item by ID.   |
| GET    | `/portfolio/all` | Fetch all portfolio items (API). |

### API Integration Routes

| Method | Endpoint                      | Description                     |
| ------ | ----------------------------- | ------------------------------- |
| GET    | `/api/financial-data/:symbol` | Fetch financial data by symbol. |
| GET    | `/api/news/:topic`            | Fetch news data by topic.       |

---

## Role-Based Access Control

- **Admin**:

  - Full CRUD operations on portfolio items.
  - Access to all API routes.
  - Can view, create, update, and delete items.

- **Editor**:
  - Can create portfolio items.
  - Access to view API data.

---

## 2FA Setup and Workflow

1. **Registration**:

   - User can enable 2FA during registration.
   - A QR code is generated for Google Authenticator setup.

2. **Login with 2FA**:

   - User enters their 2FA code after providing valid login credentials.

3. **2FA Verification**:
   - If the entered code matches, access is granted.

---

## Postman Examples

### Register User

**POST**: `http://localhost:3000/api/auth/register`

```json
{
  "username": "testuser@example.com",
  "password": "password123",
  "firstName": "John",
  "lastName": "Doe",
  "age": 25,
  "gender": "male",
  "twoFactorEnabled": true
}
```

### Login User

**POST**: `http://localhost:3000/api/auth/login`

```json
{
  "username": "testuser@example.com",
  "password": "password123"
}
```

### Create Portfolio Item

**POST**: `http://localhost:3000/portfolio`

```json
{
  "title": "My Portfolio Item",
  "description": "This is a test portfolio item.",
  "images": [
    "https://example.com/image1.jpg",
    "https://example.com/image2.jpg",
    "https://example.com/image3.jpg"
  ]
}
```

### Update Portfolio Item

**PUT**: `http://localhost:3000/portfolio/<item-id>`

```json
{
  "title": "Updated Portfolio Item",
  "description": "This portfolio item has been updated.",
  "images": [
    "https://example.com/image1_updated.jpg",
    "https://example.com/image2_updated.jpg",
    "https://example.com/image3_updated.jpg"
  ]
}
```

### Delete Portfolio Item

**DELETE**: `http://localhost:3000/portfolio/<item-id>`

---

## Visualization Pages

1. **Financial Data**:

   - Charts visualizing stock prices fetched from Alpha Vantage.

2. **News Data**:
   - Interactive list of news articles with links to the original sources.

---
