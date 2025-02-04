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

## Android Library Setup

### Prerequisites
- Android Studio 4.x or later
- Android SDK
- Firebase SDK for Android

### Integration Steps
1. Add the library dependency in `build.gradle`:
   ```groovy
   dependencies {
       implementation 'com.example:geo-api-library:1.0.0'
   }
   ```
2. Initialize the library in your `Application` class:
   ```java
   GeoApiService geoApiService = new GeoApiService();
   geoApiService.initialize();
   ```
3. Use the library to check if a point is inside a country:
   ```java
   geoApiService.checkCountry(latitude, longitude, new GeoApiService.Callback() {
       @Override
       public void onResult(String result) {
           // Handle the result
       }
       @Override
       public void onError(String error) {
           // Handle the error
       }
   });
   ```

---

## Android Example Application Setup

### Steps
1. Clone the example app repository:
   ```bash
   git clone https://github.com/your-repository/geo-api-example.git
   ```
2. Open the project in Android Studio.
3. Configure Firebase Firestore.
4. Build and run the application.
5. Test the `checkCountry` functionality.

---

## GitHub Repository & Documentation
For full documentation, visit the [GitHub Pages link](https://your-github-page-link).

### Repository Structure
- `/src` - Source code for the API and Android library
- `/docs` - Documentation and setup guides
- `/example` - Sample Android application

---

## Additional Information

### Screenshots & Diagrams
- **API Diagram** - Illustrates API interaction with the database and client applications.
- **Geo Location Flow** - Describes the process of checking a point within country boundaries.

### FAQs
**How do I add new countries?**
- Upload new geoJSON files into Firestore.

**Can I handle large datasets?**
- Yes, implement pagination for better performance.

---

## Conclusion
Geo API provides an easy-to-use solution for geolocation validation. With API access, an Android library, and an example app, developers can quickly integrate geolocation checks into their applications. If you have questions, feel free to reach out!

For more details, check the [GitHub Pages documentation](https://your-github-page-link).

