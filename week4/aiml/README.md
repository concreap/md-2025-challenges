# AI/ML Engineering Week 4 Challenge

### **Title:** SmartHire - Intelligent Resume Screening and Candidate Scoring System

---

### **Description:**

You’re working with **SmartHire**, a growing HR-tech startup focused on automating recruitment using data-driven intelligence. You’ve been tasked with building an **end-to-end AI-powered system** that helps recruiters screen resumes, extract candidate details, and assign scores based on skill-job match.

Your goal is to develop a **machine learning pipeline** that processes resumes (PDF or text), extracts key attributes (skills, experience, education), and predicts a suitability score for given job descriptions. The system should have both **a backend service (Python)** for processing and model inference, and a **frontend interface (React + Vite or Next.js)** for recruiters to upload resumes and view results.

---

### **Instructions:**

#### **Backend (Python + FastAPI or Flask)**

1. Build a REST API that exposes endpoints for:

   * Uploading resumes (PDF/Text).
   * Uploading job descriptions.
   * Returning extracted details and predicted suitability scores.
2. Implement a preprocessing pipeline for:

   * Text extraction (using libraries like `PyMuPDF`, `pdfminer`, or `textract`).
   * NLP-based skill and entity extraction (using `spaCy` or `transformers`).
3. Train a simple ML model (e.g., logistic regression, random forest, or BERT fine-tuning) for candidate-job score prediction.
4. Store processed results in a lightweight database (SQLite or PostgreSQL).
5. Document your API endpoints clearly using **README.md** or **Postman API documentation**.

#### **Frontend (React + Vite or Next.js)**

1. Create a recruiter dashboard that allows users to:

   * Upload resumes and job descriptions.
   * View extracted information (skills, experience, etc.).
   * Display predicted scores in a clean, intuitive UI.
2. Integrate your API endpoints to handle file uploads and display model predictions.
3. Use **TailwindCSS** for UI styling.

#### **Deployment**

1. Deploy your backend service on **Render**, **Railway**, or **Vercel**.
2. Deploy your frontend on **Vercel** or **Netlify**.
3. Ensure CORS is properly configured for communication between frontend and backend.

#### **Documentation**

* Include a well-documented `README.md` describing your architecture, setup, API routes, and model training approach.
* You may include a short Loom or YouTube video walkthrough (optional).

---

### **Expected Deliverables:**

* Two **separate GitHub repositories**:

  * One for **Backend (Python + FastAPI/Flask)**.
  * One for **Frontend (React + Vite or Next.js)**.
* Each repository must include:

  * A `README.md` file with setup, installation, and deployment instructions.
  * Backend repo should include **Postman API documentation** or detailed endpoint documentation in the README.
  * Trained model file(s) and preprocessing scripts.
  * A deployed live URL for both frontend and backend.
  * Unit test scripts or notebooks demonstrating model verification.
* All repositories **must be private**, and participants should invite **@braveredemptive** for review access.

---

### **Learning Resources:**

* 📘 **PDF Resource:** [Practical Guide to NLP in Python](https://arxiv.org/pdf/2107.07234.pdf)
* 🎥 **Video Resource:** [End-to-End NLP Project Tutorial with Python](https://www.youtube.com/watch?v=8rjRfW4JM2I)

---

### **Submission Guidelines:**

* Push your project to **two private GitHub repositories** (one for backend, one for frontend).
* Invite **@braveredemptive** to both repositories for review access.
* Ensure both applications are deployed and accessible online.
* Log your submission entry in this **[Google Submission Sheet](https://docs.google.com/spreadsheets/d/131My2Yo2ekHu9KR9v0-NOfFENDiNm8rT0UEXBhUrkbc/edit?usp=drivesdk)**.
* Include your repository links, deployed URLs, and API documentation links.
* **Deadline for submission is Friday, 11:59 PM.**
* **Submissions are due by the end of the week. Late submissions will not be reviewed.**

---

### **Challenge Duration:**

⏰ One week (7 days)

This challenge simulates a real-world AI/ML engineering task, combining **machine learning model building, API design, and frontend integration** — ideal for participants with **1–2 years of experience** looking to strengthen their full-stack ML system development skills.
