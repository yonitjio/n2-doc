+++
title = "AI Chat"
weight = 70
description = "N2 AI Chat nodes"
date = "2025-12-12T01:46:39.298Z"
+++

Enables building AI chat pipelines using N2’s graph-based workflows. It lets you define conversational logic, context handling, AI model calls, and responses as interconnected nodes, making chat systems visual, modular, and easy to integrate with other N2 modules.

## Dependencies
This module depends on the following modules *:
- `ai_chat_base`
- `n2_ai`

*Built-in modules not listed

## AiAgentNode
The AI Chat module extends the `AiAgentNode` to accomodate chat features: streaming chats and chat state management.

**Parameters**
- `name` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="inherit" %}}Inherited{{% /badge %}}
- `system_message` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="inherit" %}}Inherited{{% /badge %}}
- `prompt` {{% badge style="tmpl" %}}Tmpl{{% /badge %}} {{% badge style="inherit" %}}Inherited{{% /badge %}}
- `is_html_result` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="inherit" %}}Inherited{{% /badge %}}
- `is_structured` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="inherit" %}}Inherited{{% /badge %}}
- `schema` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="inherit" %}}Inherited{{% /badge %}}
- `is_streaming` {{% badge style="raw" %}}Raw{{% /badge %}}
- `is_stateful` {{% badge style="raw" %}}Raw{{% /badge %}}

## AiChatResponderNode
This node is responsible to send responses from `AiAgentNode` to the frontend.

## ManualResponseNode
Use this node to create manual or templated responses.

**Parameters**
- `message` {{% badge style="tmpl" %}}Tmpl{{% /badge %}}

## OnAiChatMessageTriggerNode
This node is to mark the graph as an AI Chat workflow. It also provide an interface to test the chat workflow.