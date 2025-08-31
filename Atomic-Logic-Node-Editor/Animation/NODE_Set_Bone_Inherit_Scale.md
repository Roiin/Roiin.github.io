- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Set Bone Data
    
- **Core Function:** Sets the "Inherit Scale" mode for a specified bone within an armature's hierarchy. This changes how the bone reacts to the scaling of its parent.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the node.
        
    - **Condition (Socket):** A boolean input; the node only executes if this is True.
        
    - **Armature (Socket):** The armature object containing the bone to modify.
        
    - **Bone Name (Selector):** A dropdown to select the specific bone.
        
    - **Inherit Scale (Dropdown):** In your screenshot, this is labeled None. This is where you would select the desired inheritance mode (e.g., Full, Aligned, None).
        
- **Practical Application:** Used for dynamically altering a rig's behavior at runtime. For example, you could temporarily set a bone's Inherit Scale to None to prevent it from squashing or stretching when a parent bone is scaled for a cartoonish effect, then set it back to Full to restore normal behavior.