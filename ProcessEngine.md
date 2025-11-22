# 📘 FileNet Process Engine Overview

## 🔹 What It Is
A core component of the **IBM FileNet P8 platform** that manages business processes.

## 🔹 Purpose
- Automates, monitors, and optimizes business workflows.

## 🔹 Key Capabilities
- Process modeling and execution  
- Task routing and escalation  
- Integration with content and external systems

---

# 🔄 What Is a Process?

## 🔹 Definition
A sequence of tasks or activities designed to achieve a specific business goal.

## 🔹 In FileNet
- Modeled using **Process Designer**
- Can include both **manual** and **automated** steps

## 🔹 Examples
- Invoice approval  
- Employee onboarding  
- Claims processing

---

# 👥 Participants

## 🔹 Who Are They?
Users or systems that perform tasks within a process.

## 🔹 Types
- **Users**: Human participants assigned to work items  
- **Roles**: Groups of users with similar responsibilities  
- **Queues**: Workbaskets where tasks are routed

## 🔹 Assignment
- Based on roles, skills, or workload

---

# 🔁 Workflow

## 🔹 Definition
The automated flow of tasks, documents, and decisions through a process.

## 🔹 Components
- **Steps**: Activities or decisions  
- **Routes**: Paths between steps  
- **Rules**: Conditions that guide flow

## 🔹 Design Tools
- FileNet **Process Designer**  
- FileNet **Case Builder**

---

# 📝 Sample Workflow – Document Approval

## 💳 Sample Credit Card Application Flow

1. **Start**  
   The process begins when a customer decides to apply for a credit card.

2. **Submit Application**  
   The applicant fills out and submits the credit card application form (online or offline).

3. **Review Application**  
   The bank reviews the application for completeness and accuracy.  
   - If **rejected**: Send rejection notice → **End**  
   - If **accepted**: Proceed to eligibility checks

4. **Check Eligibility**  
   The system or officer verifies eligibility (e.g., income, credit score, age).  
   - If **eligible**: Proceed to Open Account  
   - If **not eligible**: Send rejection notice → **End**

5. **Open Account**  
   If qualified, the bank creates a credit card account for the customer.

6. **Issue Card**  
   The credit card is issued and dispatched to the customer.

**End**  
The workflow concludes after the card is issued or the rejection notice is sent.

### 📊 Workflow Diagram (Text-Based)
```markdown
Start
  ↓
Submit Application
  ↓
Review Application
  ├── If Rejected → Send Rejection → End
  └── If Accepted → Check Eligibility
                        ↓
              ├── If Not Eligible → Send Rejection → End
              └── If Eligible → Open Account
                                      ↓
                                Issue Card
                                      ↓
                                     End
```

---

# ✅ Advantages of Using Workflows

- **Efficiency**: Reduces manual effort and processing time  
- **Consistency**: Standardizes business operations  
- **Visibility**: Tracks progress and bottlenecks  
- **Compliance**: Ensures audit trails and policy adherence  
- **Scalability**: Adapts to growing business needs



# ⚙️ IBM FileNet BPM Overview

## 🔹 What Is FileNet BPM?

**IBM FileNet BPM (Business Process Manager)** is a workflow and process automation solution built on the FileNet platform. It helps organizations design, execute, monitor, and optimize business processes—especially those involving content and document-centric workflows.

FileNet BPM is part of IBM’s **Enterprise Content Management (ECM)** suite. It integrates workflow automation with document management, enabling businesses to streamline operations, enforce compliance, and improve efficiency.

---

# 🚀 FileNet BPM – Key Features

## 🔸 Process Automation
- Automates document-centric workflows (e.g., loan approvals, credit card applications)  
- Reduces manual intervention and accelerates decision-making

## 🔸 Graphical Process Designer
- Drag-and-drop interface for designing workflows  
- Supports swimlanes, decision points, and routing rules

