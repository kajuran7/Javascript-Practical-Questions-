# Classwork: Understanding Cookies and JWT Authentication

## Goal of This Classwork

In this classwork, we will understand how login authentication works using:

* Cookies
* JWT Token
* Protected Routes
* Logout
* Admin Authorization

This is not a full project.
This is a simple backend practice to understand the concept clearly.

---

# 1. What We Are Going to Build

We are going to create a simple backend server with these routes:

```txt
GET    /
POST   /login
GET    /profile-cookie
GET    /profile-jwt
GET    /admin
POST   /logout
```

---

# 2. Concept Explanation

## What is a Cookie?

A cookie is a small piece of data stored in the browser.

Example:

After login, the server stores a token in the browser cookie.

Then, when the user visits another protected page, the browser sends that cookie back to the server.

So the server knows:

```txt
This user already logged in.
```

---

## What is JWT?

JWT means **JSON Web Token**.

JWT is like a digital ID card.

After login, the server creates a JWT token with user details like:

```json
{
  "id": 1,
  "email": "student@gmail.com",
  "role": "user"
}
```

Important:

Do not store passwords inside JWT.

---

## Cookie vs JWT

```txt
Cookie = Place to store data in the browser
JWT    = Token used to prove login
```

A JWT token can be stored inside a cookie.

---

# 3. Project Setup

## Step 1: Create Project Folder

```bash
mkdir cookie-jwt-classwork
cd cookie-jwt-classwork
```

## Step 2: Initialize Node Project

```bash
npm init -y
```

## Step 3: Install Required Packages

```bash
npm install express jsonwebtoken cookie-parser
```

## Step 4: Create Server File

Create a file named:

```txt
server.js
```

---

# 4. Full Code: server.js

Paste this full code inside `server.js`.

```javascript
const express = require("express");
const jwt = require("jsonwebtoken");
const cookieParser = require("cookie-parser");

const app = express();

// Middleware
app.use(express.json());
app.use(cookieParser());

// Secret key for JWT
const SECRET_KEY = "mysecretkey";

// Sample users
// Database is not used in this classwork.
// We use sample users only to understand the concept.
const users = [
  {
    id: 1,
    name: "Student User",
    email: "student@gmail.com",
    password: "12345",
    role: "user"
  },
  {
    id: 2,
    name: "Admin User",
    email: "admin@gmail.com",
    password: "admin123",
    role: "admin"
  }
];

// Home route
app.get("/", (req, res) => {
  res.send("Cookie and JWT Authentication Server Running");
});

// Login route
app.post("/login", (req, res) => {
  const { email, password } = req.body;

  // Find user by email and password
  const user = users.find(
    (u) => u.email === email && u.password === password
  );

  // If user not found
  if (!user) {
    return res.status(401).json({
      message: "Invalid email or password"
    });
  }

  // Create JWT token
  const token = jwt.sign(
    {
      id: user.id,
      name: user.name,
      email: user.email,
      role: user.role
    },
    SECRET_KEY,
    {
      expiresIn: "1h"
    }
  );

  // Store JWT token inside cookie
  res.cookie("token", token, {
    httpOnly: true,
    maxAge: 60 * 60 * 1000
  });

  res.json({
    message: "Login successful",
    token: token
  });
});

// Protected route using cookie
app.get("/profile-cookie", (req, res) => {
  const token = req.cookies.token;

  // Check if cookie token exists
  if (!token) {
    return res.status(401).json({
      message: "Please login first. Token not found in cookie."
    });
  }

  try {
    // Verify JWT token
    const decoded = jwt.verify(token, SECRET_KEY);

    res.json({
      message: "Profile accessed using cookie",
      user: decoded
    });
  } catch (error) {
    res.status(403).json({
      message: "Invalid or expired token"
    });
  }
});

// Protected route using Authorization header
app.get("/profile-jwt", (req, res) => {
  const authHeader = req.headers.authorization;

  // Check Authorization header
  if (!authHeader) {
    return res.status(401).json({
      message: "Authorization header not found"
    });
  }

  // Format: Bearer token
  const token = authHeader.split(" ")[1];

  if (!token) {
    return res.status(401).json({
      message: "Token not found"
    });
  }

  try {
    // Verify JWT token
    const decoded = jwt.verify(token, SECRET_KEY);

    res.json({
      message: "Profile accessed using JWT Authorization header",
      user: decoded
    });
  } catch (error) {
    res.status(403).json({
      message: "Invalid or expired token"
    });
  }
});

// Admin protected route
app.get("/admin", (req, res) => {
  const token = req.cookies.token;

  // Check cookie token
  if (!token) {
    return res.status(401).json({
      message: "Please login first"
    });
  }

  try {
    // Verify token
    const decoded = jwt.verify(token, SECRET_KEY);

    // Check user role
    if (decoded.role !== "admin") {
      return res.status(403).json({
        message: "Access denied. Admin only."
      });
    }

    res.json({
      message: "Welcome Admin",
      user: decoded
    });
  } catch (error) {
    res.status(403).json({
      message: "Invalid or expired token"
    });
  }
});

// Logout route
app.post("/logout", (req, res) => {
  // Clear cookie
  res.clearCookie("token");

  res.json({
    message: "Logout successful. Cookie removed."
  });
});

// Start server
app.listen(5000, () => {
  console.log("Server running on http://localhost:5000");
});
```

