- **Editor:** Compositor Node Editor
- **Node Group:** Group
    
- **Core Function:** A feature that encapsulates a network of nodes into a single, custom node block. This allows for simplifying complex node trees, creating reusable tools, and sharing functionality across projects.
    
- **Key Properties & Settings:**
    
    - **Creation:** Select a set of nodes and press Ctrl+G.
        
    - **Editing:** Select the group node and press Tab to enter and edit its internal network. Press Tab again to exit.
        
    - **Interface:** The inputs and outputs of the group are defined by connecting internal nodes to the **Group Input** and **Group Output** nodes, respectively. These are managed via the Sidebar (N key -> Group tab).
        
    - **Reusability:** Once created, a node group can be named and found in the Add > Group menu within the Compositor, allowing you to instance your custom tool anywhere.
        
- **Practical Application:** A common professional use of Node Groups is to create a high-quality, reusable "Despill" tool to remove green or blue screen contamination from a foreground element after keying.
    
    1. The core logic for a simple despill is to isolate the spill color (e.g., green), desaturate it, and then add back a compensatory color from the opposite side of the color wheel. This involves several nodes: a **Hue Correct** node to select the green, a **Color Balance** to remove it, and **Mix** nodes to combine it back using the generated mask.
        
    2. Select this entire network of despill logic and press Ctrl+G to create a new group.
        
    3. Tab into the group. Connect the main Image input to the **Group Input** node. Connect the final Image result to the **Group Output** node.
        
    4. To make the tool flexible, you need to expose controls. Connect the Hue value from the **Hue Correct** node to the **Group Input** so the user can select the spill color. Connect the Fac of a **Mix** node to control the overall despill strength.
        
    5. In the Sidebar, name the group "UTIL - Despill" and name its inputs "Image", "Spill Color", and "Amount".
        
    6. Now, in any composite, instead of rebuilding this logic, you can simply go to Add > Group > UTIL - Despill. You have a single, clean node that takes your keyed footage and provides a simple, intuitive interface to solve a complex problem, dramatically speeding up your workflow and ensuring consistency.