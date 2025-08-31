- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Get Bone Data
    
- **Core Function:** Retrieves the "Inherit Scale" mode of a bone. This property determines how a bone is affected by the scaling of its parent bone(s).
    
- **Key Properties & Settings:**
    
    - **Armature (Socket):** The armature object to query.
        
    - **Bone Name (Selector):** A dropdown to select the specific bone.
        
    - **Mode (Dropdown Output):** The output socket provides the current "Inherit Scale" setting for the bone (e.g., Full, Aligned, etc.). System Note: While the screenshot shows a generic "Mode" output, this would typically output an Enum or Integer representing the specific mode.
        
    - **Inherit Scale (Socket):** Alternative Output Name. A secondary socket that may output the same data.
        
- **Practical Application:** Used in advanced procedural animation or rigging setups to check a bone's scaling behavior before applying transformations. This allows the logic to adapt to different rig configurations, for example, when creating a system that dynamically attaches scaled props to a character.