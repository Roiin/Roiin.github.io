- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For each face, this node outputs the integer ID of the Face Set it belongs to. Face Sets are a feature primarily used in Sculpt Mode for quickly masking and organizing parts of a mesh. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Face Set (Socket - Output):** An integer field on the Face domain. Every face within the same sculpted Face Set will share the same ID.
        
    - **Exists (Socket - Output):** A Boolean that is True if the mesh has any Face Sets at all.
        
- **Practical Application:** This node allows you to create custom modeling tools that leverage the intuitive workflow of Sculpt Mode. Imagine you are sculpting an animal and you want to create a tool that procedurally adds fur/hair cards only to specific, painted regions.
    
    1. **The Prep:** In Sculpt Mode, you use the Face Set tools to "paint" different regions onto your animal: one Face Set for the long fur on its back, another for the short fur on its snout, etc.
        
    2. **The Tool:** You create a custom "Add Fur" tool using Geometry Nodes. The user runs the tool in Sculpt Mode.
        
    3. Inside the tool's node graph, you use the Face Set node. Its output gives you the ID for each face.
        
    4. You can use a Compare node to create a Boolean selection where the Face Set ID is equal to the ID of the "long fur" region.
        
    5. Feed this selection into a Distribute Points on Faces node, which is then used to instance your "long hair card" objects. You can repeat this for the "short fur" Face Set, instancing different geometry.
        
    6. The result is a powerful and artistic workflow. The artist can quickly and intuitively block out regions using the freeform painting tools of Sculpt Mode, and then a single click of your custom tool can execute a complex procedural operation based on those painted boundaries.