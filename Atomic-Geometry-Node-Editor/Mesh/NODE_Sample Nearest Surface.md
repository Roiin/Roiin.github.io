- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Sample)
    
- **Core Function:** For a given set of sample positions, this node finds the closest point on the surface of a target mesh and retrieves the value of a specified attribute at that location. It is a powerful tool for transferring attributes between two independent geometries based on proximity.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to read the attribute data from.
        
    - **Value (Socket - Input):** The attribute or field on the source mesh that you want to read (e.g., its vertex color, or a custom attribute).
        
    - **Sample Position (Socket - Input):** The point(s) in space from which to start the search.
        
    - **Data Type (Property):** The type of data you are expecting to retrieve (e.g., Color, Vector, Float).
        
    - **Value (Socket - Output):** The primary output; the value of the sampled attribute from the closest point on the source mesh's surface.
        
    - **Is Valid (Socket - Output):** A Boolean that is True if a valid surface point was found.
        
- **Practical Application:** This node is perfect for making instanced geometry aware of the surface it's being placed on. Imagine you have a large, lumpy animal model with a procedural color pattern (e.g., green skin with brown patches) created in the Shader Editor and stored as a vertex color attribute named "skin_color". You now want to instance spikes on its back, and you want the base of each spike to match the color of the skin directly underneath it.
    
    1. First, distribute points on the animal's back where you want to place the spikes.
        
    2. Use the Instance on Points node to place your spike models.
        
    3. **The Problem:** The spikes have their own material and don't match the skin's color pattern.
        
    4. **The Solution:**
        
        - Use the Sample Nearest Surface node. The Mesh input is your animal model. The Value you want to read is its "skin_color" attribute. The Sample Position is the position of each of the points where you are instancing the spikes.
            
        - The Value output of this node is now a color field, where each color is the skin color directly underneath each spike.
            
        - Store this color as a named attribute on the instances (e.g., "base_color").
            
        - In the spike's own shader, use an Attribute node to retrieve "base_color" and plug it into the Base Color of your Principled BSDF.
            
    5. The result is a seamless blend. The base of each spike perfectly matches the procedural color pattern of the skin, making it look like the spike is a natural growth from the creature's body.