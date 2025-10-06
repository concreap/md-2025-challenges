# 🔒 SE Challenge Week 3: Secure Multi-Role API Development

### **Title:** **Building a Secure, Token-Based Node.js API with Role-Based Access Control (RBAC)**

### **Description**

You are tasked with building a minimalist **Task Management Platform API and client** that supports two distinct user roles: **'Basic User'** and **'Admin'**. The core of this challenge is not just to make the application *work*, but to make it *secure* and resilient against common web attacks.

You must implement a robust **JSON Web Token (JWT) authentication and authorization** system using Node.js and demonstrate secure practices to mitigate critical vulnerabilities, specifically focusing on **Broken Access Control** (OWASP A01:2021) and **Injection** (OWASP A03:2021).

### **Technology Stack Requirements**

| Component | Required Technology |
| :--- | :--- |
| **Backend** | **Node.js** (using Express, **not** NestJS) |
| **Frontend** | **React-Vite** or **Next.js** |
| **Data Storage** | Light database (e.g., MongoDB or PostgresSQL for user data) |

### **Instructions**

#### **1. Backend Implementation (Node.js/Express)**

* Implement **User Registration** and **Login** endpoints. **Passwords must be hashed** (e.g., using `bcrypt` or similar).
* Implement **JWT Generation** on successful login, issuing a short-lived **Access Token** (for protected routes) and a longer-lived **Refresh Token** (for renewing the Access Token).
* Create a **Token Refresh** endpoint that securely validates the Refresh Token and issues a new Access Token without requiring re-login.
* Add a security layer for login such that, if a user supplies wrong password three times, their account gets locked for 30 minutes and it is automatically unlocked after 30 minutes.
* Implement a system to store user data, including their assigned **role** (`user` or `admin`). Ensure you have a mechanism (e.g., a simple blacklist/database record) to **revoke/blacklist refresh tokens** upon user-initiated logout.
* Implement **Role-Based Access Control (RBAC)** middleware to protect the following API routes:
    * `GET /api/tasks` (Accessible by: **User** and **Admin**)
    * `POST /api/tasks` (Accessible by: **User** and **Admin**)
    * `DELETE /api/tasks/:id` (Accessible by: **Admin ONLY**)
* Implement **Input Validation** and **Data Sanitization** on the registration and task creation endpoints to prevent **Injection** attacks ( Make sure you write your validations yourself, no libraries! ).
* Utilize security middleware (e.g., **Helmet**) to set secure HTTP headers (like CSP, XSS protection, etc.) to enhance defense.
* Implement robust search and filter endpoints for tasks, with proper paginated responses:
    * `POST /api/tasks/search` (Accessible by: **User** and **Admin**)
    * `POST /api/tasks/filter` (Accessible by: **User** and **Admin**)
* NB: Search and Filter for User only returns information from tasks on their account.

#### **2. Frontend Implementation (React-Vite/Next.js)**

* Develop a basic client application with **Registration and Login** interfaces.
* Implement a secure client-side strategy for handling JWTs. **Crucially, the short-lived Access Token must NOT be stored in standard, client-side browser \`localStorage\`** due to XSS risks. Explain your chosen secure storage method (e.g., HttpOnly cookies managed by the backend, or storing the token in client-side memory) in your `README.md`.
* Build a simple UI to display the task list, allowing all logged-in users to create tasks.
* Ensure that the **Task Delete** button is only functional and visible to users with the **Admin** role, and that the backend properly rejects unauthorized \`DELETE\` requests from 'Basic User' accounts (even if a user attempts to manually trigger the request).

### **Expected Deliverables**

1.  A fully functional **Node.js API** repository on GitHub.
2.  A fully functional **React-Vite/Next.js Frontend** repository on GitHub (can be a separate repo or a mono-repo structure).
3.  A detailed **`README.md`** file in the API repository that includes:
    * Setup and running instructions for both the backend and frontend.
    * A technical explanation of the **JWT flow**, token rotation strategy, and secure token storage method used.
    * A dedicated section detailing how you mitigated **Broken Access Control (A01)** and **Injection (A03)** vulnerabilities.

### **Relevant Learning Resources**

| Resource Type | Title/Topic | Link |
| :--- | :--- | :--- |
| **PDF Article** | **Empowering Robust Security Measures in Node.js-Based REST APIs by JWT Tokens and Password Hashing** (Covers JWT, Hashing, and common API vulnerabilities like SQL Injection and XSS). | [https://www.researchgate.net/publication/392069696\_Empowering\_Robust\_Security\_Measures\_in\_Nodejs-Based\_REST\_APIs\_by\_JWT\_Tokens\_and\_Password\_Hashing\_Safeguarding\_Cyber\_World](https://www.researchgate.net/publication/392069696_Empowering_Robust_Security_Measures_in_Nodejs-Based\_REST\_APIs\_by\_JWT\_Tokens\_and\_Password\_Hashing\_Safeguarding\_Cyber\_World) |
| **Video Tutorial** | **OWASP Top 10 Vulnerabilities Explained for Developers** (Focus on A01, A03, and A07) | [https://www.youtube.com/watch?v=9HtxKEz59Gk](https://www.youtube.com/watch?v=9HtxKEz59Gk) |

### **Submission Guidelines**

1.  Create **GitHub repositories** for backend and frontend containing all your code for each.
2. Ensure your final, unoptimized code, optimized Node.js code and the corresponding client are committed to the main branches of the backend & frontend repositories.
3. The root of your repository must contain the completed README.md file detailing your performance report (as specified in Expected Deliverables).
4. Ensure your submission entry is logged into this [Google Doc](https://docs.google.com/document/d/1ifYuyImVk_ckOOLXZ68TOS3UfAxJ1rzpu_7hdATbtzY/edit?usp=sharing) provided for submission.
5.  Ensure your **`README.md`** is complete and detailed as specified in the deliverables section.
6. Deadline for submission is Friday, 11:59 PM
7. Submissions are due by the end of the week. Late submissions will not be reviewed.

---

## **Challenge Rubrics (Total 100 Points)**

Submissions will be scored based on the following competencies:

| Skill/Competence Focus | Description | Max Points |
| :--- | :--- | :--- |
| **Core Functionality & Completeness** | All required routes (Register, Login, Refresh, Task CRUD) are implemented, functional, and correctly integrated between the client and API. | 20 |
| **Secure Token Implementation (A07)** | Correct use of **JWTs (Access/Refresh)**, proper handling of token expiration, and secure storage (explicitly avoiding vulnerable \`localStorage\`). | 25 |
| **Role-Based Access Control (A01)** | The **Admin-only** restriction on the \`DELETE\` task route is strictly enforced by the backend middleware, demonstrating robust **Broken Access Control** mitigation. | 20 |
| **Vulnerability Mitigation (A03)** | Effective **input validation and sanitization** are implemented on user inputs (e.g., preventing XSS/Injection in usernames or task content). | 15 |
| **Code Quality & Best Practices** | Clean, well-structured Node.js/React code; consistent use of modern asynchronous patterns (\`async\`/\`await\`); appropriate use of environment variables for secrets. | 10 |
| **Documentation (README.md)** | Clear, concise explanation of the Auth Flow, security choices, and a dedicated section detailing the mitigation strategy for the specified OWASP Top 10 risks. | 10 |
```eof

I've ensured the content is copy-paste ready for a Markdown file.

What topic would you like to plan the challenge for next? We still need to cover **AI/ML Engineering** and **Product Design**.