- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Get Bone Data
    
- **Core Function:** Checks whether the "Inherit Rotation" property of a bone is enabled. This determines if the bone will rotate along with its parent bone.
    
- **Key Properties & Settings:**
    
    - **Armature (Socket):** The armature object to query.
        
    - **Bone Name (Selector):** A dropdown to select the specific bone.
        
    - **Bool (Socket):** A boolean output which is True if the bone inherits rotation, and False otherwise.
        
    - **Inherit Rotation (Socket):** Alternative Output Name. A secondary socket that may output the same boolean data.
        
- **Practical Application:** Crucial for creating rigs where some bones need to maintain a specific world orientation regardless of parent movement (e.g., a "look-at" control bone for eyes) or for debugging complex armature behaviors.