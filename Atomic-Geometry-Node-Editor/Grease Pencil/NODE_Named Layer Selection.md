- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Grease Pencil (Read)
    
- **Core Function:** Generates a boolean selection that is True for any Grease Pencil layer that has a specific, user-defined name. This is the primary method for isolating and targeting a particular layer for procedural modifications.
    
- **Key Properties & Settings:**
    
    - **Name (Socket - Input):** A string input specifying the name of the layer to select. The match must be exact.
        
    - **Selection (Socket - Output):** A Boolean field that is True for the matching layer(s) and False for all others.
        
- **Practical Application:** This node is essential for applying procedural effects to specific parts of a 2D animated character. Imagine you have a Grease Pencil character with different parts of its body drawn on separate, named layers: "Head", "Torso", "Left_Arm", "Right_Arm".
    
    1. **The Goal:** You want to make only the character's "Head" layer jiggle slightly, as if it were a bobblehead, without affecting the rest of the body.
        
    2. Use the Named Layer Selection node and type "Head" into its Name input.
        
    3. The Selection output is now True only for the head layer.
        
    4. Feed this Selection into a Set Position node. For the Offset, use an animated Noise Texture (driven by Scene Time) to create a subtle, random wiggle.
        
    5. Because the Set Position node is being masked by the selection, only the strokes on the "Head" layer will be displaced by the noise. The "Torso" and "Arms" will remain perfectly still. This allows for precise, non-destructive animation effects targeted at specific, named parts of a drawing.