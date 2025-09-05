# GoREST API Automation

This project contains automated tests for the public **GoREST v2** API using **Postman** and **Newman**.
It is part of a technical challenge to assess API test automation skills.

## 📌 Content
- **Postman Collection**: Requests for `users`, `posts`, and `todos`.
- **Positive cases**: Post/todo creation, user creation, update and deletion.
- **Bad cases**: No authentication, invalid data, nonexistent resources, duplicates.
- **Validations**:
- Status code (200, 201, 204, 401, 404, 422).
- Response headers.
- Response structure (JSON Schema).
- Specific values ​​(e.g., name updated, status successful).
- Response times.
- **Reports**:
- Detailed HTML (`htmlextra`).
- XML ​​(`junit`) for CI/CD.

---

## 🚀 How to run locally

1. **Install dependencies**
```bash
npm install -g newman newman-reporter-htmlextra newman-reporter-junit
```
## Linux / macOS
```
export GOREST_TOKEN="Your_token_goes_here"
```

## Windows PowerShell
```
$env:GOREST_TOKEN = "Your_token_goes_here"
```
# Running the colletion and generating the report

## HTML (htmlextra)

```
newman run ".\postman\GoRest_v2_ApiTests.postman_collection.json" `
  -e ".\postman\GoRest_Public_v2.postman_environment.json" `
  --env-var "token=$env:GOREST_TOKEN" `
  -r htmlextra `
  --reporter-htmlextra-export ".\reports\test-report.html"
  
```

## Junit

```
newman run ".\postman\GoRest_v2_ApiTests.postman_collection.json" `
  -e ".\postman\GoRest_Public_v2.postman_environment.json" `
  --env-var "token=$env:GOREST_TOKEN" `
  -r junit `
  --reporter-htmlextra-export ".\reports\gorest-report.html" `
  --reporter-junit-export ".\reports\gorest-report.xml" `
  --export-environment ".\reports\final-environment.json" `
  --bail
```
