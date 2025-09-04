- **Editor:** Geometry
    
- **Node Group:** Curve (Write)
    
- **Core Function:** Directly modifies the position of the left or right handles of a Bézier curve's control points, allowing for procedural shaping and animation of the curve's curvature.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The Bézier curve geometry to be modified.
        
    - **Selection (Socket - Input):** A Boolean mask. Only the handles of selected control points will be affected.
        
    - **Position (Socket - Input):** A vector field defining the absolute new position for the handles in local space.
        
    - **Offset (Socket - Input):** A vector field defining a relative translation to be added to each handle's current position.
        
    - **Mode (Property):** A toggle to choose whether you are modifying the Left handle or the Right handle. You cannot modify both simultaneously with a single node.
        
    - **Curve (Socket - Output):** The curve, now with its handles repositioned and its shape updated.
        
- **Practical Application:** This node is ideal for animating the shape of a curve over time. Imagine you are creating a stylized 2D animation of a sleeping cat, and you want its belly, defined by a Bézier curve, to gently rise and fall as it breathes.
    
    1. Create a simple Bézier curve with a control point at the peak of the cat's belly.
        
    2. To make the belly rise and fall, you need to move the handles of this control point up and down.
        
    3. Use two Set Handle Positions nodes, one set to Left and one to Right.
        
    4. To create the breathing motion, use a Scene Time node and feed its Seconds output into a Math node set to 'Sine'. This creates a smooth, looping value.
        
    5. Use a Combine XYZ node to create a vector where the Y component is driven by this sine wave (e.g., [0, sine_wave, 0]). This is your Offset vector.
        
    6. Plug this Offset vector into both of your Set Handle Positions nodes.
        
    7. When you play the animation, the handles of the belly curve will now move up and down in a smooth, rhythmic cycle. If you use Fill Curve on this animated curve, you will have a 2D shape of a cat's belly that realistically appears to be breathing.