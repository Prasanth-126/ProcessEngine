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
