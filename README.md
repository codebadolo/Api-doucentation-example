# API Documentation

This documentation provides an overview of the available API endpoints, HTTP methods, required fields, and example `curl` commands for interacting with the API.

---

## **1. Register a User**
- **URL**: `/register/`
- **HTTP Method**: `POST`
- **Description**: Register a new user with the required fields.
- **Required Fields**:
  - `username`: string
  - `password`: string
  - `email`: string (optional)
  
- **cURL Example**:
  ```bash
  curl -X POST "http://127.0.0.1:8000/register/" \
  -H "Content-Type: application/json" \
  -d '{"username": "newuser", "password": "password123", "email": "user@example.com"}'
