- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Write)
    
- **Core Function:** Changes the handle type (e.g., to Free, Aligned, Vector, or Auto) for selected control points on a Bézier curve, allowing procedural control over the smoothness or sharpness of its corners.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The Bézier curve geometry to be modified.
        
    - **Selection (Socket - Input):** A boolean mask. The handle type will only be changed on control points where this is True.
        
    - **Mode (Property):** A toggle to choose whether you are modifying the Left handle, the Right handle, or Both.
        
    - **Handle Type (Property):** A dropdown menu to select the new handle type that will be applied.
        
    - **Curve (Socket - Output):** The curve, now with its handle types updated.
        
- **Practical Application:** This node is perfect for creating procedural assets that need a mix of sharp and smooth corners, like an arched window frame.
    
    1. Start with a simple 4-point Bézier curve that forms a basic arch shape: two points at the bottom, two at the top.
        
    2. By default, all handles might be 'Auto', creating a soft, rounded arch.
        
    3. **The Goal:** You want the two bottom corners to be sharp, 90-degree angles, while the top of the arch remains a smooth curve.
        
    4. You need a selection for just the bottom two points. You can do this by selecting them based on their Z position (if Z is close to 0, select True).
        
    5. Feed this Boolean selection into the Selection input of the Set Handle Type node.
        
    6. Set the Handle Type property to 'Vector'.
        
    7. The result is that the node will only affect the bottom two points, changing their handles to 'Vector', which creates sharp, straight-line corners. The top two points are unaffected and remain smooth. Now, when you use Curve to Mesh to create the frame, it will have a proper architectural look with a solid base and a gracefully curved top.