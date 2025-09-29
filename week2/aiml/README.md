# 🤖 AI/ML Engineering Challenge Week 2: The Training Throughput Bottleneck
## Title: The Training Throughput Bottleneck: Optimizing the Data Loading Pipeline

### Description
This challenge is designed with the aim of mastering performance diagnostics in Python-based training pipelines. In machine learning, training time is often limited not by the GPU's speed, but by the CPU's inability to feed data fast enough, resulting in **GPU underutilization**.

Your focus is to profile a deliberately unoptimized training loop (using **Python** and a framework like **PyTorch** or **TensorFlow**), identify the data loading bottlenecks (e.g., I/O, slow transformations, or sub-optimal worker settings), and implement concrete optimization strategies to maximize the GPU's utilization and dramatically reduce the overall epoch training time.

### Instructions

#### 🎯 Phase 1: Setup and Baseline Benchmarking

1.  **Project Setup:** Create a new project environment (Python/Anaconda) using a standard deep learning framework (PyTorch is recommended for its detailed profiler).
2.  **Create Bottleneck:** Implement a simple model training loop with a custom `DataLoader` that includes an artificial bottleneck, such as:
    * Reading images/data from disk **synchronously** within the `__getitem__` method.
    * Applying a **CPU-intensive, synchronous transformation** (e.g., a complex image filter or large-scale data augmentation) on the main thread.
3.  **Baseline Training:** Train the model for 5 epochs on a sizable dataset. **Record the average epoch time** and the reported **GPU utilization percentage**.
4.  **Profile the Baseline:** Use the framework's integrated profiler (**PyTorch Profiler** or **TensorFlow Profiler**) to capture a timeline trace. Identify the functions that consume the most **CPU time** or cause the largest **stalls/gaps** in the GPU timeline.

#### ⚙️ Phase 2: Optimization with Pipeline Parallelism

1.  **Improve Data I/O:** Implement non-blocking techniques to offload the data loading/preprocessing from the main thread. This will typically involve increasing the `num_workers` in the DataLoader and ensuring memory pinning (`pin_memory=True`).
2.  **Optimize Transformations:** Refactor any heavy CPU-bound operations (e.g., complex image processing) to run efficiently within the workers or, if possible, move them to the GPU (e.g., using frameworks like **TorchVision's TrivialAugment** or other accelerated libraries).
3.  **Confirm Decoupling:** Rerun the profiling tool to verify that the CPU-related operations are now well-parallelized and no longer causing significant waits on the GPU timeline.

#### ✅ Phase 3: Validation and Reporting

1.  **Validate Performance:** Repeat the 5-epoch training run against the optimized pipeline.
2.  **Generate Final Profile:** Capture a new profiler trace of the optimized training.
3.  **Prepare the Report:** Document your findings in the **Expected Deliverables** section below.

### Expected Deliverables

The output should be a single, well-structured document (Google Doc) containing the following sections and supporting media:

1.  **Problem & Goal Summary:** A brief (1-paragraph) statement summarizing the problem (low GPU utilization/high epoch time) and the engineering goal (achieving $>90\%$ GPU utilization).
2.  **Baseline Analysis (Unoptimized):**
    * The **initial average epoch training time** and **GPU utilization** (e.g., "75 seconds / 45%").
    * A screenshot or detailed summary of the **Profiler Trace Timeline**, clearly highlighting the **Stalls** or **Input Pipeline Delays** (the bottleneck).
3.  **Optimization Strategy:**
    * A concise explanation of *why* the data pipeline was the bottleneck (the CPU/GPU synchronization issue).
    * Justification for the chosen optimization techniques (e.g., increasing `num_workers`, using `pin_memory`, or moving transformations).
4.  **Validation Results (Optimized):**
    * The **final average epoch training time** and **GPU utilization** (e.g., "30 seconds / 92%").
    * A screenshot or summary of the new **Profiler Trace Timeline**, showing minimal gaps/stalls.
    * A calculation of the percentage reduction in epoch time (e.g., "Time reduced by $60\%$").

### Relevant Learning Resources

| Type | Title | Link | Focus |
| :--- | :--- | :--- | :--- |
| **PDF** | High Performance Python | https://dl.hellodigi.ir/dl.hellodigi.ir/dl/book/High%20Performance%20Python.pdf | Deep dive into general Python profiling (`cProfile`, `line_profiler`) and optimizing data structures for speed. |
| **Video** | How to Make Machine Learning Models Run Faster in Production | https://www.youtube.com/watch?v=7-f0C1qPgtI | Practical techniques for decreasing machine learning inference times and improving model throughput in a production environment. |
| **Docs** | PyTorch Profiler Documentation | https://docs.pytorch.org/docs/stable/profiler.html | Official guide on using the `torch.profiler` for detailed timeline traces and identifying operator execution times. |
| **Tooling** | NVIDIA System Management Interface (`nvidia-smi`) | https://youtu.be/DHRLd9xDAbI?si=hiaEX9XdysjZU13M | Command-line tool used to monitor GPU utilization and memory usage during training. |

### Submission Guidelines

1.  Create a **Google Document** containing all the **Expected Deliverables**, including embedded images/screenshots of your profiling reports and the resulting metrics.
2.  Create **private GitHub repositories** for your project and push your code.
3.  Ensure the document created above is set to "Anyone with the link can view."
4.  Ensure your submission entry is logged into this [Google Doc](https://docs.google.com/document/d 1Qm6oUOWyIRMX6ePicNEUmzdco0OQ3kXTQ4rigwcLAdc/edit?usp=sharing) provided for submission.
5.  Deadline for submission is Friday, 11:59 PM
6.  Submissions are due by the end of the week. Late submissions will not be reviewed.