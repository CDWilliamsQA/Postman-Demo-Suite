# 🚀 Postman Demo Suite

Production-style API automation framework demonstration using Postman, environment configuration, and Newman CLI execution.

This repository showcases how enterprise QA teams design, structure, and automate API validation within modern delivery pipelines.

![API Tests](https://github.com/CDWilliamsQA/Postman-Demo-Suite/actions/workflows/api-tests.yml/badge.svg)

---

## 📌 Overview

The **Postman Demo Suite** is a professional portfolio project designed to demonstrate real-world API test automation practices. It models how QA engineers structure API regression suites, separate configuration from logic, and integrate tests into CI/CD pipelines.

This project reflects engineering standards used in distributed systems where APIs power authentication, transactions, data services, and microservice communication.

---

## 🧪 What This Suite Demonstrates

- Structured API test design using Postman collections  
- Environment-driven configuration for flexible execution  
- JavaScript-based test scripting and assertions  
- Automated execution using Newman CLI  
- CI/CD pipeline readiness  
- HTML report artifact generation  
- Contract validation via JSON Schema  
- Performance regression detection  
- Enterprise-style repository organisation  

---

## 📁 Repository Structure

| Folder/File | Purpose |
|-------------|---------|
| `/collections` | Postman collection exports containing requests and test logic |
| `/environments` | Environment variable configurations for flexible execution |
| `/docs` | Technical documentation and workflow references |
| `/reports` | Generated HTML test reports (ignored in Git) |
| `.github/workflows` | CI pipeline definitions |
| `README.md` | Project overview and usage guide |
| `LICENSE` | MIT open-source license |
| `.gitignore` | Standard repository exclusions |

---

## 🧠 Test Strategy

The suite follows a layered API regression approach:

| Layer | Purpose |
|------|---------|
| Auth Flow | Session simulation and token handling |
| Smoke Tests | Service availability checks |
| Functional Tests | Data integrity and schema validation |
| Negative Tests | Error handling and resilience checks |
| Performance Checks | Response time threshold enforcement |

### Contract Validation

Functional tests include JSON Schema validation to ensure API responses conform to expected structure.

### Performance Guardrails

CI will fail if response times exceed defined thresholds, protecting against performance regressions.

---

## 🧩 Example Use Case Scenario

This suite models how an enterprise QA team might validate APIs in systems such as:

- Order processing platforms  
- Authentication services  
- Inventory and stock systems  
- Customer data APIs  
- Internal microservices  

The design supports:

- Regression testing during releases  
- Smoke testing in CI pipelines  
- Environment promotion (Dev → Test → Staging → Prod)  
- Rapid defect isolation through response validation  

---

## ⚙ Running Tests via Newman

Install Newman globally:

```bash
npm install -g newman newman-reporter-html
```

Execute the suite locally:

```bash
newman run collections/demo_collection.json \
-e environments/demo_environment.json \
--reporters cli,html \
--reporter-html-export reports/test-report.html
```

---

## 📊 HTML Test Report Output

After execution, Newman generates a detailed HTML report:

```
reports/test-report.html
```

This provides a shareable artifact summarising:

- Requests executed  
- Assertions validated  
- Response times  
- Failure breakdowns  

Useful for CI pipelines and stakeholder reporting.

---

## 🔄 CI/CD Automation

API tests run automatically via **GitHub Actions** on every push and pull request.

The pipeline:

1. Installs Node.js  
2. Installs Newman + HTML reporter  
3. Executes the Postman collection  
4. Enforces response-time thresholds  
5. Validates API schema contracts  
6. Uploads an HTML test report artifact  

This ensures:

- Continuous API reliability monitoring  
- Early detection of breaking changes  
- Performance regression prevention  

---

## 🧩 Example Test Script

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response time under threshold", function () {
    const limit = Number(pm.environment.get("timeout_limit")) || 500;
    pm.expect(pm.response.responseTime).to.be.below(limit);
});

pm.test("Response contains required fields", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("id");
    pm.expect(jsonData).to.have.property("name");
});
```

---

## 🏗 Engineering Practices Demonstrated

- Stateless API test design  
- Separation of configuration and test logic  
- Reusable test structure  
- Automation-first regression strategy  
- Environment-driven execution  
- Pipeline-compatible test framework  
- Observability through structured reporting  
- Contract testing via schema validation  
- Performance threshold enforcement  

---

## 🎯 Why This Matters

Modern systems rely on APIs and microservices. Reliable API testing ensures:

- System stability  
- Integration reliability  
- Faster deployments  
- Reduced regression risk  

This project demonstrates the workflow and structure used by professional QA automation engineers working in enterprise environments.

---

## 🧠 Portfolio Value

This repository demonstrates:

- Practical API automation knowledge  
- Proficiency in Postman test scripting  
- Automation execution via CLI tooling  
- CI/CD integration awareness  
- Professional QA documentation standards  

---

**Maintained by:** Chris Williams  
**Focus Areas:** QA Automation | API Testing | CI/CD Integration
