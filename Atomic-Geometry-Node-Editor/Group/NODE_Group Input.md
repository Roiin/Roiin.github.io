**Editor:** Geometry Nodes Editor  
**Node Group:** Group

**Core Function:** Exposes parameters from inside a node group to the outside, making them accessible as input sockets on the group node itself and in the modifier interface.

**Key Properties & Settings:**

- **Sidebar Interface:** The inputs are not controlled on the node itself, but in the **Group** tab of the Node Editor's sidebar (N-Panel). Here you can:
    
    - Add new input sockets of any data type.
        
    - Rename, reorder, and remove existing sockets.
        
    - Set default values, tooltips, and minimum/maximum ranges for each input.
        
- **Multiple Nodes:** You can have multiple Group Input nodes within a single group to bring controls to different parts of the node tree, avoiding long, messy connections.
    

**Practical Application:**  
This node is how you create user-friendly controls for a custom procedural asset. Imagine you have built a complex node group that generates a procedural spider. You need a way for a user to easily change the spider's body size without having to go inside the group and find the specific Value node.

- **The Goal:** To create an accessible "Body Size" slider on your main "Procedural Spider" node group.
    
- **The Problem:** The Value node that controls the scale of the spider's abdomen sphere is buried deep inside the complex node network. It is completely inaccessible from the outside.
    
- **The Solution:** You expose this value using the Group Input node.
    
    1. **Inside** your spider node group, find the Group Input node.
        
    2. Locate the Value node that controls the abdomen's scale. Drag a connection from its Value output socket to an empty socket on the Group Input node.
        
    3. Go to the sidebar's **Group** tab. You will see a new input, likely named "Value".
        
    4. Click on its name and change it to "Body Size". You can also set a default value (e.g., 1.0) and a minimum/maximum range to prevent unrealistic sizes.
        

Now, when you exit the group, your main "Procedural Spider" node has a new input slider labeled "Body Size". Changing this value directly controls the internal Value node, allowing for intuitive, high-level control over your procedural asset.