## 🔸 Integration with FileNet Content Manager
- Direct access to documents stored in FileNet repositories  
- Workflows can trigger actions based on document events (create, update, delete)

## 🔸 Role-Based Routing
- Assigns tasks to users or groups based on roles  
- Supports dynamic routing based on business rules

## 🔸 Business Rules Engine
- Allows defining conditions for approvals, escalations, and routing  
- Example: `Credit score > 700 → Auto-approve`

## 🔸 Monitoring & Analytics
- Real-time dashboards for process performance  
- SLA tracking and bottleneck identification

## 🔸 Integration Capabilities
- Connects with external systems via Web Services, REST APIs, and Java APIs  
- Supports integration with ERP, CRM, and other enterprise apps

## 🔸 Security & Compliance
- Role-based access control  
- Audit trails for regulatory compliance

## 🔸 Scalability
- Handles high-volume workflows across multiple departments  
- Supports distributed architecture for large enterprises

## 🔸 Mobile & Web Access
- Users can participate in workflows from web or mobile interfaces

---

📖 [IBM FileNet Workflow Management Documentation](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=features-workflow-management)


# 🛠️ FileNet Process Engine Tools

IBM FileNet provides a suite of tools to design, configure, monitor, and manage business workflows within the Process Engine.

## 🔧 FileNet Process Configuration Console (PCC)

An administrative tool used to configure and manage the **Process Engine** environment.

### 🔸 Purpose
- Set up workflow system properties  
- Manage queues, rosters, and event logs  
- Configure security and connectivity settings

---

## 🎨 FileNet Process Designer

A graphical design tool for creating and modeling workflows in FileNet.

### 🔸 Purpose
- Design process maps with steps, roles, and routing rules  
- Define deadlines, milestones, and integration points  
- Validate and deploy workflows to the Process Engine

---

## 📊 FileNet Process Tracker

A tracking tool that provides visibility into workflow execution and performance.

### 🔸 Purpose
- Monitor workflow progress and status  
- Generate reports on workflow activities  
- Analyze bottlenecks and optimize processes

---

## 🔐 FileNet Process Administrator

An administrative interface for managing workflow instances and user assignments.

### 🔸 Purpose
- Reassign or suspend work items  
- Troubleshoot workflow errors  
- Manage workflow participants and queues

📖 [IBM FileNet Workflow Management Documentation](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=features-workflow-management)

---

# 📘 FileNet Process Engine – Terminology Overview

Understanding key terms used in FileNet Process Engine helps in designing and managing workflows effectively.

## 🔑 Key Terms

### 1. **Workflow Definition**
- **What it is**: A blueprint or template that defines the sequence of steps (activities) in a business process  
- **Purpose**: Models business logic, routing rules, participants, and deadlines  
- **Example**: An invoice approval process with steps like “Receive Invoice,” “Verify,” “Approve,” and “Archive”

---

### 2. **Workflow**
- **What it is**: An instance of a Workflow Definition  
- **Purpose**: Represents a live execution of a business process  
- **Example**: A specific invoice going through the approval process

---

### 3. **Work Item**
- **What it is**: A unit of work assigned to a user or system  
- **Purpose**: Represents a task that needs to be completed as part of a workflow  
- **Types**:
  - **Step Workitem**: Assigned to a user or role  
  - **System Workitem**: Executed by the system (e.g., auto-routing)  
- **Example**: “Verify invoice amount” assigned to an Accounts Payable clerk

---

### 4. **Queue**
- **What it is**: A container that holds work items waiting to be processed  
- **Purpose**: Organizes and prioritizes tasks for users or roles  
- **Example**: “Accounts Payable Queue” with pending invoice verification tasks

---

### 5. **Roster**
- **What it is**: A searchable list of all workflows (process instances)  
- **Purpose**: Used for tracking, auditing, and reporting  
- **Example**: A roster showing all invoice approval workflows initiated in the last month

---

