+++
title = "Framework"
description = "N2 Framework"
weight = 40
date = "2025-12-12T01:46:39.298Z"
+++

## Base Framework
N2 provides a structured and extensible framework designed to make automation development predictable, modular, and expressive. At its core, N2 organizes logic into **graphs**, each composed of nodes that define how data moves and how execution progresses.

- **_Graphs_**: A graph represents a complete automation unit—a self-contained script, workflow, or logic tree. In Nuido terminology, a graph may also be referred to as a *flow* or *node definition*. N2 treats all three terms interchangeably, depending on context.

- **_Start Node_**: Every graph defines a single start node. This node marks the graph’s entry point and ensures that execution begins from a known, controlled state.

- **_Node Sequencing_**: Nodes are connected to form a directed execution chain. During runtime, data flows from node to node through defined inputs and outputs. Execution begins at the start node and continues along connected nodes until no further paths remain, signaling completion.

- **_Trigger Node_**: Graphs can optionally define a trigger node. This node listens for external events—such as data updates, user actions, or system changes—and initiates the graph when that event occurs. Trigger nodes are essential for event-driven automation patterns.

- **_Starter Node_**: Before a graph becomes runnable, it must be initialized. Starter nodes execute *only* during this initialization. They prepare the environment by tasks such as creating custom fields, updating metadata, or modifying views. They do not run during normal execution.

- **_Auxiliary Node_**: Some logic does not belong to the primary execution chain yet must exist as part of the graph’s structure. Auxiliary nodes support behaviors such as loops, reusable parameter definitions, internal state containers, or helper utilities. They keep the graph organized, modular, and maintainable without cluttering the main nodes or sequence.

This framework provides a flexible and scalable foundation for building complex automations. It encourages reusability, clear reasoning about workflows, and consistent behavior across both backend execution and frontend representation.

## Backend and Frontend
N2 is implemented in two foundational modules: the backend module `n2` and the frontend module `n2_ui`.

This separation is partly historical and partly architectural. The `n2` backend evolves from the original Nuido Flow engine, expanding its capabilities. The `n2_ui` module represents a fresh, modern approach to the UI layer built to complement the enhanced backend.

### `n2` module
The backend module provides the core execution engine responsible for:

- Handling registry definitions for graphs and it's components.
- Running graphs and managing their lifecycle
- Executing nodes, triggers, and data flows
- Validating graph structures and enforcing execution rules

In spirit, it follows its Nuido predecessor—but with cleaner abstractions, improved extensibility, and enhanced features.

### `n2_ui` module
The frontend module implements the graph editor and visualization environment. While its layout remains conceptually similar (sidebar, toolbar, workspace), the implementation is entirely new. Key UI additions include:

- A modernized interface and visual styling
- Minimap for easier navigation
- Undo/redo support
- More intuitive node manipulation
- A richer, more discoverable node library

Together, `n2` and `n2_ui` provide both the power of a backend execution engine and the usability of a polished editing experience.

## Extensibility
N2 inherits and extends the modular philosophy of Nuido and Nuido Flow. Extensibility is a first-class concern.

New functionality can be introduced without modifying core modules, ensuring:
- Upgradability
- Isolation of features
- Clear ownership of extensions

### Registry System
Both the backend and frontend rely on registry systems that declare and manage the available graph components.

Important characteristics:

- The backend and frontend registries are **separate systems**.
- They serve **different purposes**:
    - The backend registry defines how nodes behave, execute, and interact with data.
    - The frontend registry defines how nodes appear, behave visually, and integrate into the editor.
- Each node type must be registered in **both** registries to function properly.

  This is a one-to-one relationship: a backend node definition must correspond with a matching frontend UI definition.

While their structures differ (Python vs. JavaScript, execution vs. presentation), they work together to ensure that every node is both **runnable** and **usable** within the editor.

### Developing New Nodes
New nodes should always be developed in a separate module, never by modifying core N2 modules.

Since N2 modules are standard Odoo modules, they follow Odoo’s rules and conventions.

#### Module Structure
A typical N2 module looks like:
```tree
- \_\_manifest\_\_.py | fa-brands fa-python | #93a1a1
- \_\_init\_\_.py | fa-brands fa-python | #93a1a1
- data | folder | #93a1a1
    - n2_registry.xml | file | #93a1a1
- graph | folder | #93a1a1
    - messaging
        - \_\_init\_\_.py | fa-brands fa-python | #93a1a1
        - message_node.py | fa-brands fa-python | #93a1a1
    - \_\_init\_\_.py | fa-brands fa-python | #93a1a1
    - node_info.py | fa-brands fa-python | #93a1a1
- static | folder | #93a1a1
    - images | folder | #93a1a1
        - bell.svg  | file | #93a1a1
    - src | folder | #93a1a1
        - components | folder | #93a1a1
            - messaging
            - message_nodes.js  | fa-brands fa-square-js | #93a1a1
            - message_node.xml  | file | #93a1a1
```
> [!NOTE]
> This structure is adapted from the `n2_messaging` module and simplified for clarity.

Unlike many Odoo modules, N2 modules may not include models, views, or controllers. The only requirement for an Odoo module is the presence of `__manifest__.py`.

