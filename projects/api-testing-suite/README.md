# API Testing Suite

![REST Assured](https://img.shields.io/badge/REST%20Assured-5.3-green?style=for-the-badge&logo=rest-assured)
![Java](https://img.shields.io/badge/Java-17-red?style=for-the-badge&logo=java)
![TestNG](https://img.shields.io/badge/TestNG-7.5-orange?style=for-the-badge)
![Maven](https://img.shields.io/badge/Maven-3.8-red?style=for-the-badge&logo=apache-maven)
![JSON](https://img.shields.io/badge/JSON-Schema-blue?style=for-the-badge&logo=json)

A comprehensive API testing framework built with REST Assured and Java, designed for insurance domain services. This framework supports data-driven testing, JSON schema validation, and seamless CI/CD integration for automated API regression testing.

## 🚀 Features

- **REST API Automation**: Complete RESTful API testing with REST Assured
- **Data-Driven Testing**: Support for Excel, JSON, and CSV data sources
- **Schema Validation**: JSON schema validation for contract testing
- **Authentication**: Support for OAuth, API Key, and Basic Auth
- **Parallel Execution**: Run API tests in parallel using TestNG
- **CI/CD Integration**: Jenkins and GitHub Actions pipelines
- **Comprehensive Reporting**: Extent Reports with request/response logging
- **Environment Management**: Easy configuration for Dev, QA, and Prod environments
- **Error Handling**: Robust error handling and retry mechanisms

## 🛠️ Tech Stack

- **Core**: REST Assured 5.3, Java 17
- **Testing**: TestNG 7.5, JUnit 5
- **Build**: Maven 3.8
- **Data**: Apache POI (Excel), Jackson (JSON), OpenCSV
- **Validation**: JSON Schema Validator
- **Reporting**: Extent Reports 5.x, Allure Reports
- **CI/CD**: Jenkins, GitHub Actions
- **Mocking**: WireMock (for API mocking)

## 📁 Project Structure

```
api-testing-suite/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── com/
│   │   │   │   └── insurance/
│   │   │   │       ├── api/
│   │   │   │       │   ├── base/
│   │   │   │       │   │   ├── BaseAPITest.java
│   │   │   │       │   │   ├── APIClient.java
│   │   │   │       │   │   └── ConfigReader.java
│   │   │   │       │   ├── client/
│   │   │   │       │   │   ├── RESTAssuredClient.java
│   │   │   │       │   │   ├── AuthHandler.java
│   │   │   │       │   │   └── RequestBuilder.java
│   │   │   │       │   ├── config/
│   │   │   │       │   │   ├── APIConfig.java
│   │   │   │       │   │   └── Endpoints.java
│   │   │   │       │   ├── utils/
│   │   │   │       │   │   ├── JSONUtils.java
│   │   │   │       │   │   ├── ExcelUtils.java
│   │   │   │       │   │   ├── SchemaValidator.java
│   │   │   │       │   │   └── ResponseValidator.java
│   │   │   │       │   └── models/
│   │   │   │       │       ├── PolicyRequest.java
│   │   │   │       │       ├── PolicyResponse.java
│   │   │   │       │       ├── ClaimRequest.java
│   │   │   │       │       └── ClaimResponse.java
│   │   │   │       └── config/
│   │   │   │           ├── Config.properties
│   │   │   │           └── Endpoints.json
│   │   └── resources/
│   │       ├── config/
│   │       │   ├── dev.properties
│   │       │   ├── qa.properties
│   │       │   └── prod.properties
│   │       ├── schemas/
│   │       │   ├── policy-schema.json
│   │       │   ├── claim-schema.json
│   │       │   └── user-schema.json
│   │       └── testdata/
│   │           ├── api-testdata.xlsx
│   │           └── api-testdata.json
│   └── test/
│       ├── java/
│       │   ├── com/
│       │   │   └── insurance/
│       │   │       ├── users/
│       │   │       │   ├── UserAPITest.java
│       │   │       │   ├── AuthAPITest.java
│       │   │       │   └── ProfileAPITest.java
│       │   │       ├── policies/
│       │   │       │   ├── PolicyCreationTest.java
│       │   │       │   ├── PolicyUpdateTest.java
│       │   │       │   └── PolicySearchTest.java
│       │   │       ├── claims/
│       │   │       │   ├── ClaimSubmissionTest.java
│       │   │       │   ├── ClaimApprovalTest.java
│       │   │       │   └── ClaimStatusTest.java
│       │   │       └── integration/
│       │   │           ├── EndToEndAPITest.java
│       │   │           └── RegressionAPITest.java
│       └── resources/
│           ├── suites/
│           │   ├── api-smoke-suite.xml
│           │   ├── api-regression-suite.xml
│           │   └── api-full-suite.xml
│           └── data/
│               └── test-data.json
├── pom.xml
├── Jenkinsfile
├── .github/
│   └── workflows/
│       └── api-ci.yml
├── test-output/
├── reports/
└── README.md
```

## 📋 Prerequisites

- Java 17 or higher
- Maven 3.8 or higher
- REST Assured 5.3
- Jenkins (for CI/CD)
- IDE (IntelliJ IDEA or Eclipse)

## 🔧 Installation

1. Clone the repository:
```bash
git clone https://github.com/reddyjyotheeswar/api-testing-suite.git
cd api-testing-suite
```

2. Install dependencies:
```bash
mvn clean install
```

3. Configure API endpoints:
```bash
# Edit src/main/resources/config/dev.properties
# Update base URL, authentication credentials
```

## ▶️ Running Tests

### Run all API tests:
```bash
mvn test
```

### Run specific suite:
```bash
mvn test -Dsuite=api-smoke-suite.xml
mvn test -Dsuite=api-regression-suite.xml
```

### Run for specific environment:
```bash
mvn test -Denv=dev
mvn test -Denv=qa
mvn test -Denv=prod
```

### Run with data provider:
```bash
mvn test -Ddataprovider=true
```

## 📊 API Endpoints Covered

### User Management
- `POST /api/users` - Create user
- `GET /api/users/{id}` - Get user by ID
- `PUT /api/users/{id}` - Update user
- `DELETE /api/users/{id}` - Delete user

### Policy Management
- `POST /api/policies` - Create policy
- `GET /api/policies/{id}` - Get policy details
- `PUT /api/policies/{id}` - Update policy
- `GET /api/policies/search` - Search policies

### Claims Management
- `POST /api/claims` - Submit claim
- `GET /api/claims/{id}` - Get claim status
- `PUT /api/claims/{id}/approve` - Approve claim
- `PUT /api/claims/{id}/reject` - Reject claim

## 📝 Writing API Tests

### Example API Test:
```java
@Test(priority = 1, dataProvider = "policyData")
public void testCreatePolicy(String policyName, String policyType, double amount) {
    PolicyRequest request = new PolicyRequest();
    request.setPolicyName(policyName);
    request.setPolicyType(policyType);
    request.setAmount(amount);
    
    Response response = given()
        .contentType(ContentType.JSON)
        .header("Authorization", "Bearer " + authToken)
        .body(request)
    .when()
        .post("/api/policies")
    .then()
        .statusCode(201)
        .extract()
        .response();
    
    PolicyResponse policyResponse = response.as(PolicyResponse.class);
    Assert.assertEquals(policyName, policyResponse.getPolicyName());
    Assert.assertEquals("PENDING", policyResponse.getStatus());
}
```

### Schema Validation:
```java
@Test
public void testPolicySchemaValidation() {
    Response response = given()
        .get("/api/policies/123");
    
    JSONSchemaValidator validator = JSONSchemaValidator.matchesJsonSchema(
        new File("src/main/resources/schemas/policy-schema.json")
    );
    
    validator.validate(response.asString());
}
```

### Authentication:
```java
@Test
public void testAuthenticatedRequest() {
    String authToken = AuthHandler.getAuthToken("username", "password");
    
    Response response = given()
        .header("Authorization", "Bearer " + authToken)
        .get("/api/users/profile");
    
    Assert.assertEquals(200, response.getStatusCode());
}
```

## 🔄 CI/CD Integration

### Jenkins Pipeline
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('API Tests') {
            steps {
                sh 'mvn test -Dsuite=api-smoke-suite.xml'
            }
        }
        stage('Regression Tests') {
            steps {
                sh 'mvn test -Dsuite=api-regression-suite.xml'
            }
        }
        stage('Report') {
            steps {
                publishHTML target: [
                    reportDir: 'reports/extent-reports',
                    reportFiles: 'index.html',
                    reportName: 'API Test Report'
                ]
            }
        }
    }
}
```

### GitHub Actions
```yaml
name: API Testing CI
on: [push, pull_request]
jobs:
  api-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 17
        uses: actions/setup-java@v2
        with:
          java-version: '17'
      - name: Build with Maven
        run: mvn clean install
      - name: Run API Tests
        run: mvn test -Dsuite=api-full-suite.xml
```

## 📊 Reporting

Test reports include:
- **Request/Response Logging**: Complete HTTP request and response details
- **Response Time**: API response time metrics
- **Schema Validation**: JSON schema compliance results
- **Error Analysis**: Detailed error information and stack traces
- **Test Execution Summary**: Pass/fail statistics

## 🎯 Key Achievements

- ✅ Automated 50+ API endpoints
- ✅ Reduced API testing cycle from days to hours
- ✅ Implemented comprehensive schema validation
- ✅ Achieved 95% API coverage for critical services
- ✅ Integrated with CI/CD for continuous testing
- ✅ Support for multiple authentication mechanisms

## 🔐 Security Features

- **Secure Credential Management**: Encrypted API keys and tokens
- **Authentication Testing**: OAuth, API Key, Basic Auth support
- **Authorization Testing**: Role-based access control validation
- **Data Masking**: Sensitive data masking in reports
- **HTTPS Enforcement**: All API calls over secure connections

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.

## 👤 Author

**Jyotheeswar Reddy N**
- LinkedIn: [linkedin.com/in/njreddy](https://www.linkedin.com/in/njreddy)
- GitHub: [github.com/reddyjyotheeswar](https://github.com/reddyjyotheeswar)

## 🙏 Acknowledgments

- REST Assured team
- TestNG framework
- Insurance domain APIs from Infosys projects
