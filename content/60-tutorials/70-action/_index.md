+++
title = "Action Nodes"
weight= 70
description = "Learn how action nodes let you control a model’s behavior in N2 workflows."
images = ["images/logo-gray.png"]
date = "2025-12-12T01:46:39.298Z"
+++

## Prerequisites
- The N2 Core modules, N2 Action module and the built-in Contacts module must be installed.

  If you have not installed the N2 modules yet, please refer to the [Quick Start](/n2-doc/20-getting-started) guide.

- Complete the [Simple Workflow](../20-simple) tutorial.

  Please refer to the [Simple Workflow](../20-simple) tutorial to understand the basics for creating N2 workflow.

## Controlling Model's Action With `OnActionTriggerNode`
In this section, you will create simple workflows that record debug log information in the `ir.logging` table using `CodeServerActionStarterNode` and display a message using `NotifyNode` every time the action is executed.

For these workflows, you will work on the Contact model, therefore all the `Model` field of the nodes must be set to `Contact`.

1. Create a new graph.
2. Add `StartNode` and `CodeServerActionStarterNode` and connect them. `CodeServerActionStarterNode` is an auxiliary node, so it connects to the auxiliary port of the `StartNode`, not to the input port of the `StartNode`.
3. Set the `Name` field of the `CodeServerActionStarterNode` to `action_log_a_message`.
4. Paste the following to the `Code` input dialog `CodeServerActionStarterNode`:
    ```python
    log('This is a message from N2', level='info')
    ```
5. Save and process the graph.
  {{< figure
  src="./images/n2-action-code.png"
  alt="Workflow with CodeServerActionStarterNode."
  caption="Code server action node."
  width="100%"
  >}}
6. Create another graph.
7. Add `OnActionTriggerNode`, `StartNode`, `NotifyNode`, `SetValueNode` and connect these nodes.
8. Set the `Action` field of the `OnActionTriggerNode` to `action_log_a_message`.
9.  Paste the following to the `Template` input dialog of the `NotifyNode`:
    ```python
    'action_log_a_message' is triggered.
    ```
10. Paste the following to the `Value` input dialog of the `SetValueNode`:
    ```python
    {
        "run_original": True
    }
    ```
11. Save and process the graph.
  {{< figure
  src="./images/n2-action-on-action.png"
  alt="Workflow with OnActionTriggerNode."
  caption="Workflow to respond to server action execution event."
  width="100%"
  >}}
12. Create another graph.
13. Add `StartNode`, `ViewHeaderStarterNode`, `FormActionButtonStarterNode` and connect them.
14. Set the `View` field of the `ViewHeaderStarterNode` to `res.partner.form`.
15. Set the `Action` field of the `FormActionButtonStarterNode` to `action_log_a_message`.
16. Set the `Caption` field of the `FormActionButtonStarterNode` to `Log A Message`.
17. Save and process the graph.
  {{< figure
  src="./images/n2-action-button.png"
  alt="Workflow with FormActionButtonStarterNode."
  caption="Workflow for creating button to Contact form."
  width="100%"
  >}}
18. Open a contact via Contact form.
19. There should be a `Log A Message` button. A notification should be displayed when the button is clicked.
  {{< figure
  src="./images/n2-action-notify.png"
  alt="Notification from the server action."
  caption="Notification from the server action."
  width="100%"
  >}}
20. Go to Settings -> Technical -> Logging. A new record should be added whenever you click the `Log A Message` button.
  {{< figure
  src="./images/n2-ir-logging.png"
  alt="Ir.logging view."
  caption="Log message from the server action."
  width="100%"
  >}}

## Explanation
This tutorial demonstrates how N2 can be used to customize Odoo behavior and customize form views.

### Action and Method Triggers

Action trigger and method trigger nodes allow workflows to respond to server-side actions and model methods, enabling deep customization of Odoo behavior without modifying core code.

### Advanced Workflows with N2 Action module
The N2 Action module enables users to create more complex and advanced workflows by exposing server actions and model's method. Users can respond server action and models method using the `OnActionTriggerNode` and `OnMethodTriggerNode`.
And as demonstrated earlier, users can also create custom header for form views. This is useful to create features such as multi-level approvals. Visit [Odoo Development Tutorial: N2 AI Nodes + Creating Multilevel Approval with N2.](https://youtu.be/C-uERrzGv_8) to watch how to create multi-level approval with N2 Action module.

## Next Steps

Now that you understand how to control model actions using the N2 Action module, you can explore more advanced automation patterns:

- Learn how to combine action triggers with data retrieval in the [Data Nodes](../40-data) tutorial.
- Use AI-powered workflows to make decisions based on action context in the [AI Integration](../50-ai) tutorial.
- Build interactive user experiences by combining action nodes with conversational workflows in the [AI Chat](../60-ai-chat) tutorial.
- Explore advanced approval flows and conditional execution using `OnMethodTriggerNode` and custom form headers.
