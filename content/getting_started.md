+++
title = "Getting Started"
description = "A step-by-step guide to installing N2 and creating your first graph"
weight = 20
date = "2025-12-12T01:46:39.298Z"
+++

This guide walks you through installing **N2**, unlocking access, and building your very first graph.
You can be fully up and running in just a few minutes.

## Quick Start

Follow these steps to install N2 and prepare your Odoo environment.

1. **Log in to GitHub**

    Ensure you’re signed into the GitHub account you want to use with N2.

2. **Star the Repository**

    Visit **Exploring Odoo** at: https://github.com/yonitjio/exploring-odoo

    Click the **⭐ Star** button (top-right).
    N2 uses this star to verify access—downloads remain locked until the repo is starred.

3. **Sign in to N2**

    Go to **https://nuido2.skysize.io** and click **“Continue with GitHub”.**
    Once your GitHub account has starred the repo, N2 automatically unlocks full access to the modules.

4. **Download the N2 Modules**

    Download both required N2 packages:

    - **N2 Core Module**
    https://nuido2.skysize.io/shop/n2-3
    - **N2 User Interface Module**
    https://nuido2.skysize.io/shop/n2-user-interface-4

    > [!NOTE]
    > Both modules are required for N2 to function.

5. **Install the Modules in Odoo**

    1. Extract both ZIP files into your Odoo **custom addons** directory.
    2. Activate **Developer Mode** in Odoo.
    3. Go to **Apps → Update Apps List**.
    4. Search for “N2” and install both:
    - **N2**
    - **N2 User Interface**

    > [!TIP]
    > If the N2 modules don’t appear after updating the Apps list, make sure you extracted them to the correct custom addons directory, then restart your Odoo instance.

Once both modules are installed, N2 becomes fully available in your system.

## Creating Your First Graph

With N2 installed, you’re ready to build your first graph.

1. **Access the N2 Menu**

    A new **N2** entry now appears in your Odoo main menu.

    {{< figure
    src="../images/getting_started/n2-menu.png"
    alt="N2 menu item in Odoo"
    caption="N2 menu location"
    width="150"
    >}}

2. **Open the Graphs List**

    Click **N2** to open the list of available graphs.
    On a fresh installation, this list will be empty.

{{< figure
src="../images/getting_started/n2-list-view.png"
alt="Empty N2 graphs list"
caption="Graphs list view"
width="100%"
>}}

3. **Launch the Designer**

    Click the **Designer** button to open the N2 visual editor.

{{< figure
src="../images/getting_started/n2-designer.png"
alt="Empty designer workspace"
caption="Clean canvas ready for your first graph"
width="100%"
>}}

4. **Add a Start Node**

    1. In the left sidebar, type **`start`** in the search field.
    2. Drag **StartNode** onto the canvas.

    Every executable N2 graph must contain **exactly one** StartNode—it defines where the execution begins.

5. **Save Your Graph**

    Click **Save** on the toolbar, enter a name (e.g., *Hello World*), and confirm.
    Your new graph is now stored in Odoo.

6. **Process & Run**

    1. Click **Process** to validate and compile the graph.
    2. Click **Run** to execute it.

    A graph with only a StartNode will complete instantly—but you’ve now verified that everything is working.

## 🎉 Congratulations!

You’ve successfully installed N2 and created your very first graph.
From here, you can begin adding nodes, building logic, and automating workflows with the N2.

You're off to a great start—happy building!