### 6. **Event Log and Events**
- **Event Log**:
  - **What it is**: A record of all significant actions and changes in the Process Engine  
  - **Purpose**: Helps in auditing and troubleshooting  
- **Events**:
  - **What they are**: Triggers or notifications generated by workflow actions (e.g., step completed, deadline missed)  
  - **Types**: System events, custom events  
  - **Example**: An event triggered when an invoice is approved, logged in the Event Log

📖 [IBM FileNet Glossary](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=glossary)


# ⚙️ FileNet Process Designer – Component Step

## 🔹 What Is a Component Step?

A **Component Step** is a workflow step that executes custom logic or external processes via the **Component Queue** in FileNet Process Engine.

### 🔸 Purpose
- Used for tasks that require integration with external systems or custom Java code  
- Enables automation beyond standard workflow steps

---

## 🔧 Configuration

### 🔸 Steps to Configure
1. Create a **Component Queue** in Process Configuration Console  
2. Define the **Execution Class** (Java class implementing `execute()` method)  
3. Configure **Step Type** in Process Designer and link it to the queue

### 🔸 Key Parameters
- **Max Threads**  
- **Retry Count**  
- **Timeout Settings**

### 🔸 Best Practices
- Use **descriptive queue names**  
- Validate **execution class** before deployment

---

## 🔄 Passing Data from Workflow to Component Step

### 🔸 Mechanism
Workflow fields → Component Step → Execution Class

### 🔸 How to Map Data
- Use **Parameter Mapping** in Process Designer  
- Define **Input/Output Parameters** in Component Queue

### 🔸 Example
`Workflow field CustomerID → Component step parameter → Java class method`

### 🔸 Tips
- Validate **data types**  
- Handle **null values** gracefully

---

## 🚀 Performance & Threading in Component Queue

### 🔸 Threading Model
- Each queue has a **Max Threads** setting  
- Threads execute component steps concurrently

### 🔸 Performance Factors
- Queue size  
- Thread count vs CPU cores  
- External system latency

### 🔸 Tuning Guidelines
- Start with default threads (e.g., 5–10)  
- Monitor queue backlog in PE logs  
- Scale threads gradually

### 🔸 Avoid Pitfalls
- **Over-threading** → CPU contention  
- **Long-running steps** → Queue bottlenecks

---

## 🛠️ Monitoring & Troubleshooting

### 🔸 Tools
- Use **Process Engine logs** for queue activity  
- Check **Component Queue status** in Process Configuration Console

### 🔸 Common Issues
- Deadlocks  
- Timeout errors  
- Data mapping failures

---

## 📖 IBM Documentation Links

- [Designing Workflows](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=management-designing-workflows)  
- [About Workflow Steps](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=workflows-about-steps)  
- [About Component Steps](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=steps-about-component)  
- [System Functions](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=steps-system-functions)  
- [General Step Activity](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=functions-general-step-activity)


# ⚙️ FileNet Process Designer – System Step

## 🔹 What Is a System Step?

A **System Step** is a workflow element that performs built-in system functions automatically without human intervention. It is used for logic control, data manipulation, and workflow automation within the Process Engine.

### 🔸 Purpose
- Automates tasks that do not require user interaction  
- Executes predefined system functions such as:
  - Setting deadlines or timers  
  - Checking conditions  
  - Triggering events  
  - Invoking web services  
  - Managing workflow data

### 🔸 Automation Without Human Intervention
System Steps eliminate manual effort by automating internal workflow logic.

### 🔸 Logic Control and Data Manipulation
They enable precise control and data handling to ensure smooth workflow execution.

### 🔸 Integration with External Systems
System Steps can invoke web services and interact with external applications.

### 🔸 Use Cases in Enterprise Workflows
- SLA timers  
- Variable updates  
- Workflow transitions

---

## 🚀 Key Features

- **No manual processing**: Executes automatically when reached  
- **Supports multiple system functions**:
  - General System Functions: Assign values, set workflow properties  
  - Timer Functions: Delay or schedule actions  
  - Checkpoint Functions: Save workflow state  
  - Web Services Functions: Call external services  
