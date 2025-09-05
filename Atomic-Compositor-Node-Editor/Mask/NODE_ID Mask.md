- **Editor:** Compositor Node Editor  
- **Node Group:** Mask
    
- **Core Function:** **[LARGELY SUPERSEDED]** Creates a black-and-white mask for a specific object or material by using the Object Index or Material Index render pass. It requires manually assigning a numerical ID to objects/materials in the 3D scene.
    
- **Key Properties & Settings:**
    
    - **ID Value (Socket):** The input for the render pass data. This must be connected to the IndexOB (Object Index) or IndexMA (Material Index) output of a Render Layers node.
        
    - **Index (Socket):** The numerical ID of the object or material you want to isolate. This number must match the "Pass Index" you set in the Properties editor for that object or material.
        
    - **Anti-Aliasing (Property Checkbox):** When enabled, it attempts to create a smoother, less jagged edge for the mask.
        
- **Outputs:**
    
    - **Alpha (Socket):** The final black-and-white grayscale mask. It is white for the object with the matching ID and black for everything else.
        
- **Practical Application:** This node has been almost entirely replaced by the modern Cryptomatte system, which is far more flexible, powerful, and easier to use. The primary reason to know this node is for working with older files or in specific edge cases where Cryptomatte is not available.
    
    - **IMPORTANT NOTE:** For all new projects, use the Cryptomatte node. It does not require manual ID assignment, produces superior anti-aliased results, and correctly handles transparency and motion blur.
        
    - **Legacy Workflow (for reference):** The "molecule" for isolating an object was:
        
        1. **In the 3D Scene:** Select your target object. Go to Object Properties -> Relations -> Pass Index and assign it a unique number (e.g., 1). Do this for each object you might want to mask.
            
        2. **In View Layer Properties:** Under Passes, enable Object Index. This will add an IndexOB socket to your Render Layers node.
            
        3. **In the Compositor:** Add an ID Mask node. Connect the IndexOB output from Render Layers to the ID Value input of the ID Mask node.
            
        4. Set the Index value on the ID Mask node to 1 (or whatever number you assigned).
            
        5. The Alpha output will now be a mask of your target object.
            
    - **Limitations Compared to Cryptomatte:** The ID Mask produces hard, aliased edges that are difficult to work with. It does not handle semi-transparent objects or motion blur correctly, often resulting in a "stair-stepped" or incorrect matte in those situations. Each object needs a manually assigned, unique ID, which is tedious to manage in large scenes.