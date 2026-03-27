# 🚀 Backend Technical Challenge – External Service Integration (Node.js)

## 📌 Overview

The goal of this technical challenge is to evaluate your ability to:

* Design and structure a backend project
* Integrate with external APIs
* Handle errors properly
* Apply clean architecture principles
* Write maintainable and testable code
* Document your work clearly

You will build a REST API in **Node.js** that consumes an external public API, processes the data, and exposes your own endpoints.

⏳ **Time limit:** 7 days
📦 **Delivery:** Public GitHub repository

---

# 🛠 Technical Requirements

## ✅ Mandatory

* **Node.js (LTS version)**
* Framework: Express.js
* Database: PostgreSQL or MongoDB
* ORM/ODM of your choice (Sequelize as preference)
* Environment variables configuration
* Proper error handling
* Basic validation
* At least 4 unit tests

---

# 🌍 External API Integration

You must integrate with at least one public external API:

* [https://pokeapi.co/](https://pokeapi.co/)
* [https://restcountries.com/](https://restcountries.com/)
* [https://openweathermap.org/api](https://openweathermap.org/api)
* [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/)

You may propose a different public API if justified in the README.

---

# 🏗 Functional Requirements

## 1️⃣ Main Endpoint

Create the following endpoint:

```
GET /api/resources
```

This endpoint must:

* Call the external API
* Transform the received data (do NOT return raw data)
* Persist relevant data in your database
* Return a structured response defined by you

### Example of transformation

If using RestCountries, instead of returning:

```json
{
  "name": { "common": "Spain" },
  "population": 47351567,
  ...
}
```

You could return:

```json
{
  "countryName": "Spain",
  "population": 47351567,
  "populationInMillions": 47.35,
  "region": "Europe",
  "lastUpdated": "2026-03-27T12:00:00Z"
}
```

We want to see data processing, not simple proxying.

---

## 2️⃣ Persistence Rules

* Avoid duplicates in database
* Store timestamp of last synchronization
* Properly design the schema/model
* Handle concurrent calls safely

---

## 3️⃣ Secondary Endpoint

Create a second endpoint to query stored data:

```
GET /api/resources/search
```

It should support:

* Filtering (e.g., by name, region, etc.)
* Pagination
* Sorting (optional but recommended)

---

## 4️⃣ Error Handling

Your API must properly handle:

* External API timeouts
* External API failures (5xx)
* Invalid query parameters
* Internal server errors

Return structured error responses:

```json
{
  "error": true,
  "message": "External service unavailable",
  "statusCode": 503
}
```

---

# 🧪 Testing (Required)

Include at least:

* 3 unit tests

You may use:

* Jest
* Vitest
* Supertest
* Or similar tools

We will evaluate:

* Meaningful test cases
* Proper mocking of external APIs
* Coverage of edge cases

---

# 📂 Project Structure

You are free to choose your structure, but we will evaluate:

* Separation of concerns
* Clean architecture principles
* Modularization
* Reusability

Example (not mandatory):

```
src/
 ├── controllers/
 ├── services/
 ├── repositories/
 ├── models/
 ├── routes/
 ├── middlewares/
 └── utils/
```

---

# 📖 Documentation

Your README must include:

* Project description
* Tech stack used
* Architecture decisions
* How to run locally
* How to run tests
* Environment variables needed
* API documentation (Postman collection or Swagger preferred)

---

# ⭐ Bonus Points (Optional)

These are not required but highly valued:

* JWT Authentication
* Rate limiting
* Background jobs / queue system
* Deployment (Render, Railway, Fly.io, etc.)
* OpenAPI/Swagger documentation

---

# 🚫 What We Do NOT Want

* A simple proxy to the external API
* Hardcoded values
* No validation
* No error handling
* No tests
* Poorly structured code

---

# 📦 Submission

1. Create a public GitHub repository
2. Push your complete solution
3. Share the repository link

---

# 💡 What We’re Looking For

We are not looking for perfection.

We are looking for:

* Clear thinking
* Solid backend fundamentals
* Production mindset
* Clean and maintainable code
* Good engineering judgment

---

If something is unclear, document your assumptions in the README.

Good luck 🚀