- **Configurable Parameters**: Each function has its own properties (e.g., timeout, data fields)

---

## 🛠️ How to Add a System Step

1. Open **Process Designer** in Design Mode  
2. From the **Step Palette**, drag **System Step** onto the workflow map  
3. Configure Properties:
   - Select the System Function (e.g., Timer, Checkpoint, Web Service)  
   - Define input/output parameters  
   - Set conditions if needed  
4. Connect Routes to define workflow logic after execution

---

## 🧩 FileNet System Functions

| Function             | Purpose                                                                 | Use Case Example                                      |
|----------------------|-------------------------------------------------------------------------|--------------------------------------------------------|
| **Assign**           | Assigns values to workflow/system fields                                | Status = "Approved"                                   |
| **Call**             | Invokes another workflow or sub-map                                     | Reuse approval sub-process                            |
| **Create**           | Launches a workflow of a specific definition                            | Create new case file                                  |
| **DbExecute**        | Executes SQL/stored procedures on external DB                           | Update/retrieve business data                         |
| **Delay**            | Pauses workflow for a specified time                                    | Wait 24 hours before reminder                         |
| **Log**              | Writes messages to system log                                           | Track progress/errors                                 |
| **Return**           | Returns control from sub-map to main map                                | End sub-process                                       |
| **TerminateBranch**  | Ends a specific workflow branch                                          | Stop parallel processing                              |
| **TerminateProcess** | Ends the entire workflow instance                                        | Cancel process on failure                             |
| **Timer - Begin**    | Starts a timer for SLA/deadline tracking                                | Begin countdown                                       |
| **Timer - End**      | Stops a specific timer                                                   | Mark SLA completed                                    |
| **Timer - End All**  | Stops all active timers                                                  | Reset timers                                          |
| **WaitForCondition** | Pauses workflow until a condition is true                               | Wait for document approval                            |
| **Invoke**           | Calls external web service/API                                           | Integrate with ERP/CRM                                |
| **Receive**          | Receives message/event from external system                             | Trigger workflow from external input                  |
| **Reply**            | Sends response back to invoking system                                  | Confirm completion to external app                    |

---

## 🔄 Call vs Create – Key Differences

### 🔸 Call
- **Purpose**: Invokes another workflow map or sub-map  
- **Behavior**: Transfers control; waits for completion  
- **Use Case**: Reuse predefined logic  
- **Key Point**: Does **not** create a new work object

### 🔸 Create
- **Purpose**: Creates a new work object/document and optionally starts a workflow  
- **Behavior**: Generates new entity in Content Engine  
- **Use Case**: Create new case file or document  
- **Key Point**: **Creates** a new entity unlike Call

---

## 📌 Common Use Cases

- **Timeout Handling**: Escalate if task not completed in time  
- **Data Updates**: Modify workflow variables automatically  
- **Integration**: Invoke external services for data exchange  
- **Workflow Control**: Pause, resume, or checkpoint workflows

---

## 📖 IBM Documentation Links

