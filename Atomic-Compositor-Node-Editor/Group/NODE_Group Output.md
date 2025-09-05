- **Editor:** Compositor Node Editor
- **Node Group:** Group
    
- **Core Function:** Serves as the exit point for data from a custom node group, defining the final image, value, or mask that the group will provide to the rest of the node tree.
    
- **Key Properties & Settings:**
    
    - **Sockets (Input):** This node has no fixed sockets. Its input sockets are dynamically created and defined in the Sidebar's Group tab when editing a node group. Each socket you create here becomes an output on the exterior of the group node.
        
- **Practical Application:** Continuing with the custom "Lightwrap" effect from the **Group Input** example, the **Group Output** node is used to deliver the final composited image and, optionally, a utility pass.
    
    1. Inside the "Lightwrap" node group, you have a final **Mix (Screen)** node that layers the calculated light spill over the original foreground element.
        
    2. Take the Image output from this final **Mix** node and connect it to the default input socket on the **Group Output** node.
        
    3. Now, press N to open the Sidebar and go to the Group tab. Rename this output from the default "Image" to a more descriptive "FG_Wrapped".
        
    4. It can be useful to also output the raw lightwrap effect itself for further grading. Drag a connection from the output of the **Keying** node (which is just the light spill mask) to the empty socket at the bottom of the **Group Output** node.
        
    5. In the Sidebar, a new output will appear. Name this one "Wrap_Mask".
        
    6. Now, when you "tab out" to view your custom node from the outside, it will have two outputs: FG_Wrapped, which delivers the final result, and Wrap_Mask, which provides the isolated light effect as a separate element for advanced compositing adjustments.