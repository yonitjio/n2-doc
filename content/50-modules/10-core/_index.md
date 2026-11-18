+++
title = "Core Modules"
weight = 10
description = "Core Modules"
date = "2025-12-12T01:46:39.298Z"
+++

The `n2` and `n2_ui` modules are the core of N2. Together they provide the base framework and the core functionalities to enable visual automation on Odoo.
​
## ConditionalNode {{% badge style="sin" %}}Std{{% /badge %}} {{% badge style="sout" %}}Std{{% /badge %}}
Define conditions that determine the next node in the workflow, allowing for decision-based branching.

### Parameters
- `condition` {{% badge style="eval" %}}Eval{{% /badge %}}

### How It Works
The expression specified by the `condition` parameter is evaluated at runtime using the current graph context and the input received from the upstream node to determine the next node to execute.

If the expression evaluates to `True`, the process function of the node connected to the upper output port is invoked; otherwise, the process function of the node connected to the lower output port is invoked.

## ForLoopNode {{% badge style="sin" %}}Std{{% /badge %}}
Execute a sub-process repeatedly using a for-range loop, useful for iterating over a specific number of steps.

### Parameters
- `start_value` {{% badge style="raw" %}}Raw{{% /badge %}}
- `end_value` {{% badge style="raw" %}}Raw{{% /badge %}}
- `step` {{% badge style="raw" %}}Raw{{% /badge %}}

### How It Works
The `ForLoopNode` uses the parameters value for arguments the for-range loop to execute the nodes connected to the `LooperNode`.
```python
for i in range(<start_value>, <end_value>, <step>)
```

## LogNode
Output log messages at any point in the workflow, providing transparency and debugging support.

### Parameters
- `tag`  {{% badge style="raw" %}}Raw{{% /badge %}}: Used as prefix for logging.

### How It Works
The input parameters is serialized to string and printed using `logging` module.
The `tag` parameter value used as prefix for logging the input parameters.

```python
_logger.info("%s: %s", tag, log_msg)
```

## LoopNode
Loop through a sub-process with a for-in loop, iterating over items in a collection.

### Parameters
- `iterable` {{% badge style="eval" %}}Eval{{% /badge %}}

### How It Works
The `iterable` parameter is evaluated and used in for-in loop:
```python
for item in <iterable>
```

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

### Parameters
- `parameters` {{% badge style="dict" %}}Dict{{% /badge %}}
​
## ValueNode
Set or pass values to be used by subsequent nodes, allowing dynamic data handling throughout the workflow.

### Parameters
- `value` {{% badge style="eval" %}}Eval{{% /badge %}}