- [Designing Workflows](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=management-designing-workflows)  
- [System Functions Overview](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=steps-system-functions)  
- [General Step Activity](https://www.ibm.com/docs/en/filenet-p8-platform/5.7.0?topic=functions-general-step-activity)


# 📘 DB Execute Workflow Setup Guide

## Step 1: Create Administration DB Execute Connection in ACCE
Navigate:  
**Administrative → Workflow Systems → DB Execute Connection → New**

Fill in the following fields:
- **Connection Name**: *(example: FNOS-DB)*
- **Database Type**: *(example: DB2)*
- **Database Name**: *(example: FNOSDB)*
- **Database Host Name**: *(enter host name)*
- **Database Port**: *(example: ******)*
- **DB Username**: *(example: ******)*
- **DB Password**: *(example: ******)*

Then:  
**Next → Validate → OK → Save**

---

## Step 2: Connect to the Server (Remote Connection)
Open **DB2 Command Window** from the search bar.  

Use the following commands:

```bash
db2start                 -- Start the server (optional)
db2 list db directory    -- List all databases in DB2
db2 connect to DB_NAME   -- Connect to a specific database
db2 list tables          -- Show all tables in the database
db2 disconnect DB_NAME   -- Disconnect from the database
```

---

## Step 3: Create a Table
Syntax:

```sql
db2 "CREATE TABLE Table_Name (
    Column1 datatype(size),
    Column2 datatype(size),
    Column3 datatype(size)
)"
```

---

## Step 4: Create a Procedure
Syntax:

```sql
CREATE PROCEDURE Procedure_Name (
    INOUT param1 INT
)
LANGUAGE SQL
BEGIN
    -- Modify the INOUT parameter value
    SET param1 = param1 + 10;
END
```

---

## Step 5: Create Workflow in Process Designer
In the **DBExecute Step**, specify:
1. **Database Connection Alias** → The alias created in ACCE  
2. **Procedure Name** → `SchemaName.Procedure_Name`  
3. **Parameters** → Match the order with table columns  

Then perform:  
**Validate → Check-in → Transfer → Launch Workflow**

Open **PE Administrator → PE Tracker** and complete the task.



⚠️ **Note**: If you encounter any exceptions, refer to *MalFunction* documentation to understand and resolve the error.

---

## Step 6: Verify Data Storage
After successful workflow completion, open **DB2 Command Window** and check data:


By using below command check the data:
```sql
db2 "SELECT * FROM Table_Name"
```


   # IBM FileNet 5.5.8 Step Processors

## Navigator Step Processor
The **Navigator Step Processor** is the preferred choice for modern FileNet deployments due to its flexibility, web-based interface, and integration with **IBM Content Navigator (ICN)**.  
It supports advanced customization through **Dojo widgets**, **JavaScript hooks**, and **layout XML configurations**.

---

## How to Configure a Step Processor
1. **Design Workflow**: Use Process Designer or Case Builder to define workflow steps.  
2. **Assign Step Processor**: In the step properties, specify the step processor type (e.g., In-Basket, Custom).  
3. **Configure Parameters**: Set input/output parameters, UI labels, and routing logic.  
4. **Deploy Workflow**: Publish the workflow definition to the Process Engine.  
5. **Test and Validate**: Ensure the step processor behaves as expected in the runtime environment.  

---

## Why Customize Step Processors?
Customization is often necessary to:
- **Align with Business Processes**: Tailor UI to match specific workflows or data capture needs.  
- **Enhance User Experience**: Improve usability with modern interfaces, validations, and dynamic behavior.  
- **Integrate with Other Systems**: Embed APIs or external services into the workflow UI.  
- **Support Branding**: Match corporate branding and design standards.  

### Customization Methods
- **Java-based development** (for Workplace XT)  
- **JavaScript and REST APIs** (for ICN custom widgets)  
- **HTML5/CSS** for responsive design  

---

## Navigator Step Processor Overview
The Navigator Step Processor is a component of **IBM Content Navigator** that renders workflow steps (work items) in a browser-based UI.  
It is the **default step processor** when using ICN as the client interface for FileNet workflows.

### Key Features
- **Web-based UI**: Runs in a browser, no desktop client required  
- **Customizable**: Supports custom widgets and layouts using Dojo and JavaScript  
- **Integrated with ICN**: Leverages ICN’s security, navigation, and content services  
- **Responsive Design**: Suitable for various screen sizes and devices  

---

## How It Works
1. **Workflow Step Assignment**: A user receives a work item in their ICN in-basket.  
2. **Step Processor Launch**: ICN invokes the Navigator Step Processor to render the step.  
3. **UI Rendering**: Displays fields, attachments, and actions based on the workflow definition.  
4. **User Interaction**: The user completes the step by entering data or making decisions.  
5. **Submission**: Data is validated and submitted back to the Process Engine.  

---

## Customization Options
- **Custom Widgets**: Create Dojo-based widgets to extend or replace default UI components.  
- **Layout Configuration**: Modify layout XML to change field arrangement and behavior.  
- **JavaScript Hooks**: Use event handlers to add logic during step load, validation, or submission.  

---

## 🧑‍💻 When to Use It
Use the Navigator Step Processor when:
- Deploying FileNet workflows via **IBM Content Navigator**  
- You want a **modern, browser-based experience**  
- You need to **customize the UI** for specific business needs without building a full custom application  


# Malfunction Step in Workflows

## What Is a Malfunction Step?
A **malfunction step** is a specific point in a workflow or process where an error or failure occurs, causing the process to deviate from its expected behavior.  

It’s often used in:

- **FileNet Process Engine** examples:
  - A workflow step that fails to execute due to an error (e.g., script failure, missing data, system outage).
  - A designated step in a workflow that handles exceptions or errors (similar to a catch block in programming).
  - A custom step configured to log the error, notify administrators, or reroute the workflow.

---

## Purpose of a Malfunction Step
- **Error handling**: Captures and logs the issue.  
- **Process continuity**: Allows the workflow to continue or end gracefully.  
- **Notification**: Triggers alerts to administrators or users.  
- **Debugging**: Helps identify root causes for failures.  

---

## Example: Malfunction Step in FileNet Workflow

### Invoice Approval Workflow
**Workflow Steps:**
1. Submit Invoice  
2. Manager Approval  
3. Finance Review  
4. Payment Processing  

**Problem:**  
If the **Finance Review** step fails (e.g., due to a missing account number), the workflow cannot continue.

**Malfunction Step:**  
- **Step Name:** `FinanceErrorHandler`  
- **What it does:**  
  - Logs the error (e.g., “Missing account number”)  
  - Sends an email to the finance team  
  - Moves the invoice to a **Manual Review** queue  

**Result:**  
Instead of stopping the entire workflow, the process continues by alerting the right team and allowing them to fix the issue manually.  

---

## Override Malfunction Submap

### Steps to Override the Malfunction Submap
1. **Open Workflow Properties**  
   - In Process Designer, select the **Action** menu → **Workflow Properties** → **Maps tab**.  

2. **Select the Malfunction Map**  
   - The Maps tab lists all maps, including the main map, user-defined submaps, and system maps like **Terminate** and **Malfunction**.  
   - Select the **Malfunction system map**.  

3. **Override the Map**  
   - Use the option to override the selected map.  
   - This makes the existing steps on the system-provided map available for modification or deletion.  

4. **Define Custom Processing**  
   - Modify the steps within the overridden Malfunction submap to define specific error handling logic.  
   - Examples:  
     - Log the error details in a data field.  
     - Notify a specific user or workgroup via email.  
     - Route the work item to an administrative queue for manual review.  
     - Use a **Return system function** to control where processing continues after the exception is handled.  

5. **Validate and Save**  
   - Apply modifications, validate the workflow, and save it.  

---

## Key Considerations
- **Custom Return Logic**  
  - If you place a step with a Return system function on your custom Malfunction map, ensure the Return expression is set appropriately.  
  - `false` → continues processing after the step that caused the error.  
  - `true` → may repeat the call or return to the calling map depending on context.  

- **Permissions**  
  - Ensure you have the necessary IBM FileNet license and system administrator permissions to override system-supplied maps.  

- **Testing**  
  - Thoroughly test your custom malfunction submap to ensure it handles exceptions correctly and routes work items as expected.
 


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
- [IBM Documentation: Processing parallel or sequential workflows (FileNet P8)](https://www.ibm.com/docs/en/content-navigator/3.1.0?topic=navigator-processing-parallel-sequential-workflows-filenet-p8)



