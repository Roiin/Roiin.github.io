- **Editor:** Geometry Node Editor
    
- **Node Group:** Attribute
    
- **Core Function:** Smooths attribute values across a geometry by mixing the value of each element (e.g., vertex) with its immediate neighbors.
    
- **Key Properties & Settings:**
    
    - **Value (Socket):** The input attribute field (e.g., vertex weights, color values) that will be blurred.
        
    - **Iterations (Socket):** An integer that defines how many times the smoothing process is repeated. Higher values result in a more diffused, smoother result.
        
    - **Weight (Socket):** A field that controls the influence of each element's value during the blur calculation.
        
    - **Data Type (Property):** The data type of the attribute being processed (e.g., Float, Vector, Color). This is typically inferred from the Value input.
        
    - **Value (Socket):** The output socket providing the newly calculated, blurred attribute values.
        
- **Practical Application:** A critical tool for creating organic transitions. It can be used to smooth out procedural noise on a landscape to create rolling hills instead of sharp peaks. It is also essential for blending vertex group weights, allowing for smoother transitions between materials or for creating softer deformations in animations. This could be used to create natural-looking erosion effects or blend moss/snow materials onto rock assets based on proximity and orientation.