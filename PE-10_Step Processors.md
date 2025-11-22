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
