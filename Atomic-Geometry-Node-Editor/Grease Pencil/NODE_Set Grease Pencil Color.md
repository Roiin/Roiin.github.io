- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Grease Pencil (Write)
    
- **Core Function:** Changes the color and/or opacity of Grease Pencil strokes or their fills based on a selection. This is the primary node for procedurally coloring Grease Pencil drawings.
    
- **Key Properties & Settings:**
    
    - **Grease Pencil (Socket - Input):** The source Grease Pencil geometry.
        
    - **Selection (Socket - Input):** A boolean mask. Only the color of selected points or strokes will be changed.
        
    - **Color (Socket - Input):** A color field providing the new color to be applied.
        
    - **Opacity (Socket - Input):** A float field providing the new opacity (alpha) value.
        
    - **Mode (Property):**
        
        - **Stroke:** Applies the color change to the lines themselves.
            
        - **Fill:** Applies the color change to the filled areas inside closed strokes.
            
    - **Grease Pencil (Socket - Output):** The Grease Pencil geometry with the updated colors.
        
- **Practical Application:** This node is perfect for creating dynamic color effects, like the fur on a magical animal that shimmers with shifting colors.
    
    1. First, you draw the animal's fur using many individual Grease Pencil strokes.
        
    2. **The Goal:** You want the color of each stroke to cycle through a rainbow gradient over time.
        
    3. Use the Set Grease Pencil Color node with the Mode set to 'Stroke'.
        
    4. For the Color input, you need an animated color. Use a Color Ramp node to define your rainbow gradient.
        
    5. To make the color change, you need a value to drive the Factor of the Color Ramp. Use a Noise Texture and set its W (4D) input to be driven by the Seconds output of a Scene Time node. This creates an animated, swirling noise pattern.
        
    6. The result is that the Noise Texture provides a different grayscale value to each part of the drawing, which in turn samples a different color from the rainbow gradient. Because the noise is animated through time, these colors will shift and shimmer across the animal's fur, creating a beautiful and complex magical effect with very few nodes.