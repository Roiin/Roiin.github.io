- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Get Bone Data
    
- **Core Function:** Checks whether a bone is "Connected" to its parent. A connected bone's head is locked to the tail of its parent bone, forming a continuous chain.
    
- **Key Properties & Settings:**
    
    - **Armature (Socket):** The armature object to query.
        
    - **Bone Name (Selector):** A dropdown to select the specific bone.
        
    - **Bool (Socket):** A boolean output which is True if the bone is connected to its parent, and False otherwise.
        
    - **Connected (Socket):** Alternative Output Name. A secondary socket that may output the same boolean data.
        
- **Practical Application:** Useful for dynamically analyzing a rig's structure. For example, a script could traverse an armature to find the end of a "chain" by checking for the first bone where Connected is False.