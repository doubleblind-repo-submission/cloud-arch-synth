## Flow Diagram

- **Flow diagram:** In the space provided, draw the service flow by connecting the nodes of your assigned architecture with arrows.
- **Written justification:** Answer the questions in the spaces provided.

---

## Guiding Questions

### Question 1. Services added and/or removed (max. 3 changes)

- Write down the changes you made to the services (you may add or remove services; maximum of 3 changes).
- Justify each change: does it improve performance, reduce latency, or simplify the design?
- **Examples:**
  - Added: “We added *FSx for Lustre* because we need shared storage across multiple HPC nodes.”
  - Removed: “We removed *CloudFront* because we do not need content distribution to external users.”

---

### Question 2. Design assumptions

- Every design relies on assumptions. State the assumptions you are considering.
- Consider, for example:
  - Which tasks are processed at the **Edge** and which at **HPC**?
  - How does data move: in real time (**stream**) or in batches (**batch**)?
  - Where is data stored: cache, distributed storage, or a database?
- **Example:** “We assume sensors continuously send data to the *Edge (Greengrass)*, which filters events, and only relevant data is sent in batches to the *Batch* cluster.”

---

### Question 3. Proposed validations and metrics

Explain how you would verify that your architecture works correctly. Break your proposal down into at least two of the following aspects:

1. **Latency:** How fast does data travel from the Edge to the HPC layer?  
   Example: “The time between the sensor and the cluster response should not exceed 150 ms.”

2. **Throughput:** How many events or batches can the system process within a given time interval?  
   Example: “The system should process at least 10,000 events per minute without accumulating delays.”

3. **Scalability:** What happens if you double the number of Edge devices or HPC nodes?  
   Example: “If devices increase from 50 to 100, the architecture should maintain at least 80% of the original performance.”

4. **Fault tolerance:** What happens if a service or node fails?  
   Example: “If an HPC node fails, Batch should reassign the task to another node without losing the work.”
