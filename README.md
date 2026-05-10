# Postman API Test Collection

This repository contains API test collections and environments built with Postman, demonstrating automated API testing practices for real-world web applications.

## 📌 About

These collections were created to validate REST API endpoints including authentication flows, CRUD operations, error handling, and edge cases. Tests are structured to be reusable and easy to integrate into CI/CD pipelines.

## 🛠️ Tools & Technologies

- [Postman](https://www.postman.com/) — API testing and automation
- [Newman](https://github.com/postmanlabs/newman) — Command-line runner for Postman collections
- Jenkins / GitLab CI — Pipeline integration

## 📁 Structure

```
Postman/
├── collections/
│   ├── auth-tests.json        # Login, token validation, logout flows
│   ├── user-api-tests.json    # CRUD operations for user endpoints
│   └── smoke-tests.json       # Core endpoint availability checks
├── environments/
│   ├── dev.json               # Development environment variables
│   └── staging.json           # Staging environment variables
└── README.md
```

## ✅ Test Coverage

- **Authentication** — Login, token refresh, unauthorized access handling
- **CRUD Operations** — Create, read, update, delete for core resources
- **Error Handling** — 4xx and 5xx response validation
- **Edge Cases** — Boundary values, missing fields, invalid data types
- **Smoke Tests** — Quick health checks for critical endpoints

## 🚀 Running the Tests

### Via Postman
1. Import the collection from the `collections/` folder
2. Import the environment file from the `environments/` folder
3. Select the environment and run the collection

### Via Newman (CLI)
```bash
# Install Newman
npm install -g newman

# Run a collection
newman run collections/smoke-tests.json -e environments/dev.json

# Run with HTML report
npm install -g newman-reporter-htmlextra
newman run collections/smoke-tests.json -e environments/dev.json -r htmlextra
```

### Via Jenkins / GitLab CI
Collections are integrated into CI/CD pipelines to run automatically on each deployment. Failed tests block the pipeline and notify the team.

## 📊 Sample Test Script (Postman)

```javascript
// Example: Validate login response
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response contains access token", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("access_token");
    pm.expect(jsonData.access_token).to.be.a("string").and.not.empty;
});

pm.test("Response time is acceptable", function () {
    pm.expect(pm.response.responseTime).to.be.below(2000);
});
```

## 👩‍💻 Author

**Sinem Kirtac** — QA Engineer  
10+ years in Manual, Automation, API & Performance Testing  
[LinkedIn](https://www.linkedin.com/in/sinem-kirtac-aa197670/) | sinemayk@gmail.com
