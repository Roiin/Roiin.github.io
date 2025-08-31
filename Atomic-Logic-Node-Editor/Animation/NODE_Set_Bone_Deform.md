- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Set Bone Data
    
- **Core Function:** Enables or disables the "Deform" property of a specified bone, which controls whether the bone influences the mesh of the character model.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input.
        
    - **Armature (Socket):** The armature object.
        
    - **Bone Name (Selector):** A dropdown to select the bone.
        
    - **Bool (Socket):** A boolean input. True enables deformation, False disables it.
        
- **Practical Application:** Could be used for optimization by disabling deformation on bones that are not visible to the camera, or for special effects where you want to "detach" a part of a mesh from its underlying bone temporarily.