**Editor:** Geometry Nodes Editor  
**Node Group:** Group

**Core Function:** Passes data from inside a node group to the outside, making it available as an output socket on the group node.

**Key Properties & Settings:**

- **Sidebar Interface:** Like the Group Input, the outputs are managed in the **Group** tab of the Node Editor's sidebar (N-Panel). Here you can add, rename, and manage all the output sockets.
    
- **Multiple Outputs:** You can create several distinct outputs. For example, a single "Procedural Tree" group could have one output for the trunk geometry and a separate output for the leaf geometry.
    
- **Multiple Nodes:** You can use multiple Group Output nodes within the same group to send out data from different logical points in your node tree, keeping it organized.
    

**Practical Application:**  
This node is essential for delivering the final result of your procedural generation. Continuing the "Procedural Spider" example, you need to output the final, assembled spider mesh.

- **The Goal:** To make the complete spider geometry (body, legs, eyes) available as a single mesh output on your "Procedural Spider" node.
    
- **The Problem:** The final Join Geometry node that combines all the spider's parts is the last step inside the group. Its result is trapped within the group and cannot be connected to anything else in the scene.
    
- **The Solution:** You pass the final mesh to the Group Output node.
    
    1. **Inside** your spider node group, locate the final Join Geometry node.
        
    2. Drag a connection from its Geometry output socket to an empty socket on the Group Output node.
        
    3. Go to the sidebar's **Group** tab. You will see a new output, likely named "Geometry".
        
    4. Rename it to "Spider Mesh" for clarity.
        

When you exit the group, your "Procedural Spider" node now has a "Spider Mesh" output socket. You can connect this to the final Group Output of your entire scene to render the spider, or you could connect it to other nodes for further processing (e.g., to a Set Material node).