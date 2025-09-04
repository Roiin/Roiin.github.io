- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Converts 3D curve objects into 2D Grease Pencil strokes, creating a new Grease Pencil object. Attributes like radius on the curve are translated into the thickness of the resulting strokes.
    
- **Key Properties & Settings:**
    
    - **Curves (Socket - "Input"):** The source curve geometry to be converted.
        
    - **Selection (Socket - Input):** A Boolean mask to select which curves or instances will be converted.
        
    - **Instances as Layers (Socket - Input):** A Boolean. If True, each input instance will be converted into a separate layer within the Grease Pencil object. If False, all curves are merged into a single layer.
        
    - **Grease Pencil (Socket - "Output"):** The resulting Grease Pencil object.
        
- **Practical Application:** This node is excellent for creating stylized, hand-drawn effects based on 3D motion, like the magical trail from a wizard's staff.
    
    1. First, attach an Empty to the tip of an animated wizard staff. Use the "Bake to Action" or a similar tool to generate a motion path for this Empty, which creates a 3D curve that perfectly traces its movement.
        
    2. **The Goal:** You want this path to look like a sparkly, hand-drawn ink stroke.
        
    3. Use the Curves to Grease Pencil node on this motion path curve.
        
    4. To give the trail a dynamic, tapered look, use a Set Curve Radius node on the curve before converting it. Drive the radius with the curve's Spline Parameter to make the stroke thinner at the end.
        
    5. The output is a Grease Pencil object. You can now apply Grease Pencil's own powerful effect modifiers to it, like 'Noise' to make the line wobbly and hand-drawn, or 'Dot Dash' to add sparkles, creating a final look that is much more stylized than a standard 3D mesh render.