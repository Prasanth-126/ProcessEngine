✔ What is Process Engine
✔ Workflow creation (Process Designer)
✔ Workflow configuration (Process Administrator)
✔ Workflow monitoring (Process Tracker)
✔ How everything works internally
✔ How to connect using Java API (VWSession & CE Workflow API)

---

🧩 1. What is FileNet Process Engine (PE)?

Process Engine is the workflow engine in IBM FileNet P8 that executes business workflows such as:

Leave request workflow

Loan approval workflow

Aadhar registration workflow

Patient registration

Document approval

Claim processing


PE works together with Content Engine (CE), but its job is:

Component	Responsibility

CE	Stores metadata, documents
PE	Runs workflows (steps, queues, routing rule, timers)



---

🏗️ 2. How FileNet Workflow Works

A workflow typically consists of:

1. Start Step


2. Route (decision)


3. Work Queue Step


4. Integration step (Java, REST, DB)


5. System Step (Auto complete)


6. Stop Step



Workflow items move between queues, handled by users or groups, until completed.


---

🎨 3. Process Designer (Workflow Creation Tool)

Process Designer is used by developers to create workflow definitions.

⭐ You use Process Designer for:

Creating workflow steps

Designing routes

Creating launch parameters

Creating data fields

Adding step processors (custom or default forms)

Assigning participants (users/groups)

Creating system steps (automatic steps)

Adding timers and deadlines

Rule-based routing (if-else routing)


Workflow Components in Designer:

Component	Purpose

Steps	Work performed by user/system
Step Processors	UI form shown to user
Parameters	Input for workflow
Data Fields	Variables stored inside workflow
Queues	WorkList for users
Rosters	All workflow instances
Participants	Who will work on steps
Rules	Routing logic


Example:

Loan Approval Workflow

Step 1: Collect Details

Step 2: Validate Documents

Step 3: Manager Approval

Step 4: Generate Loan Letter



---

🔧 4. Process Config Console (PCC)

PCC is used for configuring the Process Engine:

Connection Points

Event Logs

Logging, tracing

Security (CE → PE security bridge)

PE server configuration



---

🛠️ 5. Process Administrator (Admin Tool for PE)

Used by administrators for managing workflows after deployment.

In Process Administrator, you can:

List workflow definitions

Enable/Disable workflows

Create rosters

Create/manage queues

Transfer work item ownership

Search workflows

Reassign work items to another user

Change step instructions

Restart workflows

Fix stuck workflows


Admins use PA to maintain workflow system health.


---

📊 6. Process Tracker (Monitoring Tool)

Process Tracker is used to monitor active workflow instances.

You can:

Track workflow process diagram

See which step is currently running

View all data fields

View audit logs

View execution path

See delays or bottlenecks

Debug routing

View completed workflows


Tracker is mainly used for debugging and visibility.


---

🔗 7. Workflow Components in Architecture

Workflow Terminology:

Term	Meaning

Workflow Definition	Model created in Designer
Workflow Instance	Actual running workflow
Step	One task
Queue	Work items waiting
Roster	Table storing workflow instances
Roster Element	One entry in roster
Participant	User/group assigned
Launch Step	Step needed to start workflow



---

🧩 8. How Workflow Communicates with CE

PE works with CE using a mechanism called:

✔ PE Bridge to CE

PE requests CE for:

Document metadata

Step processor URLs

Workflow step UI input

Storing data fields (CE fields tied to workflows)


CE stores the metadata but PE controls workflow execution.


---

🧠 9. Changing/Deploying Workflow

Workflow model is saved as a .xdp file.

Steps:

1. Open Process Designer


2. Make your changes


3. Save workflow


4. Publish workflow to Content Engine


5. Administrator enables workflow


6. Ready for execution




---

💻 10. Workflow Through Java API (Two Ways)


---

🔹 A. PE Java API (Direct) — using VWSession (Old way)

Classes used:

Class	Purpose

VWSession	Connect to PE
VWQueue	Fetch queue
VWWorkItem	Get/complete work item
VWRoster	Get roster
VWLaunchStep	Launch workflow


Example:

VWSession session = new VWSession();
session.logon("user", "pwd", "ConnectionPoint");

VWQueue queue = session.getQueue("QueueName");
VWWorkItem wi = queue.fetchWorkItem(false, VWFetchType.LOCK_NO_LOCK);

wi.doLock();
wi.setParameterValue("Approved", true);
wi.doDispatch();

✔ Direct PE connection
✔ Powerful
✘ Old, not recommended for new systems
✘ Needs PE URL and port


---

🔹 B. CE Workflow Java API (Modern Way — No VWSession)

Classes used:

WorkflowConnection

Roster

Queue

WorkItem

LaunchStep


Example: Launch Workflow

LaunchStep launch = wfConn.createLaunchStep("LoanWorkflow");
launch.setParameterValue("ApplicantName", "Prasanth");
launch.launch();

Example: Complete Step

WorkItem wi = qe.fetchWorkItem();
wi.setParameterValue("Approved", "Yes");
wi.complete();

✔ Recommended
✔ Uses CE connection (Web Service)
✔ Secure
✔ Easy


---

🔥 11. Workflow End-to-End Example (Real Time)

Use Case: Aadhar Registration

1. User submits details → Start Workflow


2. Step 1: Document Verification


3. Step 2: Officer Approval


4. Step 3: Generate Aadhar Number


5. Step 4: Send confirmation SMS


6. End workflow



Queues:

VerificationQueue

ApprovalQueue

SystemQueue


Roster:

AadharRoster


Participants:

VerificationGroup

ApprovalGroup


Data Fields:

Name

Mobile

DOB

Address

Status


All this is designed in Process Designer and monitored through Tracker.

Java APIs are used by applications to:

Start workflows

Get pending items

Complete tasks

View workflow status



---

🎯 Final Summary

Component	Purpose

Process Designer	Create workflows
Process Administrator	Manage workflows, queues, rosters
Process Tracker	Monitor running workflows
PCC	Configure PE
Java API (VWSession)	Direct PE connection
Java API (CE Workflow API)	Modern, indirect, secure
