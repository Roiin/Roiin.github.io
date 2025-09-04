- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** Procedurally shortens each spline by "trimming" sections off its start and/or end, creating a new, shorter curve while preserving the shape of the remaining segment. **Warning: This node does not currently support cyclic (closed) splines.**
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be trimmed.
        
    - **Selection (Socket - Input):** A boolean mask. Only splines where this is True will be trimmed.
        
    - **Start (Socket - Input):** The new starting point of the curve.
        
    - **End (Socket - Input):** The new ending point of the curve.
        
    - **Mode (Property):** Determines how the Start and End values are interpreted:
        
        - **Factor:** Uses a normalized 0-to-1 value representing the percentage of the spline's total length. For example, a Start of 0.1 and an End of 0.8 keeps the middle 70% of the curve.
            
        - **Length:** Uses absolute distance units measured from the beginning of the spline. For example, a Start of 2.0 and an End of 5.0 keeps the segment of the curve between the 2-meter and 5-meter marks.
            
    - **Curve (Socket - Output):** The new, trimmed curve.
        
- **Practical Application:** This node is the primary method for creating "growing" or "drawing" effects with curves. Imagine you want to animate a vine growing up a wall.
    
    1. First, you model the final, complete path of the vine as a single, static curve.
        
    2. Insert the Trim Curve node. Set its Mode to 'Factor' and leave the Start value at 0.0.
        
    3. To animate the growth, you need to drive the End value over time. Use a Scene Time node and feed its Frames or Seconds output into a Map Range node.
        
    4. Configure the Map Range node to map your desired animation duration (e.g., from frame 1 to frame 100) to a Factor range (from 0.0 to 1.0).
        
    5. Connect the output of the Map Range node to the End input of the Trim Curve node.
        
    6. Finally, use a Curve to Mesh node on the output of the Trim Curve node to give the vine thickness.
        
    7. The result is a perfect animation: as the timeline plays, the End value increases, progressively revealing more of the curve. The Curve to Mesh node generates geometry on this growing curve, creating the illusion of a vine magically growing along its predefined path.