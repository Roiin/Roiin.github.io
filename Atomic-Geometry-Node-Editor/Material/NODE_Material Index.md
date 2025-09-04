- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Material
    
- **Core Function:** For each face in a mesh, this node outputs an integer representing the index of the material assigned to it. The index corresponds to the material's position in the object's material slot list (starting from 0).
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Material Index (Socket - Output):** An integer field on the Face domain, where each value is the material slot index for that face.
        
- **Practical Application:** This node is essential for creating procedural effects that are guided by pre-existing material assignments. Imagine you have a model of an animal that has already been manually textured with two materials: "Fur" (in slot 0) and "Claws" (in slot 1).
    
    1. **The Goal:** You want to procedurally add extra geometry, like a magical glow, but only on the parts of the model that have the "Claws" material.
        
    2. Use the Material Index node. This will output 0 for all the "Fur" faces and 1 for all the "Claws" faces.
        
    3. Use a Compare node to create a Boolean selection where the Material Index is equal to 1.
        
    4. This selection now perfectly isolates all the faces that make up the claws.
        
    5. You can now use this selection to drive another procedural effect. For example, you could Separate Geometry using this selection to isolate the claw mesh, then Duplicate Elements and scale it slightly to create a glowing outline around just the claws, leaving the fur untouched. The Material Index node allowed you to translate the artist's manual material setup into a precise procedural mask.