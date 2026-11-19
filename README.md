# URL Shortener

A full-stack URL shortener built with Node.js, Express, MongoDB, and EJS.

## Project Purpose

The purpose of this project is to practice and learn about server-side rendering in full-stack applications. It demonstrates how an Express server can handle application logic, authentication, database operations, and dynamically rendered EJS pages without relying on a separate front-end framework.

## Features

- Create short URLs using NanoID
- Redirect short URLs to their original destinations
- Track the number of clicks for each URL
- Register and log in to a personal account
- Hash passwords with bcrypt
- Authenticate protected routes with JWT cookies
- Separate URL access for `NORMAL` and `ADMIN` roles
- View URL analytics through the API
- Render pages server-side with EJS templates

## Tech Stack

- Node.js
- Express 5
- MongoDB and Mongoose
- EJS
- JSON Web Tokens
- bcrypt
- NanoID
- cookie-parser
- dotenv

## Project Structure

```text
.
├── controllers/       # User and URL request handlers
├── middleware/        # Authentication and role authorization
├── models/            # Mongoose schemas
├── routes/            # Page and API routes
├── service/           # Authentication-related service
├── views/             # Server-rendered EJS templates
├── connection.js      # MongoDB connection
├── index.js           # Application entry point
└── package.json
```

## Prerequisites

- Node.js
- npm
- MongoDB, either running locally or available through MongoDB Atlas

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/IFFAT12375/URL-Shortner.git
   cd URL-Shortner
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Create a `.env` file in the project root:

   ```env
   MONGO_URL=mongodb://127.0.0.1:27017/url-shortener
   JWT_SECRET=replace-with-a-long-random-secret
   ```

   - `MONGO_URL`: MongoDB connection string
   - `JWT_SECRET`: Secret key used to sign and verify JWT tokens

4. Start the development server:

   ```bash
   npm run dev
   ```

5. Open `http://localhost:8000` in a browser.

## Main Routes

| Method | Route | Description |
| --- | --- | --- |
| `GET` | `/register` | Render the registration page |
| `POST` | `/register` | Create a new user |
| `GET` | `/login` | Render the login page |
| `POST` | `/login` | Authenticate a user |
| `GET` | `/logout` | Clear the authentication cookie |
| `GET` | `/` | Render the authenticated URL dashboard |
| `POST` | `/shorten` | Create a short URL |
| `GET` | `/:shortId` | Redirect to the original URL and increment its click count |
| `GET` | `/urls/analytics/:shortId` | Return analytics for an accessible URL |

## Role Behavior

- `NORMAL` users can create URLs and view the URLs they created.
- `ADMIN` users can view URLs created by all users.
- URL analytics are restricted to administrators or the user who created the URL.

## Server-Side Rendering Flow

1. The browser sends an HTTP request to Express.
2. Route middleware verifies the JWT and user role when required.
3. Controllers query MongoDB through Mongoose.
4. EJS receives the resulting data and renders the complete HTML response.
5. Express sends the rendered page back to the browser.

## Learning Areas

This project is intended to help practice:

- Building a full-stack application with Express
- Server-side rendering with EJS
- Routing and middleware
- MongoDB schema design and queries
- Cookie-based JWT authentication
- Password hashing
- Role-based authorization
- Form handling and redirects
- Basic click analytics
