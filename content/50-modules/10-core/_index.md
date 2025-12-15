+++
title = "Core Modules"
weight = 10
description = "Core Modules"
date = "2025-12-12T01:46:39.298Z"
+++

The `n2` and `n2_ui` modules are the core of N2. Together they provide the base framework and the core functionalities to enable visual automation on Odoo.
​
## ConditionalNode
Define conditions that determine the next node in the workflow, allowing for decision-based branching.

**Parameters**
- `condition` {{% badge style="eval" %}}Eval{{% /badge %}}: Expression to determine the next node.
​
## ForLoopNode
Execute a sub-process repeatedly using a for-range loop, useful for iterating over a specific number of steps.
```python
for i in range(<start_value>, <end_value>, <step>)
```
**Parameters**
- `start_value` {{% badge style="raw" %}}Raw{{% /badge %}}
- `end_value` {{% badge style="raw" %}}Raw{{% /badge %}}
- `step` {{% badge style="raw" %}}Raw{{% /badge %}}

## LogNode
Output log messages at any point in the workflow, providing transparency and debugging support.

**Parameters**
- `tag`  {{% badge style="raw" %}}Raw{{% /badge %}}: Used as prefix for logging.

## LoopNode
Loop through a sub-process with a for-in loop, iterating over items in a collection.

```python
for item in <iterable>
```
**Parameters**
- `iterable` {{% badge style="eval" %}}Eval{{% /badge %}}

## LooperNode
Mark the starting point of a loop sub-process, facilitating structured iteration within workflows.

## MergeNode
Combine data from multiple nodes into a single output, streamlining data integration.
​
## SpreadNode
Repeat sub-processes with the same parameters, enabling parallel or repetitive operations efficiently.
​
## StartNode
Indicate the beginning of a workflow, establishing a clear entry point for automation.

**Parameters**
- `parameters` {{% badge style="raw" %}}Raw{{% /badge %}}
​
## ValueNode
Set or pass values to be used by subsequent nodes, allowing dynamic data handling throughout the workflow.

**Parameters**
- `value` {{% badge style="eval" %}}Eval{{% /badge %}}
