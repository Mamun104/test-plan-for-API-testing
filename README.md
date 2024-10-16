
# 🎯 **Dmoney Users API - Test Plan** 🎯

This repository contains the test plan for the Dmoney Users API. The document provides a comprehensive approach for testing the API’s functionality, security, and performance to ensure it works as intended and integrates seamlessly with other systems.
---

## 🚀 **Project Overview**

- **Project Name**: Dmoney Users API  
- **API Name**: Dmoney Users  
- **Purpose**: This document outlines the approach for testing the Dmoney Users API, ensuring functionality, error handling, and integration with other systems.

---

## 📝 **Test Objectives**

| 🎯 **Objective**                  |
|------------------------------------|
| ✔️ Validate the functionality of the Dmoney Users API. |
| ✔️ Ensure the API handles invalid inputs appropriately. |
| ✔️ Test data integrity, security, and error handling.   |
| ✔️ Verify API performance under different scenarios.    |

---

## 📍 **Scope of Testing**

| **In-Scope**                                                                                  | **Out-of-Scope**                                       |
|-----------------------------------------------------------------------------------------------|--------------------------------------------------------|
| 🔹 POST `/user/login` <br> 🔹 GET `/user/list` <br> 🔹 GET `/user/search/id/{id}`              | 🔸 Front-end validation                                |
| 🔹 POST `/user/create` <br> 🔹 PUT `/user/update/{id}` <br> 🔹 DELETE `/user/delete/{id}`      | 🔸 Internal database tests unrelated to API calls      |

---

## 🔧 **Test Environment**

| **Test Environment**  | **API Base URL**              | **Database**    | **Authentication**           |
|-----------------------|------------------------------|-----------------|------------------------------|
| Development / Staging  | `http://dmoney.roadtocareer.net` | PostgreSQL      | JWT Token + X-AUTH-SECRET-KEY |

---

## 📊 **Test Data**

| **Field**             | **Example Value**              |
|-----------------------|--------------------------------|
| 📧 Email              | `test@gmail.net`      |
| 🔑 Password           | `1234`                         |
| 🔐 Token              | `eyJhbGciOiJIUzI1NiIsInR5...`  |
| 🆔 User ID            | `4153`                         |

---

## 🧪 **Test Scenarios**

| **Scenario**                        | **API Method**               | **Input Data**                                      | **Expected Output**                                                                                     |
|-------------------------------------|------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| ✅ **Login with valid credentials**  | POST `/user/login`           | `{ "email": "test@gmail.net", "password": "1234" }` | Status: **200 OK** <br> Token returned and set as environment variable                                   |
| 🚫 **Login with wrong email**        | POST `/user/login`           | `{ "email": "test@gmailt", "password": "1234" }`    | Status: **404 Not Found** <br> Response: `{ "message": "User not found" }`                              |
| 🚫 **Login with wrong password**     | POST `/user/login`           | `{ "email": "test@gmail.net", "password": "123" }` | Status: **401 Unauthorized** <br> Response: `{ "message": "Password incorrect" }`                        |
| 👥 **Get user list**                 | GET `/user/list`             | Authorization Token                                | Status: **200 OK** <br> Response: `{ "message": "User list", "users": [...] }`                          |
| 🛑 **Get user list with invalid token** | GET `/user/list`          | Invalid Authorization Token                        | Status: **403 Forbidden** <br> Response: `{ "error": { "message": "Token expired" }}`                    |
| ✏️ **Create a new user**             | POST `/user/create`          | `{ "name": "John Doe", "email": "john.doe@example.com", "password": "1234", "phone_number": "01504789428" }` | Status: **201 Created** <br> Response: `{ "message": "User created", "user": {...} }`                    |
| 🚫 **Create existing user**          | POST `/user/create`          | `{ "name": "test user", "email": "test@gmail.net", "password": "1234" }` | Status: **208 Already Reported** <br> Response: `{ "message": "User already exists" }`                   |
| 🔄 **Update user details**           | PUT `/user/update/{id}`      | `{ "name": "John Doe", "email": "john.updated@example.com", "phone_number": "01504789428" }` | Status: **200 OK** <br> Response: `{ "message": "User updated successfully" }`                          |
| ❌ **Delete user by ID**             | DELETE `/user/delete/{id}`   | User ID 4153                                       | Status: **200 OK** <br> Response: `{ "message": "User deleted successfully" }`                           |

---

## 🛠 **Types of Testing**

| **Type of Testing**     | **Description**                                                                                             |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| 🔍 **Functional Testing** | Validate the functionality of the API.                                                                     |
| 🔒 **Security Testing**   | Ensure token validation, access control, and secure data handling.                                          |
| 🎯 **Boundary Testing**   | Test edge cases, such as invalid email formats or missing required fields.                                  |
| ⚡ **Performance Testing**| Measure API response times and behavior under load.                                                         |

---

## 🧰 **Tools Used**

| **Tool**                | **Purpose**                                  |
|-------------------------|----------------------------------------------|
| 🛠 **Postman**           | API Functional Testing                       |
| 📊 **JMeter**            | Load and Performance Testing                 |
| 📜 **Swagger**           | API Documentation and Reference              |

---

## 📅 **Test Schedule**

| **Activity**                       | **Start Date**    | **End Date**      |
|------------------------------------|-------------------|-------------------|
| 📝 Test Case Preparation            | 2024-10-18        | 2024-10-19        |
| 🚀 Functional Test Execution        | 2024-10-20        | 2024-10-22        |
| ⚡ Performance Test Execution       | 2024-10-23        | 2024-10-24        |
| 📑 Reporting & Closure              | 2024-10-25        | 2024-10-26        |

---

## 🔍 **Assumptions**

| **Assumption**                                                                                   |
|--------------------------------------------------------------------------------------------------|
| ✅ The API is stable and fully functional in the testing environment.                             |
| ✅ All required dependencies (database, services, etc.) will be available during the testing.     |

---

## ⚠️ **Risks**

| **Risk**                                                                                          |
|---------------------------------------------------------------------------------------------------|
| 🔺 API instability due to ongoing development.                                                     |
| 🔺 Incomplete test data might lead to missed edge cases or incorrect error handling scenarios.      |

---

## 📊 **Reporting**

- **Test results** will be shared via project management tools such as JIRA.
- **Logs and test evidence** (screenshots, error logs) will be uploaded to the test repository.

---
