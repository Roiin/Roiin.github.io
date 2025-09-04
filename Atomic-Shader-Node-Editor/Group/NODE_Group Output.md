**Editor:** All Node Editors (when inside a Node Group)  
**Engine(s) Supported:** All  
**Node Group:** N/A (Used to define group outputs)

**Core Function:** This node is the counterpart to the Group Input node. It defines the exit points for data, creating the output sockets that will appear on the exterior of the collapsed Group Node. This allows the result of the internal node network to be passed on to the rest of the main node tree.

**Key Properties & Settings:**

- **Socket Management:** Similar to the Group Input node, the output sockets are managed in the **Sidebar** (N key) under the **Group** tab. You can add, remove, rename, and reorder the outputs for the parent group.
    
- **Multiple Instances:** For better organization within a large node group, you can add multiple Group Output nodes. This allows you to place an output connection right where the data is generated, preventing long, confusing connection lines back to a single output node.
    

**Practical Application:**  
In your "Custom Metal" node group, the primary result is the final shader. However, you might also want to output a mask for the rust pattern, in case you want to use it for something else in the main shader tree (like affecting displacement).

1. Inside the node group, go to the Sidebar (N key) > Group > Outputs panel.
    
2. By default, there might be one output. Rename it to "Shader." If not, create one.
    
3. Click the + icon to add a second output and name it "Rust Mask." Set its data type to a grayscale Factor.
    
4. Connect the final output of your Principled BSDF (or whatever the last shader node is) to the "Shader" input on the Group Output node.
    
5. Find the part of your node network that generates the black-and-white texture for the rust and connect it to the "Rust Mask" input on the Group Output node.
    
6. When you exit the group (Tab), your "Custom Metal" node will now have two outputs: "Shader" (to be connected to the Material Output) and "Rust Mask" (which can now be used to drive other effects in your main node tree).