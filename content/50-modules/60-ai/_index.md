+++
title = "AI"
weight = 60
description = "N2 AI nodes"
date = "2025-12-12T01:46:39.298Z"
+++

Transforms workflows into intelligent systems by integrating AI agents. This module enables decision-making, content generation, classification, and reasoning capabilities, allowing workflows to adapt dynamically based on data and context.

## Dependencies
This module depends on the following modules *:
- `n2`
- `n2_ui`
- `n2_trigger`
- `n2_data`

*Built-in modules not listed

## Python Requirement
This module requires the following Python package:
- `agent-framework-core`

## AiAgentNode
This node represents an AI agent responsible for orchestrating reasoning, handling tool calls, interacting with context providers, and executing AI-driven tasks.

**Parameters**
- `name` {{% badge style="raw" %}}Raw{{% /badge %}}
- `system_message` {{% badge style="raw" %}}Raw{{% /badge %}}
- `prompt` {{% badge style="tmpl" %}}Tmpl{{% /badge %}}
- `is_html_result` {{% badge style="raw" %}}Raw{{% /badge %}}
- `is_structured` {{% badge style="raw" %}}Raw{{% /badge %}}
- `schema` {{% badge style="raw" %}}Raw{{% /badge %}}

## AiCalculatorMcpToolNode
This node exposes calculator functionality as a Machine-Configurable Protocol (MCP) tool.

## AiClientNode
This node is used to connect the AiAgentNode to your AI backend via the OpenAI Chat API.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `api_key` {{% badge style="raw" %}}Raw{{% /badge %}}
- `base_url` {{% badge style="raw" %}}Raw{{% /badge %}}

These parameters are used as parameters for `OpenAIChatClient` of the Microsoft Agent Framework.

## AiDateToolNode
Provides two date-related tools for the AiAgentNode:

`get_todays_date` — Returns the current date.
`get_todays_datetime` — Returns the current date and time.

These tools allow the agent to incorporate real-time temporal data into its reasoning and outputs.

## ManualContextProviderNode
A context provider node that supplies manually defined contextual information to the AiAgentNode.

**Parameters**
- `context` {{% badge style="tmpl" %}}Tmpl{{% /badge %}}