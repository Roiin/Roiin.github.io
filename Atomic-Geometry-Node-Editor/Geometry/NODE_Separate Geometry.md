- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Acts as a filter, splitting a single geometry into two separate outputs based on a boolean Selection. Elements where the selection is True go to one output, and elements where it is False go to the other.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry to be split.
        
    - **Selection (Socket - Input):** A boolean field that acts as the sorting criteria.
        
    - **Domain (Property):** The element type (Point, Edge, Face, Spline) that the Selection is evaluated on.
        
    - **Selection (Socket - Output):** The part of the geometry where the Selection input was True.
        
    - **Inverted (Socket - Output):** The part of the geometry where the Selection input was False.
        
- **Practical Application:** This node is perfect for applying different procedural effects to different parts of the same mesh. Imagine you have a model of an animal, like a zebra, and you want to procedurally create its fur, with black fur for the stripes and white fur for the other areas.
    
    1. First, you use a Noise Texture or Wave Texture to create a black and white pattern across the animal's skin. You use a Color Ramp to make this pattern a sharp, binary mask. This Boolean mask will be your Selection.
        
    2. Feed the animal's mesh into the Separate Geometry node with the Domain set to 'Face'.
        
    3. The Selection output now contains only the "stripe" faces, and the Inverted output contains only the "white" faces.
        
    4. You can now treat these two geometry streams completely independently.
        
        - On the "stripe" geometry, you use Distribute Points on Faces and instance short, black fur curves.
            
        - On the "white" geometry, you do the same but instance slightly longer, white fur curves.
            
    5. Finally, use a Join Geometry node to combine both fur systems. The result is a single, cohesive fur coat that perfectly matches the procedural stripe pattern, all made possible by splitting the base mesh into two distinct logical parts.