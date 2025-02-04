# Geo API - Spring Boot & Firebase

## Overview
Geo API is a RESTful service built with Spring Boot and Firebase Firestore. The API allows users to determine whether a specific latitude and longitude coordinate lies within a given country's boundaries. This is useful for location-based applications that require geolocation validation.

## Features
- Check if a geographical point is inside a country's borders
- Android library integration for easy mobile application development
- Example Android app demonstrating usage
- Firebase Firestore as a scalable database backend
- RESTful API with structured JSON responses

## Technologies Used
- **Spring Boot** - Backend framework
- **Firebase Firestore** - Database
- **Java** - Programming language
- **Gradle** - Build tool
- **Android SDK** - Mobile integration

The API service runs on `http://localhost:8080`.

---

## API Endpoints

### 1. Check if a Point is Inside a Country
**POST /api/check-country**

#### Request:
```json
{
  "latitude": 46.505,
  "longitude": 38.770
}
```

#### Response:
```json
{
  "result": "The point is inside Armenia."
}
```

#### Error Responses:
- **400 - Bad Request**: Missing or incorrect latitude/longitude values.
- **404 - Country Not Found**: No matching country found in the database.
- **500 - Server Error**: Internal processing error.

Example error response:
```json
{
  "error": "The point is not in any known country."
}
```

---

## API Service Setup

### Prerequisites
- Java 11 or later
- Gradle 6.x or later
- Firebase SDK for Firestore

### Setup Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repository/geo-api.git
   ```
2. Navigate to the project directory:
   ```bash
   cd geo-api
   ```
3. Build the project:
   ```bash
   ./gradlew build
   ```
4. Start the API service:
   ```bash
   ./gradlew bootRun
   ```
5. The service will be available at `http://localhost:8080`.

---

