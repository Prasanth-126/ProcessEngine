Great — here are complete, ready-to-use Java code examples for working with FileNet Workflows without using VWSession, using only the Content Engine Workflow Java API.


---

✅ 1. Connect to Content Engine (CE) + WorkflowConnection

This is required for all workflow operations.

import com.filenet.api.core.*;
import com.filenet.api.workflow.*;
import com.filenet.api.util.UserContext;

public class CEWorkflowConnect {

    public static WorkflowConnection getWorkflowConnection() {

        String ceUri = "http://your-server:9080/wsi/FNCEWS40MTOM/";
        String username = "p8admin";
        String password = "password";
        String stanza = "FileNetP8WSI";

        // Connect to CE
        Connection ceCon = Factory.Connection.getConnection(ceUri);

        // Authenticate
        UserContext uc = UserContext.get();
        Subject subject = UserContext.createSubject(ceCon, username, password, stanza);
        uc.pushSubject(subject);

        // Create Workflow connection
        WorkflowConnection wfConn = Factory.WorkflowConnection.createWorkflowConnection(ceCon);
        return wfConn;
    }
}


---

✅ 2. Fetch a Roster (Workflow Inbox/Roster List)

public class FetchRosterExample {

    public static void main(String[] args) {
        WorkflowConnection wfConn = CEWorkflowConnect.getWorkflowConnection();

        Roster roster = wfConn.fetchRoster("MyRoster");
        System.out.println("Roster Name: " + roster.get_Name());
    }
}


---

✅ 3. Get and Iterate Workflow WorkItems from Roster

import java.util.Iterator;
import com.filenet.api.workflow.*;

public class FetchWorkItems {

    public static void main(String[] args) {
        WorkflowConnection wfConn = CEWorkflowConnect.getWorkflowConnection();

        Roster roster = wfConn.fetchRoster("MyRoster");

        RosterElementList items = roster.fetchElements(null, null, null, null);

        Iterator<?> it = items.iterator();
        while (it.hasNext()) {
            RosterElement element = (RosterElement) it.next();
            System.out.println("WorkItem ID: " + element.get_F_WorkItemId());
            System.out.println("Workflow Name: " + element.get_F_WorkFlowName());
        }
    }
}


---

✅ 4. Fetch a WorkItem From a User Queue

public class FetchQueueItems {

    public static void main(String[] args) {
        WorkflowConnection wfConn = CEWorkflowConnect.getWorkflowConnection();

        Queue queue = wfConn.fetchQueue("Inbox");

        QueueEntryList list = queue.fetchQueueEntries(null, null, null, null);

        for (Object obj : list) {
            QueueEntry qe = (QueueEntry) obj;
            System.out.println("Queue Item: " + qe.get_F_InstructionName());
        }
    }
}


---

✅ 5. Launch a Workflow (No VWSession Required)

import com.filenet.api.workflow.*;

public class LaunchWorkflow {

    public static void main(String[] args) {
        WorkflowConnection wfConn = CEWorkflowConnect.getWorkflowConnection();

        // Create LaunchStep
        LaunchStep launchStep = wfConn.createLaunchStep("MyWorkflowName");

        // Set parameters
        launchStep.setParameterValue("ApplicantName", "Prasanth");
        launchStep.setParameterValue("ApplicantAge", 25);

        // Launch
        launchStep.launch();
        System.out.println("Workflow launched successfully!");
    }
}


---

✅ 6. Complete a WorkItem

public class CompleteWorkItem {

    public static void main(String[] args) {
        WorkflowConnection wfConn = CEWorkflowConnect.getWorkflowConnection();

        Queue queue = wfConn.fetchQueue("Inbox");

        QueueEntryList list = queue.fetchQueueEntries(null, null, null, null);

        for (Object obj : list) {
            QueueEntry qe = (QueueEntry) obj;

            // Fetch actual work item
            WorkItem wi = qe.fetchWorkItem();

            // Set response / output parameters
            wi.setParameterValue("ApprovalStatus", "Approved");

            // Complete
            wi.complete();
            System.out.println("WorkItem Completed: " + wi.getObjectId());
        }
    }
}


---

🔥 Summary

Using CE Workflow Java API, you can:

Task	Supported without VWSession?

Connect to workflow	✅ Yes
Launch workflow	✅ Yes
Get roster items	✅ Yes
Get queue items	✅ Yes
Fetch WorkItem	✅ Yes
Complete WorkItem	✅ Yes
Direct PE functions	❌ Needs VWSession


So you do not need VWSession for almost all business operations.


---

If you want

I can also give:

✅ Complete utility class for Workflow operations
✅ A sample Spring Boot application connecting to Process Engine
✅ Error handling (not authorized, security token expired, etc.)
✅ A sequence diagram showing how CE → PE Bridge works

Just tell me!