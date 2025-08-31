- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Get Bone Data
    
- **Core Function:** Checks whether the "Deform" property of a bone is enabled.
    
- **Key Properties & Settings:**
    
    - **Armature (Socket):** The armature object.
        
    - **Bone Name (Selector):** A dropdown to select the bone.
        
    - **Deform (Socket):** A boolean output which is True if the bone is a deforming bone, and False otherwise.
        
- **Practical Application:** Allows logic to differentiate between control bones (like IK targets) and bones that directly influence the mesh, which can be useful for optimizing or applying specific logic only to relevant parts of a rig.