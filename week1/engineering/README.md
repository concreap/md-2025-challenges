# The E-commerce Checkout System Challenge

This one-week challenge is designed to help you deepen your understanding of how different components of a software system work together. You'll analyze an existing system, propose an architectural breakdown, and implement a small part of it. The skills you'll build are critical for moving into more senior roles.

---

## 📝 Challenge Details

### **Title: The E-commerce Checkout System**

### **Description**
You are a software engineer at a growing e-commerce company. The current monolith application is struggling with scalability and is becoming difficult to maintain. Your task is to propose a new, more robust architecture for the checkout system. This involves breaking down the functionality into smaller, manageable services and implementing a proof of concept for one of those services.

### **Instructions**
1.  **System Analysis**: Begin by mapping out the current, monolithic e-commerce checkout process. Identify key functions such as user authentication, cart management, payment processing, and order confirmation.
2.  **Architectural Proposal**: Propose a **microservices-based architecture** for the checkout system. Decide which functionalities should be their own services. For each service, provide a brief description of its purpose and the data it will handle. 

[Image of a microservices architecture diagram](https://storage.googleapis.com/pacitude-buckets/licensed-image.jpeg)

3.  **Backend Implementation**: Using **Node.js**, implement a simple API for one of the services you proposed. For this challenge, you will build the **`cart-service`**. This service should expose two major functionalities. The authentication functionalities and two cart endpoints. For example:
    * `POST /add-to-cart`: Adds an item to a user's cart.
    * `GET /get-cart/:userId`: Retrieves all items in a user's cart.
    * *Note: Use mongoDB database to simulate data persistence.*
4.  **Frontend Implementation**: Using **React-Vite** or **Next.js**, build a simple user interface that consumes the `cart-service` backend. The frontend should display a list of products and have a button to add an item to the cart. It should also have a view that displays the current items in the user's cart.
5.  **Documentation**: Create a comprehensive `README.md` file in your GitHub repository. This file should contain a diagram of your proposed architecture and clear instructions on how to run your backend and frontend code locally.

---

### **✅ Expected Deliverables**

* **Backend Repository (Node.js)**: A public GitHub repository containing the `cart-service` API.
* **Frontend Repository (React-Vite/Next.js)**: A public GitHub repository with the UI that interacts with your backend.
* **`README.md` File**: A single, well-documented `README.md` file in the main backend repository that includes:
    * A high-level architectural diagram of your proposed microservices.
    * Instructions to set up and run the backend and frontend services.
    * Explanation of the API endpoints.

---

### **📚 Relevant Links**

* **PDF**: "Microservices Architecture" by Martin Fowler. This classic article provides a great introduction to the concepts. [https://martinfowler.com/articles/microservices.html](https://martinfowler.com/articles/microservices.html)
* **Video**: "Introduction to Microservices" on YouTube. This video gives a visual and accessible overview of why and how microservices are used. [https://youtube.com/playlist?list=PLaLqLOj2bk9ZV2RhqXzABUP5QSg42uJEs&si=lF3a_5olvX_IsuNA](https://youtube.com/playlist?list=PLaLqLOj2bk9ZV2RhqXzABUP5QSg42uJEs&si=lF3a_5olvX_IsuNA)

---

### **📬 Submission Guidelines**

1.  Commit your completed backend and frontend code to separate GitHub repositories.
2.  Ensure your `README.md` file is clear and concise.
3.  Invite `@braveredemptive` to your backend and frontend repositories. The link to your frontend repository should be included in the backend's `README.md`.
4.  Submissions are due by the end of the week. Late submissions will not be reviewed.