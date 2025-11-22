# Processing Parallel or Sequential Workflows (IBM FileNet P8)

Workflows in FileNet P8 can be designed to run **sequentially** (one step after another) or **in parallel** (multiple steps at the same time). The choice depends on business requirements such as efficiency, dependencies, and review processes.

---

## 🔹 Sequential Workflows
- **Definition**: Tasks are executed one at a time, in a defined order.  
- **Behavior**: Each step must complete before the next begins.  
- **Example**: A document goes through review → approval → archiving.  
- **Advantages**:
  - Simple to design and debug  
  - Easier to track progress and dependencies  
- **Limitations**:
  - Slower execution overall  
  - Bottlenecks if one step takes too long  

---

## 🔹 Parallel Workflows
- **Definition**: Multiple tasks are executed simultaneously.  
- **Behavior**: A **Split node** initiates concurrent branches; a **Join node** synchronizes them later.  
- **Example**: A document is sent to multiple reviewers at the same time; once all reviews are complete, it proceeds to approval.  
- **Advantages**:
  - Faster execution  
  - Better resource utilization  
- **Limitations**:
  - More complex to manage  
  - Requires careful synchronization to avoid race conditions  

---

## ⚙️ Workflow Constructs in FileNet

### Split Node
- Divides a single process path into multiple branches  
- Enables parallel or conditional execution of tasks  

### Join Node
- Synchronizes multiple branches back into a single path  
- Ensures workflow proceeds only when required branches are complete  

---

## 🏆 Best Practices
- Use **AND Split/Join** for tasks that must run and complete in parallel  
- Use **XOR Split/Join** for mutually exclusive paths  
- Always pair Split with a corresponding Join to avoid workflow deadlocks  
- Clearly define conditions for OR/XOR logic to prevent ambiguity  

---

## 📂 Real-World Example: Bank Policy Review
- **Sequential**: CEO reviews → Legal team reviews → Compliance team reviews  
- **Parallel**: CEO, Legal, and Compliance teams review simultaneously → Join node waits for all to finish → Final approval  

---

## 🔧 Merge Types in FileNet Workflows
When branches modify the same data field, merge types control how the final value is determined:

1. **Default**  
   - No change to the data field  
   - Field retains value from the split point  

2. **Override**  
   - Value from the last completed branch overrides previous values  
   - Useful when the most recent input is authoritative  

3. **Add**  
   - Values from all branches are aggregated  
   - Strings → concatenated; Numbers → summed  
   - Useful for collecting inputs from multiple sources  

---

## 📖 Reference
- [IBM Documentation: Processing parallel or sequential workflows (FileNet P8)]
- (https://www.ibm.com/docs/en/content-navigator/3.1.0?topic=navigator-processing-parallel-sequential-workflows-filenet-p8)
