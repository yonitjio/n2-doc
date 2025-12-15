+++
title = "Messaging"
weight = 50
description = "N2 messaging nodes"
date = "2025-12-12T01:46:39.298Z"
+++

This module supplies a collection of nodes dedicated to delivering messages to users. This includes notifications, alerts, and other communication mechanisms that can be embedded directly into workflows to keep users informed or prompt action.

## Dependencies
This module depends on the following modules *:
- `n2`
- `n2_ui`

*Built-in modules not listed

## Python Requirement
This module requires the following Python package:
- `markdown`

## MessageNode
A node used to send messages directly to users through OdooBot.

**Parameters**
- `template` {{% badge style="tmpl" %}}Tmpl{{% /badge %}}

## NotifyNode
A node responsible for displaying sticky notifications to users.

**Parameters**
- `template` {{% badge style="tmpl" %}}Tmpl{{% /badge %}}
- `sticky` {{% badge style="raw" %}}Raw{{% /badge %}}
