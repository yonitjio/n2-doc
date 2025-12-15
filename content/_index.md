+++
title = "N2 Documentation"
type = "home"
description = "N2 Documentation Home"
date = "2025-12-12T01:46:39.298Z"
+++

**N2 is the next evolution of the Nuido ecosystem, designed to bring a unified and streamlined approach to visual automation in Odoo.**
Where the original Nuido library focused on node-based user interfaces and Nuido Flow extended those capabilities into visual automation, N2 consolidates these concepts into a single, cohesive framework.

Unlike its predecessors—which separated functionality into distinct base modules—N2 is built on two core components:

- **N2** — the backend foundation, providing Python logic, XML views, and server-side integration.
- **N2 UI** — the frontend layer, delivering the JavaScript framework, client views, and interaction model.

On top of this foundation, **N2 includes additional modules that correspond to the functionality previously offered by Nuido Flow**. For example, the **N2 Trigger** module serves the same purpose as the former **Nuido Trigger**, while leveraging N2’s modernized architecture and unified design.

Together, these components make N2 a flexible, robust platform for building visual automation experiences within Odoo.


## Document Conventions

This documentation uses visual badges to indicate how a node’s parameters are interpreted and processed at runtime. Each parameter may have one or more of the following badges applied to it.

### Parameter Badges

- {{% badge style="raw" %}}Raw{{% /badge %}}: The parameter value is passed through exactly as written, without any evaluation, parsing, or transformation.

- {{% badge style="eval" %}}Eval{{% /badge %}}: The parameter value is fully evaluated with default context and active record info as an expression before it is used. This allows dynamic computation and access to runtime context.

- {{% badge style="patched" %}}Patched{{% /badge %}}: The parameter is interpreted as a model name. One or more methods of the referenced model are patched or overridden before use, altering its behavior at runtime.

- {{% badge style="liteval" %}}Liteval{{% /badge %}}: The parameter is treated as a lightweight expression and evaluated before use. Compared to **Eval**, this evaluation is more restricted and is intended for simple expressions.

- {{% badge style="tmpl" %}}Tmpl{{% /badge %}}: The parameter is treated as a template. It is first parsed and then evaluated, allowing interpolation of variables, expressions, or other dynamic content before being used.

- {{% badge style="inherited" %}}Inherited{{% /badge %}}: The parameter is defined on the parent node and inherited by the node.
