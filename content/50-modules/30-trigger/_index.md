+++
title = "Triggers"
weight = 30
description = "N2 trigger nodes"
date = "2025-12-12T01:46:39.298Z"
+++

This module provides the core trigger nodes that initiate automation workflows. Triggers represent entry points such as scheduled events, user actions, or system events, enabling workflows to react to changes or external inputs.

## Dependencies
This module depends on the following modules *:
- `n2`
- `n2_ui`

*Built-in modules not listed

## OnCreateTriggerNode
Triggers the workflow automatically whenever a new record is created in Odoo.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="patched" %}}Patched{{% /badge %}}

## OnDeleteTriggerNode
Activates the workflow when an existing record is deleted.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="patched" %}}Patched{{% /badge %}}

## OnEditTriggerNode
Fires the workflow whenever an existing record is updated or modified.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="patched" %}}Patched{{% /badge %}}
- `selected_fields` {{% badge style="raw" %}}Raw{{% /badge %}}

On graph processing stage, the `selected_fields` is saved and used to find the related `model`'s fields.

## OnScheduleTriggerNode
Executes the workflow on a defined schedule or time interval. This node is useful for recurring tasks such as automated reports, routine checks, or scheduled reminders.

**Parameters**
- `interval` {{% badge style="raw" %}}Raw{{% /badge %}}
- `interval_type` {{% badge style="raw" %}}Raw{{% /badge %}}

## OnWebhookTriggerNode
Initiates the workflow in response to an external webhook request. This allows seamless integration with third-party applications, enabling workflows to start when external events or API calls occur.

**Parameters**
- `webhook_id` {{% badge style="raw" %}}Raw{{% /badge %}}

The `webhook_id` is saved on graph processing stage. When a request is sent to N2 controller, `webhook_id` is used to validate the request.
