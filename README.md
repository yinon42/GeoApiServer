Sure! Here's a structured guide to help you get started with the documentation:

---

# API Service Documentation

This document provides an overview of the API service, Android library, and the Android Example application. It includes setup instructions, usage examples, and additional information useful for developers.

---

## Table of Contents

1. [Introduction](#introduction)
2. [API Service Setup](#api-service-setup)
3. [Android Library Setup](#android-library-setup)
4. [Android Example Application Setup](#android-example-application-setup)
5. [Usage Examples](#usage-examples)
6. [Error Handling](#error-handling)
7. [GitHub Pages and Repository Access](#github-pages-and-repository-access)
8. [Additional Information](#additional-information)

---

## Introduction

The API service enables users to check if a point (latitude, longitude) lies within the geographical boundaries of a given country. This is useful for applications that require geolocation-based features, such as determining the user's location relative to country borders.

Additionally, an Android library is provided to integrate the API service into Android applications, along with an Android example application for easy reference.

---

## API Service Setup

### Prerequisites
1. Java 11 or later
2. Gradle 6.x or later
3. Firebase SDK for Firestore

### Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/your-repository/geo-api.git
   ```

2. Navigate to the API project directory:

   ```bash
   cd geo-api
   ```

3. Build the project using Gradle:

   ```bash
   ./gradlew build
   ```

4. Start the API service:

   ```bash
   ./gradlew bootRun
   ```

5. The service will now be available at `http://localhost:8080`.

---

## Android Library Setup

### Prerequisites
1. Android Studio 4.x or later
2. Android SDK
3. Firebase SDK for Android

### Steps

1. Add the library to your `build.gradle` file:

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

3. Call the API to check if the point is within a country:

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

3. Set up Firebase with the necessary Firestore configurations.

4. Build and run the app on your emulator or device.

5. The app will allow you to test the `checkCountry` functionality.

---

## Usage Examples

### Check if a Point is Inside a Country

To use the API, send a POST request with the latitude and longitude:

```bash
POST http://localhost:8080/api/check-country
Content-Type: application/json

{
  "latitude": 46.505,
  "longitude": 38.770
}
```

Response:

```json
{
  "result": "The point is inside Armenia."
}
```

---

## Error Handling

- **400 - Bad Request**: The request body is missing required fields (latitude, longitude, country).
- **404 - Country Not Found**: The specified country was not found in the Firestore database.
- **500 - Server Error**: Internal server error, try again later.

### Example Response (Error)

```json
{
  "error": "The point is not in any known country."
}
```

---

## GitHub Pages and Repository Access

To access the full documentation, please visit the [GitHub Pages link](https://your-github-page-link).

### Repository Structure

- `/src`: Source code for the API and Android library.
- `/docs`: Documentation for setup, usage, and API reference.
- `/example`: Example Android app using the library.

---

## Additional Information

### Screenshots and Diagrams

For detailed images and architecture diagrams, please refer to the `/docs/images` directory.

- **API Diagram**: Illustrates the interaction between the API service and the Android application.
- **Geo Location Flow**: A flowchart detailing how geographical checks are performed.

### FAQs

- **How do I add new countries?**
  - You can add countries by uploading geoJSON files into the Firestore database.

- **Can I use this service for large datasets?**
  - Yes, but consider implementing pagination for handling large numbers of countries.

---

## Conclusion

This documentation provides everything you need to set up and use the geo location API service, along with the Android library and example app. Feel free to reach out if you have any questions or need further assistance.

---

The documentation should be saved in the `docs` folder of your project, and you can generate a GitHub Pages link by following the instructions in the [GitHub Pages Documentation](https://docs.github.com/en/pages/getting-started-with-github-pages).

Let me know if you'd like to adjust or expand any specific section!
