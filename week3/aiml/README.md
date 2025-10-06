# 🔒 AI/ML Challenge Week 3: Secure Multi-Tenant ML Inference API

### **Title: Securing a Multi-Tenant Inference Endpoint with JWT and Anti-DoS Measures**

### **Description**

You are tasked with building the secure serving layer for a **Multi-Tenant Classification Service**. This platform allows different users (tenants) to deploy and query their private machine learning models via a central API.

The core challenge is to ensure that the inference endpoint is not only secured by standard authentication but is also protected against two critical threats specific to ML deployments:

1.  **Insecure Direct Object Reference (IDOR) / Unauthorized Access:** Preventing one tenant from querying another tenant's proprietary model.
2.  **Model Denial of Service (DoS):** Protecting the serving infrastructure from resource exhaustion by inputs that are maliciously oversized or incorrectly shaped.

You must build the API layer and implement the necessary security middleware in Python.

### **Technology Stack Requirements**

| Component | Required Technology |
| :--- | :--- |
| **API Framework** | **Python** (FastAPI or Flask) |
| **Authentication** | **PyJWT** (or equivalent library for JWT creation/validation) |
| **Model Simulation** | A simple **Scikit-learn** model (e.g., Logistic Regression or Decision Tree) saved as a \`.pkl\` file to simulate the resource to be protected. |
| **Data Storage** | A simple in-memory dictionary or JSON file to map **User IDs** to **Model File Paths**. |

### **Instructions**

#### **1. Setup and Model Simulation**

* **Setup:** Create a Python virtual environment and choose either FastAPI or Flask.
* **Model:** Train a trivial scikit-learn model (e.g., classifying a simple dataset like Iris) and save it to two separate files: \`model_user_a.pkl\` and \`model_user_b.pkl\`.
* **Tenant Mapping:** Create a structure (e.g., a Python dictionary) that maps a simulated \`user_id\` to their respective model file path and expected input shape.
    * Example: \`{"alice_id": {"model_path": "model_user_a.pkl", "expected_shape": [1, 4]}}\`

#### **2. Authentication and Authorization (Auth Flow)**

* **JWT Generation:** Create a mock login function that, given a user credential (e.g., a hardcoded username/password), returns a JWT token. This token **must** contain the unique \`user_id\` in its payload.
* **Authentication Middleware:** Implement a middleware function that intercepts every inference request, extracts the JWT, validates its signature and expiry, and extracts the \`user_id\`.

#### **3. Vulnerability Mitigation**

* **A. Prevent IDOR/Unauthorized Access:**
    * The inference endpoint should be defined as: \`/api/v1/predict\` (or similar).
    * In the handler, use the authenticated \`user_id\` (from the JWT) to look up the path to the **user's specific model file**.
    * **Crucially**, the request payload **must not** contain a model ID or path; the model is implicitly chosen based on the authenticated user, thus mitigating IDOR/unauthorized access to other models.
    * If the \`user_id\` is invalid or not mapped to a model, return a $403$ or $404$ error.

* **B. Mitigate Model Denial of Service (ML04: DoS):**
    * Implement **strict input shape and size validation** *before* passing data to the loaded ML model.
    * The request body will contain the input data (e.g., a list of features).
    * If the input data array is excessively large (e.g., $> 1000$ inference requests in one batch) or the shape does not match the model's \`expected_shape\`, reject the request immediately with a $400$ error. This prevents a malicious user from submitting massive payloads that exhaust server memory or CPU cycles.

#### **4. API Deployment**

* Define a single, secure inference endpoint that loads the correct model and performs all required security checks before running \`model.predict(data)\`.
* Ensure the API returns useful error messages for both authentication failures ($401$), authorization/IDOR attempts ($403$), and DoS-related input validation failures ($400$).

### **Expected Deliverables**

1.  A fully functional **Python API** repository (FastAPI/Flask) on GitHub.
2.  The repository must include the simulated model files (\`model_user_a.pkl\`, etc.).
3.  A detailed **\`README.md\`** file that includes:
    * Setup and running instructions.
    * A technical explanation of the **Auth Flow** (how the JWT payload is used to enforce authorization).
    * A dedicated section detailing how the implementation prevents **Model Denial of Service (ML04)** and **Unauthorized Model Access (IDOR)**.

### **Relevant Learning Resources**

| Resource Type | Title/Topic | Link |
| :--- | :--- | :--- |
| **PDF Article** | **Machine Learning Security: Getting familiar with essential cyber security concepts, input validation, and adversarial ML.** | [https://cydrill.com/wp-content/uploads/CYDMLPy.pdf](https://cydrill.com/wp-content/uploads/CYDMLPy.pdf) |
| **Video Tutorial** | **A Guide to the OWASP Top 10 for LLMs** (Focuses on Prompt Injection, Model DoS, and Sensitive Information Disclosure). | [https://www.youtube.com/watch?v=mpvfEsyl-C8](https://www.youtube.com/watch?v=mpvfEsyl-C8) |

### **Submission Guidelines**

1.  Create a **GitHub repository** containing all your code and models.
2.  Ensure your submission entry is logged into this [GoogleDoc](https://docs.google.com/document/d/1Qm6oUOWyIRMX6ePicNEUmzdco0OQ3kXTQ4rigwcLAdc/edit?usp=sharing) provided for submission.
3. Ensure your **\`README.md\`** is complete and detailed as specified in the deliverables section.
4.  Deadline for submission is Friday, 11:59 PM
5.  Submissions are due by the end of the week. Late submissions will not be reviewed.