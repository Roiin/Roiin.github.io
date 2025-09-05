- **Editor:** Compositor Node Editor  
- **Node Group:** Mask
    
- **Core Function:** Generates a complex grayscale gradient that fills the space between two input masks. The gradient is white at the Inner Mask and smoothly fades to black towards the edges of the Outer Mask.
    
- **Key Properties & Settings:**
    
    - **Inner Mask (Socket):** The grayscale mask that defines the "start" of the gradient (the white area).
        
    - **Outer Mask (Socket):** The grayscale mask that defines the "end" or boundary of the gradient (the black area). This mask must be larger than or encompass the inner mask.
        
    - **Inner Edge (Property):** Controls how shapes are handled. All is the standard mode. Adjacent Only is for specific cases where multiple disconnected shapes are involved.
        
- **Outputs:**
    
    - **Mask (Socket):** The final grayscale gradient mask.
        
- **Practical Application:** This node is a problem-solver for creating custom falloffs and gradients that follow specific, non-uniform shapes, which would be difficult or impossible to create with standard gradient or blur nodes.
    
    - **Molecular (Custom Shape Falloff):** This is its primary purpose. Imagine you want to create a glow that is shaped like a star, but has a soft, circular falloff.
        
        1. Create a star-shaped mask (using a Mask node or an image). This is your Inner Mask.
            
        2. Create a larger, circular Ellipse Mask that completely contains the star. This is your Outer Mask.
            
        3. The Double Edge Mask will generate a gradient that is perfectly star-shaped in the center, but smoothly fades out in a circular pattern. This can be used for highly art-directed glows or light effects.
            
    - **Organic (Shoreline / Wet Sand Effect):** To create a procedural mask for wet sand along a shoreline:
        
        1. You have a black-and-white mask of your ocean (Mask A) and a mask of your sand/land (Mask B).
            
        2. Slightly Erode the land mask to create a new, smaller landmass. This will be your Inner Mask. The original, larger landmass will be your Outer Mask.
            
        3. The Double Edge Mask will create a smooth gradient along the coast, running from the dry sand (white) to the water's edge (black).
            
        4. You can use this gradient as a factor to darken and increase the saturation/specularity of the sand texture, creating a perfectly procedural and animatable wet map.
            
    - **Organic (Procedural Veins / Root Systems):**
        
        1. Create a base shape for a leaf or an object. This is your Outer Mask.
            
        2. Create a thinner, branching pattern inside it using procedural textures or other masks. This is your Inner Mask.
            
        3. The Double Edge Mask will create a beautiful gradient that flows from the "veins" outwards to the edge of the leaf, which can be used to drive variations in color or displacement for a very organic look.