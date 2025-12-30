+++
title = "Action"
weight = 80
description = "N2 Action nodes"
date = "2025-12-12T01:46:39.298Z"
+++

The N2 Action module provides additional controls for creating Odoo automation. It allows you to define triggers that respond to method calls and server actions, create reusable workflows, and customize the user interface by adding form view headers, buttons, and status bars.

## Dependencies
This module depends on the following modules *:
- `n2`
- `n2_ui`
- `n2_trigger`
- `n2_data`

*Built-in modules not listed

## ActionNode
Executes server action on one or more records of a model.

**Parameters**
- `ids` {{% badge style="eval" %}}Eval{{% /badge %}}
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `record_ids` {{% badge style="raw" %}}Raw{{% /badge %}}

## RunNode
Runs another workflow graph from within the current workflow. Useful for modularizing automation by reusing existing graphs.

**Parameters**
`record_id`  {{% badge style="raw" %}}Raw{{% /badge %}}

## OnActionTriggerNode
Executes the workflow when a specific server action is called. This is used to extend standard Odoo actions with additional custom behavior.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `record_ids` {{% badge style="raw" %}}Raw{{% /badge %}}

## OnMethodTriggerNode
Executes the workflow when a particular method on a model is called. This node allows automation to respond to business logic changes.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `method_name` {{% badge style="raw" %}}Raw{{% /badge %}}

## CodeServerActionStarterNode
Creates a new server action that executes Python code. This node is used to programmatically define automation logic without creating a new Odoo module.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `name`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `code`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `use_existing`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `remove_on_reset`  {{% badge style="raw" %}}Raw{{% /badge %}}

## ViewHeaderStarterNode
Adds a custom header to a form view. This can include status bar or action buttons.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `view_id` {{% badge style="raw" %}}Raw{{% /badge %}}
- `group_ids` {{% badge style="raw" %}}Raw{{% /badge %}}
- `invisible` {{% badge style="raw" %}}Raw{{% /badge %}}
- `use_existing` {{% badge style="raw" %}}Raw{{% /badge %}}
- `remove_on_reset` {{% badge style="raw" %}}Raw{{% /badge %}}

## StatusBarStarterNode
Adds a status bar to a form view header. This can display workflow status, progress, or other indicators relevant to the user.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `field_name` {{% badge style="raw" %}}Raw{{% /badge %}}
- `group_ids` {{% badge style="raw" %}}Raw{{% /badge %}}
- `visible` {{% badge style="raw" %}}Raw{{% /badge %}}
- `invisible` {{% badge style="raw" %}}Raw{{% /badge %}}

## FormActionButtonStarterNode
Adds a clickable action button to a form view header to trigger server actions.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `action_id` {{% badge style="raw" %}}Raw{{% /badge %}}
- `group_ids` {{% badge style="raw" %}}Raw{{% /badge %}}
- `disabled` {{% badge style="raw" %}}Raw{{% /badge %}}
- `icon` {{% badge style="raw" %}}Raw{{% /badge %}}
- `caption` {{% badge style="raw" %}}Raw{{% /badge %}}