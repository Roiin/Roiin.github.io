- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** Generates a Boolean selection that is True for any Bézier curve control point whose handles match a specified type (e.g., Aligned, Vector, Free).
    
- **Key Properties & Settings:**
    
    - **Mode (Property):** Determines whether to check the Left handle, the Right handle, or if either (Both) matching the type is sufficient to make the selection True.
        
    - **Handle Type (Property):** A dropdown to select the handle type to search for (Free, Aligned, Vector, Auto).
        
    - **Selection (Socket - Output):** The primary output; a Boolean field that is True for control points that match the criteria.
        
- **Practical Application:** This node is great for creating procedural geometry that respects artist-defined joints and corners. Imagine you are rigging a simple robotic arm using a single Bézier curve, where each control point represents a joint.
    
    1. In Edit Mode, you set the handle type for the "shoulder" and "elbow" joints to 'Aligned' to create smooth, swooping motions. However, for the "gripper" at the end, you set the handle type to 'Vector' to create a sharp, mechanical corner.
        
    2. In your Geometry Nodes setup, you want to instance a large, smooth, rounded joint housing at the smooth joints, and a smaller, squared-off joint housing at the sharp corners.
        
    3. Use two Handle Type Selection nodes:
        
        - The first is set to 'Aligned'. Its Selection output is True only at the shoulder and elbow.
            
        - The second is set to 'Vector'. Its Selection output is True only at the gripper.
            
    4. You can use these two separate Boolean selections to drive the Selection input of two different Instance on Points nodes. The first instances a sphere (for the rounded housing) at the 'Aligned' points, and the second instances a cube (for the squared housing) at the 'Vector' points.
        
    5. This allows the procedural rigging to automatically adapt to the artistic intention defined by the curve's handle types, intelligently choosing the correct type of geometry for each joint.