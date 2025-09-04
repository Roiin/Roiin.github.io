- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Grease Pencil (Write)
    
- **Core Function:** Sets the softness factor for Grease Pencil strokes, controlling the blurriness or fade-out at the edges of the lines themselves.
    
- **Key Properties & Settings:**
    
    - **Grease Pencil (Socket - Input):** The source Grease Pencil geometry.
        
    - **Selection (Socket - Input):** A boolean mask. The softness will only be changed on selected stroke points.
        
    - **Softness (Socket - Input):** A float field providing the new softness value. A value of 0.0 results in a crisp, hard-edged stroke. Higher values create a softer, more blurred or transparent edge.
        
    - **Grease Pencil (Socket - Output):** The Grease Pencil geometry with the updated stroke softness.
        
- **Practical Application:** This node is perfect for creating atmospheric effects like distant, misty outlines in a landscape drawing.
    
    1. Imagine a 2D drawing of a mountain range with peaks in the foreground and peaks in the background, drawn on separate layers named "Foreground_Peaks" and "Background_Peaks".
        
    2. **The Goal:** You want the background peaks to look hazy and distant, while the foreground peaks remain sharp and clear, creating a sense of atmospheric perspective.
        
    3. Use the Named Layer Selection node to create a selection for the "Background_Peaks" layer.
        
    4. Feed this selection into the Set Grease Pencil Softness node.
        
    5. Provide a Value (e.g., 0.2) to the Softness input.
        
    6. The result is that only the strokes on the "Background_Peaks" layer will be softened. They will appear slightly blurred and less distinct, effectively pushing them into the background and creating a powerful illusion of depth in your 2D artwork.