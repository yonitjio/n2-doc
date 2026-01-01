+++
title = "Automatic Layout"
weight = 20
description = "N2 Elk: Automatic Layout for N2"
date = "2025-12-12T01:46:39.298Z"
+++

This module extends N2 by integrating **elk-js** to automatically compute and apply layout arrangements for workflow diagrams. This module improves readability by organizing nodes and connections, especially in large or complex workflows.

This module does not add new nodes to N2.

## Known Issue
Because N2 uses a layout approach that **elk-js** does not natively support—specifically, allowing multiple graph directions on the same layer without grouping—a workaround is required to enable auto-layout. Due to this limitation, highly complex graphs or workflows may not be arranged correctly. In some cases, the module may be unable to compute a valid layout and may raise an exception. This behavior stems from the inherent differences between N2’s flexible structure and ElkJS’s layout constraints.