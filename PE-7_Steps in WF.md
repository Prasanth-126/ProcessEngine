# Steps in Workflow Design

## About Steps
A **step** is a stage in a workflow where a distinct, well-defined kind of work is performed.  
Each step on a workflow map represents a specific activity or task in the business process you are defining.

---

## Working with Steps
- **Process Designer** provides palettes of pre-defined steps in the docked palette of the steps section.  
- You can add these steps to the workflow map to represent different types of activities.  
- Work with the docked palette or click the right arrow icon `>> Open Palette Window` to use a floating palette.  
- Each type of step provides an appropriate interface where you define the parameters for processing that step.

---

## Types of Steps

### Launch Step
- The **Launch step** is the first step in a workflow.  
- It is automatically placed on the main workflow map when you create a new workflow definition.  
- This step can be renamed, but it **cannot be deleted or copied**.

### Activity Step
- Represents an activity in a workflow.  
- Processed by either:
  - One or more workflow participants, or  
  - A work queue.

### Submap Step
- Represents a call from the current workflow map to another map in the same workflow definition.  
- Can be placed on any map.

### System Step
- Provides a way to include one or more **IBM® FileNet-supplied system functions** at a particular point in a workflow definition.

#### System Functions
- Built-in system functions perform logic-control and other functionality in the workflow.  
- You can include one or more system functions in a system step.

### Component Step
- Makes it possible to route work to operations in custom **Java™** or **Java Message Service (JMS)** components.  
- Connects to a component queue configured for one or more operations in the custom component.  
- Can be placed on any workflow map.

