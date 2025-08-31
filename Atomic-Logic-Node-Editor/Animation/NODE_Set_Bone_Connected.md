- **Editor:** Logic Node Editor
    
- **Node Group:** Animation > Set Bone Data
    
- **Core Function (Intended):** This node is intended to dynamically connect or disconnect a bone from its parent's tail. Connecting a bone (True) locks its head to its parent's tail, while disconnecting it (False) allows it to be moved independently.
    
- **System Note on Error:** In your provided UPBGE 0.44.0 build, this specific node is **non-functional and produces a TypeError**. The error message enum "connected" not found indicates that the underlying Blender/UPBGE property this node is trying to access is either named incorrectly in the node's code, has been removed, or is read-only at runtime. Therefore, while its purpose is clear from its name, it cannot be used in your current version.
    
- **Practical Application (Intended):** The intended use is for advanced dynamic rigging, such as creating a "sticky" effect where a character's hand bone could be temporarily disconnected from the arm to "stick" to a wall, and then reconnected once the character moves away.