Everything else follows N2 conventions.

#### Base conventions
N2 modules should follow these conventions:
- Module names must be prefixed with n2_
- The suffix should describe the primary feature or domain
- Code should follow both Odoo and N2 style conventions

#### Creating A New Node
Creating a node requires both client-side and server-side implementation.
##### Client Side (Frontend)
1. Create a template inheriting from `n1.base-node`.
   ```xml
    <t t-name="n2_my_module.my-node" t-inherit="n2.base-node" t-inherit-mode="primary">
        <xpath expr="//div[@id='node-container']" position="inside">
            <label t-attf-id="label-{{props.node.id}}-my-data" t-attf-for="text-{{props.node.id}}-my-data">My Data</label>
            <input class="o_input w-100" t-attf-id="text-{{props.node.id}}-my-data" t-model.lazy="state.data.my_data"></input>
        </xpath>
    </t>
   ```
2. Create a UI component derived from the `BaseNode` class.
    ```javascript
    export class MyNode extends BaseNode {

    }
    ```
3. Define the class name.
    ```javascript
    export class MyNode extends BaseNode {
        static _className = 'MyNode';
    }
    ```
4. Attach the template.
    ```javascript
    export class MyNode extends BaseNode {
        static _className = 'MyNode';
        static template = "n2_my_module.message-node";
    }
    ```
5. Register the node.
    ```javascript
    registerNodeType({
        category: "Data",
        type: MyNode.className,
        label: "My Node",
        description: "My Node description.",
        iconUrl: "/n2_my_module/static/images/my-icon.svg",
        screenSize: { width: "200px", height: "auto" },
        uiComponent: MyNode,
        data: {
            my_data: "This is my data",
        },
        ports: [
            {
                type: "input",
                maxConnections: 1,
                screenPosition: { x: 0, y: "50%" },
                data: { label: 'Input Port' },
            },
            {
                type: "output",
                maxConnections: 1,
                screenPosition: { x: 200, y: "50%" },
                data: { label: 'Output Port' },
            }
        ],
    });
   ```
##### Server Side
1. Register build and create functions in `n2_registry.xml`.
    ```xml
    <?xml version="1.0" encoding='UTF-8'?>
    <odoo>
        <data>
            <!-- BUILD FUNCTIONS -->
            <record id="build_function_my_node" model="n2.registry">
                <field name="category">Build Function</field>
                <field name="key">MyNode</field>
                <field name="value">n2_my_module.graph.node_info,build_my_node</field>
            </record>
            <!-- CREATE FUNCTIONS -->
            <record id="create_function_my_node" model="n2.registry">
                <field name="category">Create Function</field>
                    <field name="key">MyNode</field>
                    <field name="value">n2_my_module.graph.node_info,create_my_node</field>
            </record>
        </data>
    </odoo>
    ```
2. Implement the node logic.
    ```python
    from odoo.addons.n2.graph.core.base_node import BaseNode
    class NotifyNode(BaseNode):
        def _process(self, params):
            parent_res = super()._process(params)
            # Get data from node definition
            my_data = self.definition["my_data"]
            # Process data, etc.
            # The convention is to return a dict.
            my_result = {
                "result": My
            }
            return my_result
    ```
3. Implement the build function and create function.
    ```python
    from ..graph.my_node_directory import my_node
    from odoo.addons.n2.graph.node_info import getBasicInfo

    def build_my_node(node, nodes, edges):
        info = getBasicInfo(node, nodes, edges)
        # Get data from client side definition
        info["my_data"] = node["data"]["my_data"]

        return info

    def create_my_node(environment, create_function_registry, definitions, definition):
        return my_node.MyNode(environment, create_function_registry, definitions, definition)
    ```
This completes the lifecycle of a node—from visual definition, to registry binding, to executable backend behavior—fully aligned with the N2 framework architecture.

## Process Monitoring
N2 provides a **process monitoring** feature designed to assist developers and users during workflow creation, execution, and debugging. When enabled, this feature offers real-time visual feedback directly on the workflow canvas, making it easier to understand the execution state of each node and quickly identify issues.

### Visual Indicators
As a workflow runs, each node is highlighted with a colored border that reflects its current status:
- **Yellow border** – The node is actively processing. This indicates that execution has reached this node and its logic is currently running.
- **Green border** – The node has completed its execution successfully. All associated operations finished without errors.
- **Red border** – The node encountered an error during execution. This helps pinpoint exactly where the workflow failed and simplifies troubleshooting.

These visual cues update dynamically as the workflow progresses, providing immediate insight into execution flow and node behavior.

### Enabling Process Monitoring
Process monitoring is disabled by default. To enable it, update the Odoo system parameters as follows:

1. Go to **Settings → Technical → System Parameters**.
2. Update the parameter:
   - **Key:** `n2.monitor_process`
   - **Value:** `True`
3. Save the changes.

Once enabled, all workflow executions will display node-level processing states using the visual indicators described above.
> [!WARNING]
> Enabling process monitoring introduces overhead during execution and is primarily recommended for development, testing, and debugging environments rather than regular use.
