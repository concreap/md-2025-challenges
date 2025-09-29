# 💻 SE Challenge Week 2: The Latency Detective
## Title: Profiling and Performance Optimization (Node.js)

### Description
This challenge is designed with the aim of helping Engineers **master performance diagnostics and optimization in a high-concurrency Node.js** environment.

Node.js is single-threaded, meaning CPU-intensive, synchronous operations can **block the Event Loop**, leading to increased latency and poor application responsiveness under load. Your focus is to profile a deliberately unoptimized Express API, identify the blocking function, and refactor the system using **Worker Threads** to offload the heavy work and restore high throughput.

### Instructions

#### 🎯 Phase 1: Setup and Baseline Benchmarking

1.  **Project Setup:** Create a new project structure with a **Node.js/Express** backend and a simple **Frontend** (using React-Vite or Next.js) client.
2.  **Create Bottleneck Endpoint:** In your Node.js server, implement an endpoint (`POST /api/process-data`) that performs an artificial, synchronous, and CPU-intensive calculation (e.g., a massive JSON data parse followed by a long-running complex mathematical loop, such as a deep Fibonacci sequence calculation).
3.  **Load Test Simulation:** Use your simple Frontend client (or a tool like `autocannon` if you prefer CLI) to send **100 concurrent requests** to the unoptimized `POST /api/process-data` endpoint.
4.  **Profile the Baseline:** Use the built-in Node.js profiler (`node --inspect app.ts` + Chrome DevTools Performance Panel) or command-line profiling (`node --prof`) to capture the CPU profile during the load test. **Record the average request latency** and identify the function that consumed the most time on the Main Thread.

#### ⚙️ Phase 2: Optimization with Worker Threads

1.  **Introduce Worker Threads:** Refactor the blocking, CPU-intensive logic into a dedicated **Node.js Worker Thread** file (e.g., `worker.ts`).
2.  **Decouple:** Update the `POST /api/process-data` endpoint logic to use the `Worker` class. The main Express route should now simply:
    * Receive the request.
    * Spawn the worker and pass the necessary data.
    * Wait for the worker's result using a Promise/Async-Await pattern.
    * Send the final response.
3.  **Confirm Decoupling:** Verify that the main thread is now primarily free to handle I/O, demonstrating that the heavy calculation is running in the background thread.

#### ✅ Phase 3: Validation and Reporting

1.  **Validate Performance:** Repeat the load test (100 concurrent requests) against the newly optimized endpoint.
2.  **Generate Final Profile:** Capture a new CPU profile of the optimized server.
3.  **Prepare the Report:** Document your findings in the **Expected Deliverables** section below.

### Expected Deliverables

Your final `README.md` must serve as a professional performance report covering the following points:

1.  **Baseline Analysis (Unoptimized):**
    * The **initial average request latency** (e.g., "3.5 seconds").
    * A screenshot or detailed summary of the **CPU profile/Flame Graph** for the unoptimized code, clearly highlighting the function that blocked the Event Loop and consumed the most CPU time.
2.  **Optimization Strategy:**
    * A concise explanation of *why* the Event Loop was blocked.
    * Justification for choosing **Worker Threads** as the solution over other techniques (e.g., clustering).
    * A brief overview of the communication strategy between the main thread and the worker thread.
3.  **Validation Results (Optimized):**
    * The **final average request latency** (e.g., "50 milliseconds").
    * A screenshot or summary of the new CPU profile, showing the significant reduction in time spent on the Main Thread for the heavy calculation.
    * A calculation of the percentage improvement in latency (e.g., "Latency improved by 98%").

### Relevant Learning Resources

| Type | Title | Link | Focus |
| :--- | :--- | :--- | :--- |
| **PDF** | Optimizing Node.Js Performance for Production: Memory Management, Clustering, and Monitoring | https://ijirt.org/publishedpaper/IJIRT182978_PAPER.pdf | Deep dive into Event Loop dynamics and how clustering/threading addresses blocking I/O. |
| **Video** | Node.js Performance Optimization: Boost Your App's Speed & Efficiency! | https://www.youtube.com/watch?v=c4twikSs2Ws | Practical tips and best practices for avoiding Event Loop blocks and improving overall throughput. |
| **Docs** | Node.js Worker Threads Documentation | https://nodejs.org/api/worker_threads.html | Official guide on implementing and communicating with dedicated worker threads. |
| **Tooling** | Profile Node.js performance with the Performance panel | https://youtu.be/Dr7kzOAO1U8?si=U4FMwrWANeAxbFwe | Guide on setting up DevTools for remote profiling of your Node.js backend. |

### Submission Guidelines

1.  Create **private GitHub repositories** for your projects.
2.  Ensure your final, unoptimized code, optimized Node.js code and the corresponding client are committed to the main branches of the backend & frontend repositories.
3.  The root of your repository **must** contain the completed `README.md` file detailing your performance report (as specified in **Expected Deliverables**).
4.  Ensure your submission entry is logged into this [Google Doc](https://docs.google.com/document/d/1ifYuyImVk_ckOOLXZ68TOS3UfAxJ1rzpu_7hdATbtzY/edit?usp=sharing) provided for submission.
5.  Deadline for submission is Friday, 11:59 PM
6.  Submissions are due by the end of the week. Late submissions will not be reviewed.