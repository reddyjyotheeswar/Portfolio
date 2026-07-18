# Insurance Test Automation Framework

![Selenium](https://img.shields.io/badge/Selenium-WebDriver-green?style=for-the-badge&logo=selenium)
![Java](https://img.shields.io/badge/Java-17-red?style=for-the-badge&logo=java)
![TestNG](https://img.shields.io/badge/TestNG-7.5-orange?style=for-the-badge)
![Maven](https://img.shields.io/badge/Maven-3.8-red?style=for-the-badge&logo=apache-maven)
![Jenkins](https://img.shields.io/badge/Jenkins-2.400-blue?style=for-the-badge&logo=jenkins)

A robust hybrid test automation framework designed for insurance domain applications using Selenium WebDriver, Java, and TestNG. This framework implements the Page Object Model design pattern for maintainable test automation and includes CI/CD integration with Jenkins.

## 🚀 Features

- **Page Object Model**: Clean separation between test logic and page elements
- **Data-Driven Testing**: Support for Excel and JSON data sources
- **Parallel Execution**: Run tests in parallel using TestNG
- **CI/CD Integration**: Jenkins pipeline for continuous testing
- **Comprehensive Reporting**: Extent Reports with screenshots and logs
- **Cross-Browser Support**: Chrome, Firefox, Edge compatibility
- **Reusable Components**: Common utilities for web elements, waits, and actions
- **Configuration Management**: Environment-specific configurations

## 🛠️ Tech Stack

- **Core**: Selenium WebDriver 4.x, Java 17
- **Testing**: TestNG 7.5, JUnit 5
- **Build**: Maven 3.8
- **Reporting**: Extent Reports 5.x, Allure Reports
- **Design Pattern**: Page Object Model, Factory Pattern
- **Data**: Apache POI (Excel), Jackson (JSON)
- **CI/CD**: Jenkins, GitHub Actions

## 📁 Project Structure

```
insurance-test-automation/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── com/
│   │   │   │   └── insurance/
│   │   │   │       ├── base/
│   │   │   │       │   ├── BaseTest.java
│   │   │   │       │   ├── WebDriverFactory.java
│   │   │   │       │   └── ConfigReader.java
│   │   │   │       ├── pages/
│   │   │   │       │   ├── LoginPage.java
│   │   │   │       │   ├── DashboardPage.java
│   │   │   │       │   ├── ClaimsPage.java
│   │   │   │       │   └── PolicyPage.java
│   │   │   │       ├── elements/
│   │   │   │       │   ├── ButtonElement.java
│   │   │   │       │   ├── FormElement.java
│   │   │   │       │   └── TableElement.java
│   │   │   │       ├── actions/
│   │   │   │       │   ├── ClickAction.java
│   │   │   │       │   ├── SubmitAction.java
│   │   │   │       │   └── ValidateAction.java
│   │   │   │       ├── utils/
│   │   │   │       │   ├── ExcelUtils.java
│   │   │   │       │   ├── JSONUtils.java
│   │   │   │       │   ├── ScreenshotUtils.java
│   │   │   │       │   ├── WaitUtils.java
│   │   │   │       │   └── LoggerUtils.java
│   │   │   │       └── config/
│   │   │   │           ├── Config.properties
│   │   │   │           └── TestData.json
│   │   └── resources/
│   │       ├── config/
│   │       │   ├── dev.properties
│   │       │   ├── qa.properties
│   │       │   └── prod.properties
│   │       └── testdata/
│   │           ├── testdata.xlsx
│   │           └── testdata.json
│   └── test/
│       ├── java/
│       │   ├── com/
│       │   │   └── insurance/
│       │   │       ├── smoke/
│       │   │       │   ├── LoginTest.java
│       │   │       │   └── DashboardTest.java
│       │   │       ├── regression/
│       │   │       │   ├── ClaimsTest.java
│       │   │       │   ├── PolicyTest.java
│       │   │       │   └── IntegrationTest.java
│       │   │       └── api/
│       │   │           └── APITest.java
│       └── resources/
│           ├── suites/
│           │   ├── smoke-suite.xml
│           │   ├── regression-suite.xml
│           │   └── full-suite.xml
│           └── data/
│               └── test-data.xlsx
├── pom.xml
├── Jenkinsfile
├── .github/
│   └── workflows/
│       └── ci.yml
├── test-output/
├── reports/
└── README.md
```

## 📋 Prerequisites

- Java 17 or higher
- Maven 3.8 or higher
- Chrome/Firefox/Edge browsers
- Jenkins (for CI/CD)
- IDE (IntelliJ IDEA or Eclipse)

## 🔧 Installation

1. Clone the repository:
```bash
git clone https://github.com/reddyjyotheeswar/insurance-test-automation.git
cd insurance-test-automation
```

2. Install dependencies:
```bash
mvn clean install
```

3. Configure environment:
```bash
# Edit src/main/resources/config/dev.properties
# Update URL, credentials, and other configurations
```

## ▶️ Running Tests

### Run all tests:
```bash
mvn test
```

### Run specific suite:
```bash
mvn test -Dsuite=smoke-suite.xml
mvn test -Dsuite=regression-suite.xml
```

### Run with specific browser:
```bash
mvn test -Dbrowser=chrome
mvn test -Dbrowser=firefox
```

### Run in parallel:
```bash
mvn test -Dparallel=true
```

## 📊 Reporting

Test reports are generated in the following locations:
- **Extent Reports**: `reports/extent-reports/`
- **TestNG Reports**: `test-output/testng-results.xml`
- **Screenshots**: `reports/screenshots/`

## 🔄 CI/CD Integration

### Jenkins Pipeline
The project includes a Jenkinsfile for continuous integration:

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Report') {
            steps {
                publishHTML target: [
                    reportDir: 'reports/extent-reports',
                    reportFiles: 'index.html',
                    reportName: 'Extent Report'
                ]
            }
        }
    }
}
```

### GitHub Actions
Automated testing with GitHub Actions:

```yaml
name: CI/CD Pipeline
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 17
        uses: actions/setup-java@v2
        with:
          java-version: '17'
      - name: Build with Maven
        run: mvn clean install
      - name: Run Tests
        run: mvn test
```

## 📝 Writing Tests

### Example Page Object:
```java
public class LoginPage {
    private WebDriver driver;
    private By usernameField = By.id("username");
    private By passwordField = By.id("password");
    private By loginButton = By.id("login-btn");
    
    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }
    
    public void enterUsername(String username) {
        driver.findElement(usernameField).sendKeys(username);
    }
    
    public void enterPassword(String password) {
        driver.findElement(passwordField).sendKeys(password);
    }
    
    public DashboardPage clickLogin() {
        driver.findElement(loginButton).click();
        return new DashboardPage(driver);
    }
}
```

### Example Test Class:
```java
@Test(priority = 1)
public void testValidLogin() {
    LoginPage loginPage = new LoginPage(driver);
    loginPage.enterUsername("testuser");
    loginPage.enterPassword("password");
    DashboardPage dashboardPage = loginPage.clickLogin();
    Assert.assertTrue(dashboardPage.isDisplayed());
}
```

## 🎯 Key Achievements

- ✅ Achieved 70% test coverage for critical business flows
- ✅ Reduced regression testing time by 60% through automation
- ✅ Implemented data-driven testing reducing maintenance effort by 40%
- ✅ Integrated with CI/CD pipeline for continuous testing
- ✅ Support for multiple browsers and parallel execution

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.

## 👤 Author

**Jyotheeswar Reddy N**
- LinkedIn: [linkedin.com/in/njreddy](https://www.linkedin.com/in/njreddy)
- GitHub: [github.com/reddyjyotheeswar](https://github.com/reddyjyotheeswar)

## 🙏 Acknowledgments

- Selenium WebDriver team
- TestNG framework
- Extent Reports for excellent reporting
- Insurance domain knowledge from Infosys projects
