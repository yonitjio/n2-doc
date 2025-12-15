+++
title = "Modules"
description = "Modules"
weight = 50
date = "2025-12-12T01:46:39.298Z"
+++

N2 is a modular automation platform composed of a set of core and optional modules. Each module focuses on a specific responsibility, allowing you to enable only the functionality you need while keeping the system extensible and maintainable.

## Core Modules

- **`n2`**
  The backend module that provides the core execution engine of N2. It is responsible for workflow orchestration, node execution, state management, and communication between modules. All workflows rely on this module to run reliably and efficiently.

- **`n2_ui`**
  The frontend module that delivers the visual workflow editor and runtime visualization environment. It allows users to design, configure, and monitor workflows using an interactive graph-based interface, making complex automations easier to understand and manage.

## Extension Modules

- **`n2_elk`**
  Extends N2 by integrating **ElkJS** to automatically compute and apply layout arrangements for workflow diagrams. This module improves readability by organizing nodes and connections, especially in large or complex workflows.

- **`n2_trigger`**
  Provides the core trigger nodes that initiate automation workflows. Triggers represent entry points such as scheduled events, user actions, or system events, enabling workflows to react to changes or external inputs.

- **`n2_data`**
  Offers a suite of configurable workflow nodes designed to simplify data automation within Odoo. These nodes handle common data operations such as reading, transforming, validating, and writing records, reducing the need for custom code.

- **`n2_messaging`**
  Supplies a collection of nodes dedicated to delivering messages to users. This includes notifications, alerts, and other communication mechanisms that can be embedded directly into workflows to keep users informed or prompt action.

- **`n2_ai`**
  Transforms workflows into intelligent systems by integrating AI agents. This module enables decision-making, content generation, classification, and reasoning capabilities, allowing workflows to adapt dynamically based on data and context.

- **`n2_ai_chat`**
  Enables building AI chat pipelines using N2’s graph-based workflows. It lets you define conversational logic, context handling, AI model calls, and responses as interconnected nodes, making chat systems visual, modular, and easy to integrate with other N2 modules.

Together, these modules form a flexible ecosystem that allows N2 to scale from simple automations to complex, intelligent workflow systems.
