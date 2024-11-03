
### Initial Requirements Gathering

- **Stakeholders**: 
  - Users
  - Admins
  - Maintainers

- **Functionality**: 
  - Different groups have different needs.

- **Non-Functional Requirements**: 
  - Page color
  - Logo

#### User Interface Design
- Based on specific guidelines and principles.
- List of functionalities leads to a specific view.

- Functional requirements can be translated into a set of controllers and corresponding views.
- Non-functional requirements do not translate into controllers but are essential for user experience (UX).

#### Importance of Requirement Gathering
- Avoid language ambiguity.
- Capture use cases and examples.
- Consider test cases and how requirements will be validated.

---

### Units of Implementation

- Break functional requirements down into small, implementable units.
- Each unit may become a single controller or may be combined into a single controller.

---

### Unit Testing

- Tests each individual unit of implementation.
- May involve a single controller or part of a controller.
- Clearly define inputs and expected outputs.
- Ensure testability in isolation: Can each unit be tested without the entire system? Create artificial data to check if a single update works.

---

### Test-Driven Development

- Write tests for the code before implementing the code.
- This forms the regression testing suite.

---

### Integration

- The application consists of multiple modules.
- Continuous Integration (CI) combined with a version control system.
- Each commit to the main branch triggers a re-evaluation of integration tests.

---

### System Level Testing

- A step beyond integration testing.
- Includes server and environment considerations.
- Primarily black-box testing to validate final usage.

---

### Non-Functional Tests

- Performance under load.
- Number of instances scaling.
- Cost evaluation.

---

### System Testing Automation

- Must simulate user interaction.
- Utilizes browser automation frameworks (e.g., Selenium).
- Includes database interactions and persistent connections.
- Typically involves a complete secondary system.

---

### User Acceptance Testing

- Deploy the final system.
- Tested by a restricted set of users (pilot).
- Beta testing involves beta software before production.



___________
---
---


## System Design Overview

### 1. Requirements Gathering

#### A. Stakeholders
- **Users:** End-users interacting with the system.
- **Admins:** Responsible for managing user accounts and system functionality.
- **Maintainers:** Handle system updates and operational integrity.

#### B. Requirements
1. **Functional Requirements:**
   - Define what the system should do.
   - Vary by user group:
     - Regular Users: Basic functionalities (account management, data entry).
     - Admins: User management, reporting, system monitoring.
     - Maintainers: System updates and troubleshooting.

2. **Non-Functional Requirements:**
   - Aesthetic Elements: Page colors, logo, branding.
   - Usability: User-friendliness and accessibility.
   - Performance: Load times and responsiveness.
   - Security: Data protection and user authentication.

#### C. Importance of Requirement Gathering
- Prevent language ambiguity with clear terminology.
- Capture use cases and examples for clarity.
- Consider test cases early to ensure requirements are testable.

### 2. Design Principles

#### A. User Interface Design
- Follow guidelines such as:
  - Consistency across interfaces.
  - Feedback mechanisms for user actions.
  - Error prevention strategies.

#### B. Functional Requirements Translation
- Map functional requirements to:
  - **Controllers:** Manage user requests and interactions.
  - **Views:** Display data and facilitate interactions.

### 3. Implementation Strategy

#### A. Units of Implementation
- Break functional requirements into small, manageable units (user stories).
- Each unit may correspond to a single controller or be combined into one.

#### B. Unit Testing
- Tests each individual implementation unit.
- Focus on:
  - Clearly defined inputs and expected outputs.
  - Isolatable testing using mock data for validation.

### 4. Development Methodologies

#### A. Test-Driven Development (TDD)
- Write tests before coding functionalities.
- Use tests as a regression suite to catch future errors.

### 5. Integration Testing

#### A. Overview
- Applications consist of multiple modules.
- **Continuous Integration (CI):** Automated integration tests triggered by commits to the main branch.
  - Tools: Jenkins, Travis CI, CircleCI.

#### B. System Level Testing
- Validate the entire system beyond integration.
- Employ black box testing to ensure it meets user requirements in a deployed environment.

### 6. Non-Functional Testing
- **Performance Testing:** Assess system behavior under load.
- **Scalability Testing:** Determine the system's ability to handle increased demand.
- **Cost Analysis:** Evaluate operational costs based on usage.

### 7. Automation in Testing

#### A. System Testing Automation
- Automate user interactions to simulate real-world usage.
- Tools:
  - **Browser Automation Frameworks:** Selenium, Cypress, TestCafe.
- Ensure tests include databases and persistent connections.

### 8. User Acceptance Testing (UAT)
- Conduct post-deployment with a limited user group (pilot).
- **Beta Testing:** Release pre-production software for feedback and bug identification.

---

## Relevant Resources

### Books
- "Software Requirements" by Karl Wiegers and Joy Beatty.
- "Clean Code: A Handbook of Agile Software Craftsmanship" by Robert C. Martin.

### Web Resources
- [IEEE Standards for Software Requirements Specifications](https://www.ieee802.org/1/files/public/docs2019/802-1-cc-requirements-specifications.pdf)
- [Atlassian: Understanding User Stories](https://www.atlassian.com/agile/user-stories)

### Tools
- **Unit Testing Frameworks:** JUnit (Java), NUnit (.NET), PyTest (Python).
- **CI Tools:** Jenkins, Travis CI, GitHub Actions.
- **Automation Frameworks:** Selenium, Cypress, TestCafe.

### Online Courses
- Coursera: Software Testing and Automation.
- Udacity: Agile Software Development.

---
