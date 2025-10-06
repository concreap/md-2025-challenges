# Design Challenge Week 3: Establishing a Scalable Design System for Enterprise Data

### **Challenge Title: Scaling Complexity: Designing Patterns and States for a High-Volume Data Manager**

### **Description**

Your organization is launching a new Enterprise Asset Management platform. The product currently uses ad-hoc UI components, leading to inconsistency, slow development, and poor user experience when dealing with large datasets ($10,000+$ records).

Your mission is to establish the core components of a scalable design system and apply those patterns to redesign a complex, high-volume interaction flow: **The Data Table and Advanced Filtering System.**

The focus is not just aesthetics, but **reusability, clarity of state, and flow efficiency** when interacting with vast amounts of information.

### **Technology/Output Requirements**

| Component | Required Output/Format |
| :--- | :--- |
| **Design Tool** | **Figma, Sketch, or Adobe XD** (Link must be public) |
| **Output** | High-fidelity mockups and components documentation. |
| **Documentation** | Design Rationale (PDF or dedicated Figma page) focusing on scalability decisions. |

### **Instructions**

#### **1. Design System Foundation (Patterns for Scale)**

Establish the following foundational elements, ensuring they are documented as reusable components:

* **Colors:** Define a primary, secondary, and a full set of semantic colors (Success, Warning, Error, Information).
* **Spacing:** Define a $4$-point or $8$-point spacing scale and demonstrate its application on a simple card component.
* **Components:** Create and document the component states for a **Button** (Default, Hover, Disabled, Loading) and a **Text Input Field** (Default, Focused, Error, Disabled).

#### **2. Redesign: The Core Data Table Component (States)**

Design the main Data Table component, focusing on communicating the $6$ essential states for a data-driven application:

1.  **Default/Success State:** A typical view with $5$ columns and up to $10$ rows of data.
2.  **Loading State:** The pattern used while the data is being fetched (e.g., skeleton loaders).
3.  **Empty State:** The view when the table has no data (on initial setup). Must include an action to onboard new data.
4.  **Error State:** The view when the data fetch fails (must include clear, actionable copy).
5.  **Filtered/No Results State:** The view when filters are applied but yield zero results (must provide clear path to modify or reset filters).
6.  **Selected/Active State:** Design the pattern for bulk selection, including a persistent header bar for displaying the number of selected items and available bulk actions (e.g., Delete, Export).

#### **3. Redesign: The Advanced Filtering Flow (Flows)**

Design the interaction flow for an **Advanced Filtering** feature connected to the Data Table. This flow must handle multiple criteria without overwhelming the user.

* Design the entry point (e.g., a "Filter" button).
* Design the filter modal/panel where users can apply $3$ different criteria (e.g., Status, Date Range, Value greater than X).
* Design how the active filters are clearly displayed on the main Data Table screen after the user closes the modal/panel.

### **Expected Deliverables**

1.  A public link to the **Design File** containing:
    * The documented Design System foundation (Colors, Spacing, Button, Input).
    * The $6$ required states of the Data Table component.
    * The Advanced Filtering flow screens.
2.  A concise **Design Rationale** document/page answering:
    * How your design choices for the Data Table states address user anxiety and ambiguity.
    * How the component hierarchy ensures reusability across future, unforeseen features.

### **Submission Guidelines**

1.  Ensure your Figma link is logged into this [Google Doc](https://docs.google.com/document/d/1epdj4Ese9ujA8FqKzSlxhlwJuaRlMbyD_IZenRRedCM/edit?usp=sharing) provided for submission.
2.  Make sure you fill in the information on the google doc correctly.
3.  Double submission automatically disqualifies your submission. Ensure you submit in the correct week based on the tab in the document
4.  Deadline for submission is Friday, 11:59 PM
5.  Submissions are due by the end of the week. Late submissions will not be reviewed.

---

## **Challenge Rubrics (Total 100 Points)**

Submissions will be scored based on the following competencies:

| Skill/Competence Focus | Description | Max Points |
| :--- | :--- | :--- |
| **Component Scalability (Patterns)** | Clarity and definition of the foundational design system elements (Colors, Spacing, reusable components) that ensure consistency across hundreds of screens. | 25 |
| **State Communication** | Effective and clear design of all $6$ required Data Table states. The user understands what is happening (loading, error, empty) immediately without confusion. | 35 |
| **Flow Efficiency (Complexity Management)** | The Advanced Filtering flow is intuitive, minimizes cognitive load, and clearly communicates the results and current active criteria to the user. | 25 |
| **Design Execution & Documentation** | Quality of high-fidelity visual design, adherence to component-based thinking, and clear rationale for scalability choices. | 15 |
```eof