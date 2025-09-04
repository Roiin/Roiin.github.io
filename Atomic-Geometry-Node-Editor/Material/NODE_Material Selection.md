- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Material
    
- **Core Function:** For a given material, this node generates a Boolean selection that is True for every face that has that specific material assigned to it.
    
- **Key Properties & Settings:**
    
    - **Material (Socket - Input):** The material to search for, typically provided by a Material input node.
        
    - **Selection (Socket - Output):** A Boolean field on the Face domain that is True for all faces assigned the specified material.
        
- **Practical Application:** This node is a more user-friendly way to create selections based on materials, perfect for a group input. Imagine you are building a "Procedural Spikes" node group that you want to be reusable on any creature.
    
    1. **The Goal:** The node group should add spikes to a specific part of a creature's body, for example, the parts covered in "Armor" plating.
        
    2. Instead of forcing the user to know the exact material index for their armor, you can provide a more intuitive control.
        
    3. In your node group, create a Group Input with a Material socket. Label it "Target Material for Spikes".
        
    4. Use the Material Selection node. Connect this new "Target Material" input to its Material socket.
        
    5. The Selection output is now a mask for the material the user has chosen. You can feed this directly into the Selection input of a Distribute Points on Faces node to scatter your spikes.
        
    6. **The Result:** You have a flexible and user-friendly tool. An artist can now take your node group, apply it to their creature, and in the modifier panel, simply pick their "Armor" material from the dropdown list. The spikes will instantly and correctly appear only on the armor-plated sections, without the artist needing to worry about the underlying material slot numbers.