**Editor:** All Node Editors (when inside a Node Group)  
**Engine(s) Supported:** All  
**Node Group:** N/A (Used to define group inputs)

**Core Function:** This node acts as the entry point for data into a node group. It defines the input sockets that will appear on the exterior of the collapsed Group Node, allowing you to feed information into the internal network from the outside.

**Key Properties & Settings:**

- **Socket Management:** The inputs (sockets) that appear on this node are defined and managed in the **Sidebar** (N key) under the **Group** tab. Here you can add, remove, rename, and reorder the inputs for the parent group.
    
- **Multiple Instances:** You can have multiple Group Input nodes inside the same group. This is purely for organizational purposes, allowing you to place an input connection exactly where it is needed in a complex network, avoiding the need to drag long connection "noodles" across the entire graph.
    

**Practical Application:**  
Continuing the "Custom Metal" node group example: inside the group, you might need to control the base color, the amount of scratches, and the scale of a rust pattern.

1. Inside the node group, go to the Sidebar (N key) > Group > Inputs panel.
    
2. Click the + icon three times to create three new input sockets.
    
3. Select each one and rename them "Base Color," "Scratch Amount," and "Rust Scale," setting their data types appropriately (e.g., Color, Factor, Float).
    
4. These three sockets will now appear on the Group Input node.
    
5. Connect the "Base Color" output from the Group Input node to the Base Color input of the Principled BSDF node inside your group.
    
6. Connect the "Scratch Amount" output to the part of your network that controls the visibility of the scratch texture.
    
7. When you exit the group (Tab), your "Custom Metal" node will now have these three sockets available, allowing for easy control of the material's appearance from the main shader editor.