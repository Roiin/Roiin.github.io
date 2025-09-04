- **Editor:** Geometry Node Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Outputs a static Boolean value (True or False), acting as a simple on/off switch within the node tree.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Checkbox (Property):** A single checkbox directly on the node interface that sets the output. Checked represents True, and unchecked represents False.
        
    - **Boolean (Socket - Output):** The selected True or False value.
        
- **Practical Application:** This is a fundamental control node. It's used as a simple toggle for procedural systems, often connected to a Switch node to choose between two different geometry or data paths. A procedural asset could have an exposed Boolean input in the modifier panel labeled "Enable Battle Damage." When checked (True), it activates a set of nodes that add dents and scratches; when unchecked (False), it bypasses them, providing a clean version of the asset.