---

# 5. Run the Server

In terminal, run:

```bash
node server.js
```

Expected output:

```txt
Server running on http://localhost:5000
```

Open browser:

```txt
http://localhost:5000
```

You should see:

```txt
Cookie and JWT Authentication Server Running
```

---

# 6. Testing Using Postman

## Test 1: Home Route

Method:

```txt
GET
```

URL:

```txt
http://localhost:5000/
```

Expected output:

```txt
Cookie and JWT Authentication Server Running
```

---

## Test 2: Login as Normal User

Method:

```txt
POST
```

URL:

```txt
http://localhost:5000/login
```

Body:

```json
{
  "email": "student@gmail.com",
  "password": "12345"
}
```

Expected output:

```json
{
  "message": "Login successful",
  "token": "your_jwt_token_here"
}
```

After login, a cookie named `token` will be stored.

---

## Test 3: Access Profile Using Cookie

Method:

```txt
GET
```

URL:

```txt
http://localhost:5000/profile-cookie
```

Expected output:

```json
{
  "message": "Profile accessed using cookie",
  "user": {
    "id": 1,
    "name": "Student User",
    "email": "student@gmail.com",
    "role": "user"
  }
}
```

---

## Test 4: Access Profile Using JWT Header

Method:

```txt
GET
```

URL:

```txt
http://localhost:5000/profile-jwt
```

Go to **Headers** in Postman and add:

```txt
Authorization: Bearer your_token_here
```

Expected output:

```json
{
  "message": "Profile accessed using JWT Authorization header",
  "user": {
    "id": 1,
    "name": "Student User",
    "email": "student@gmail.com",
    "role": "user"
  }
}
```

---

## Test 5: Access Admin Route as Normal User

First login using:

```json
{
  "email": "student@gmail.com",
  "password": "12345"
}
```

Then test:

```txt
GET http://localhost:5000/admin
```

Expected output:

```json
{
  "message": "Access denied. Admin only."
}
```

This happens because the normal user role is:

```txt
user
```

---

## Test 6: Login as Admin User

Method:

```txt
POST
```

URL:

```txt
http://localhost:5000/login
```

Body:

```json
{
  "email": "admin@gmail.com",
  "password": "admin123"
}
```

Then test:

```txt
GET http://localhost:5000/admin
```

Expected output:

```json
{
  "message": "Welcome Admin",
  "user": {
    "id": 2,
    "name": "Admin User",
    "email": "admin@gmail.com",
    "role": "admin"
  }
}
```

---

## Test 7: Logout

Method:

```txt
POST
```

URL:

```txt
http://localhost:5000/logout
```

Expected output:

```json
{
  "message": "Logout successful. Cookie removed."
}
```

Now try:

```txt
GET http://localhost:5000/profile-cookie
```

Expected output:

```json
{
  "message": "Please login first. Token not found in cookie."
}
```

---

# 7. Class Explanation Flow

## Login Flow

```txt
User sends email and password
        ↓
Server checks user details
        ↓
Server creates JWT token
        ↓
Server stores token inside cookie
        ↓
Login successful
```

---

## Protected Route Flow

```txt
User requests profile page
        ↓
Server checks cookie
        ↓
Server gets token from cookie
        ↓
Server verifies JWT token
        ↓
If token is valid, access allowed
        ↓
If token is missing or invalid, access denied
```

---

## Admin Route Flow

```txt
User requests admin page
        ↓
Server checks token
        ↓
Server verifies token
        ↓
Server checks user role
        ↓
If role is admin, access allowed
        ↓
If role is user, access denied
```

---

## Logout Flow

```txt
User clicks logout
        ↓
Server clears cookie
        ↓
Token removed from browser
        ↓
User must login again
```

---

# 8. Small Changes to Understand the Concept

## Practice 1: Change Token Expiry Time

In the login route, change:

```javascript
expiresIn: "1h"
```

to:

```javascript
expiresIn: "30s"
```

Then login, wait 30 seconds, and try to access the profile route.

You should get:

```json
{
  "message": "Invalid or expired token"
}
```

---

## Practice 2: Add More User Data to JWT

Inside `jwt.sign()`, add:

```javascript
phone: "0771234567"
```

Then login again and check the profile output.

Important:

Do not add password into JWT.

---

## Practice 3: Change User Role

Change student role from:

```javascript
role: "user"
```

to:

```javascript
role: "admin"
```

Then login as student and test the admin route.

Now the student can access the admin route because the role changed to admin.

---

# 9. Important Things to Remember

```txt
Cookie stores data in the browser.
JWT proves that the user is logged in.
Protected routes check the JWT before giving access.
Authorization checks what the user is allowed to access.
Logout clears the cookie.
```

---

# 10. Security Notes

For classwork, this simple method is okay.

For real projects:

* Do not store plain passwords.
* Use bcrypt to hash passwords.
* Do not hardcode the secret key.
* Use environment variables.
* Use HTTPS.
* Use `secure: true` in cookies when using HTTPS.
* Do not store sensitive data inside JWT.
* Do not store passwords inside JWT.

---

# 11. Final Understanding

At the end of this classwork, students should understand:

```txt
Login creates JWT.
JWT can be stored in cookie.
Protected routes verify JWT.
Role can control access.
Logout removes cookie.
```
