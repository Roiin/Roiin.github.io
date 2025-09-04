- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Retrieves the data from a named attribute (like a vertex group, UV map, or a custom attribute created with a Store Named Attribute node). It also provides a boolean output to confirm if the attribute actually exists on the geometry.
    
- **Key Properties & Settings:**
    
    - **Name (Socket - Input):** A string input specifying the name of the attribute to be read.
        
    - **Data Type (Property):** A dropdown menu to set the expected type of data (e.g., Float, Vector, Boolean). This helps Blender interpret the data correctly.
        
    - **Attribute (Socket - Output):** The main data output, providing the values of the requested attribute as a field.
        
    - **Exists (Socket - Output):** A boolean that is True if the named attribute was found on the geometry, and False otherwise. This is useful for creating fallback behaviors.
        
- **Practical Application:** This node provides a powerful bridge between manual painting and proceduralism.
    
    1. Start with a plane and go into Weight Paint mode. Create a new vertex group and name it "density_map". Paint some weights onto the plane.
        
    2. In Geometry Nodes, add a Distribute Points on Faces node to scatter points on the plane.
        
    3. Add a Named Attribute node and type "density_map" into its Name field.
        
    4. Connect the Attribute output of this node to the Density input of the Distribute Points on Faces node.
        
    5. The points will now only be scattered in the areas you painted, with the density directly controlled by the strength of your painted weights. This allows you to artistically direct where procedural elements like grass or rocks should appear.