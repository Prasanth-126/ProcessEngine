# Parameters Overview in FileNet Process Engine

In FileNet Process Engine:
- **Rosters** expose parameters that describe workflow instances (e.g., workflow class, roster name, instance count).  
- **Queues** expose parameters that describe pending work items (e.g., queue name, priority, element count).  

**Purpose**:  
- Rosters → Monitoring/reporting across workflows  
- Queues → Managing and processing tasks  

**Usage**:  
- Rosters help administrators track workflow populations  
- Queues help users and systems retrieve and process work items  

---

## 📂 Roster Parameters – Purpose & Usage
A **roster** is a database structure that contains references to all workflow instances (active and completed).

### Key Parameters
- **Roster Name** – Identifier for the roster  
- **Workflow Class Name** – Defines the type of workflows stored  
- **Instance Count** – Number of workflow instances in the roster  
- **Status Fields** – Workflow state (active, completed, suspended)  
- **Custom Data Fields** – Business-specific metadata stored with workflows  

### Purpose
- Provides a global view of workflows across queues  
- Enables searching and reporting across all workflow instances  
- Supports monitoring SLA compliance and identifying bottlenecks  

### Usage
- Administrators query workflows regardless of queue location  
- Useful for auditing, analytics, and dashboards  
- **Example**: Checking how many insurance claims are active across all queues  

---

## 📂 Queue Parameters – Purpose & Usage
A **queue** is a structure that contains work items waiting to be processed.

### Key Parameters
- **Queue Name** – Identifier for the queue  
- **Queue Type** – User queue (manual tasks) or system queue (automated tasks)  
- **Work Item Count** – Number of items currently in the queue  
- **Priority** – Determines processing order  
- **Security Settings** – Controls who can access the queue  
- **Step Element References** – Links to tasks assigned to users/systems  

### Purpose
- Organizes pending work items for efficient processing  
- Provides task-level visibility and control  
- Supports load balancing and security enforcement  

### Usage
- Users retrieve tasks from queues to work on them  
- System components poll queues for automated processing  
- **Example**: A “Claims Verification Queue” holds all pending claim verification tasks  

---

## ✅ Best Practices – Using Rosters and Queues
- Use **rosters** for monitoring and reporting, not for direct task execution  
- Use **queues** for operational task management  
- Keep queues optimized with proper priority settings to avoid bottlenecks  
- Regularly audit roster parameters to ensure workflow health  

---

# Exposed Parameters

**Definition**: Workflow data fields (from a workflow definition) made visible to the Process Engine for searching, filtering, and reporting.  
They act as metadata fields that can be indexed and queried.

### Example
- Insurance claim workflow → Claim ID, Policy Number, Claim Amount  

### Purpose
- Allow efficient querying of workflows across rosters and queues  
- Enable business-level searches (e.g., find all claims > $10,000)  
- Support reporting and monitoring  
- Provide flexibility for administrators and developers  

---

## 🔎 Exposed Parameters – Usage in PE Search

### Roster Search
- Rosters store workflow instances  
- Exposed parameters let you query workflows by business data  
- **Example**: Search roster for workflows where `CustomerID = 12345`  

### Queue Search
- Queues store pending work items (Step Elements)  
- Exposed parameters allow filtering tasks by workflow data  
- **Example**: Search queue for tasks where `Priority = High` and `Region = APAC`  

### APIs
- Developers use **VWSession, VWQueue, VWRoster** objects in Java/.NET APIs  
- Queries can include exposed parameters as filters  

**Pseudo-code Example**:
```java
VWRoster roster = session.getRoster("ClaimsRoster");
VWQuery query = roster.createQuery("ClaimAmount > 10000");
VWWorkObject[] results = query.execute();

# ✅ Best Practices for Exposing Parameters in FileNet Process Engine

## Best Practices
- Expose only **essential business fields** to avoid overhead  
- Index **frequently queried parameters** for performance  
- Use **consistent naming conventions** across workflows  
- Avoid exposing **sensitive data** unless required for compliance  
- Regularly review exposed parameters to align with **business reporting needs**  

---

## 📊 Summary
- **Business data** = workflow-specific fields (e.g., ClaimID, CustomerID)  
- Exposing business data makes it **searchable** in queues, rosters, and event logs  
- **Purpose**: reporting, monitoring, auditing, compliance  
- **Usage**: enables business users and admins to query workflows by meaningful attributes  

---

## Expose Parameters – Best Practices
- Expose only **necessary parameters** to avoid overhead  
- Index frequently queried fields for **faster searches**  
- Use **consistent naming** across workflow definitions  
- Regularly review exposed parameters to align with **reporting needs**  

### For Queues
- Expose parameters that help users **filter tasks**  

### For Rosters
- Expose parameters that help admins **monitor workflows globally**  

---

## 📌 Summary by Component
- **Queues** → Expose task-level parameters for searching pending work items  
- **Rosters** → Expose workflow-level parameters for monitoring/reporting across processes  
- **Event Logs** → Exposed parameters make them searchable and reportable (auditing, monitoring, troubleshooting, compliance)  

⚠️ Always **commit changes in PCC** after configuration  

---

## 📖 References
- [IBM Docs – Designing Workflows](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=management-designing-workflows)  
- [IBM Docs – Queue, Roster, Event Log Properties](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=console-queue-roster-event-log-properties)  
- [IBM Docs – Getting Started with Process Configuration Console](https://www.ibm.com/docs/en/filenet-p8-platform/5.2.1?topic=system-getting-started-process-configuration-console)  
