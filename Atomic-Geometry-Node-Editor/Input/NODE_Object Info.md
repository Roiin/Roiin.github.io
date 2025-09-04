- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Imports a selected object's data from the scene, providing its geometry and transform information to the node tree.
    
- **Key Properties & Settings:**
    
    - **Object (Socket - Input):** The source object to get information from.
        
    - **As Instance (Property):** A boolean. If True, outputs the entire object as a single, lightweight instance. If False, outputs its raw, realized geometry.
        
    - **Transform Space (Property):** A dropdown to control how the object's transform is interpreted ('Original' or 'Relative').
        
    - **Transform (Socket - Output):** A 4x4 matrix containing the object's full location, rotation, and scale.
        
    - **Location (Socket - Output):** The world-space position of the object's origin.
        
    - **Rotation (Socket - Output):** The world-space rotation of the object.
        
    - **Scale (Socket - Output):** The world-space scale of the object.
        
    - **Geometry (Socket - Output):** The object's geometry data, with all of its modifiers applied.
        
- **Practical Application:** This node is commonly used to create interactive controllers. For example, you can add an Empty to your scene and reference it with the Object Info node. By taking the Location output of the Empty and calculating the distance to the points of your main geometry, you can create a proximity effect. This distance value could then be used to scale down instances or mask a displacement effect, creating a circular 'safe zone' or a ripple effect that follows the Empty as you move it in the viewport.