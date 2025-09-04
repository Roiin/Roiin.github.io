- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Primitives)
    
- **Core Function:** Generates a flat, circular arrangement of vertices and edges, with options to fill the interior with a face.
    
- **Key Properties & Settings:**
    
    - **Vertices (Socket - Input):** The number of vertices in the circle. A value of 3 creates a triangle, 4 a square, etc.
        
    - **Radius (Socket - Input):** The radius of the circle.
        
    - **Fill Type (Property):**
        
        - **None:** Creates only the outer ring of edges.
            
        - **N-Gon:** Fills the interior with a single, circular face.
            
        - **Triangles:** Fills the interior with a fan of triangles meeting at the center.
            
    - **Mesh (Socket - Output):** The generated circular mesh.
        
- **Practical Application:** The Mesh Circle with the 'N-Gon' fill type is the perfect base for creating the iris and pupil of an animal's eye.
    
    1. **The Iris:** Create a Mesh Circle and set the Vertices to a high number like 32 for a smooth circle. This will be the colored part of the eye.
        
    2. **The Pupil:** Create a second Mesh Circle. Make its Radius smaller than the iris's. This will be the black center.
        
    3. **The Assembly:**
        
        - To layer them, you can use a Transform Geometry node to move the pupil slightly forward in space (e.g., a small positive Z value) so it sits on top of the iris.
            
        - Use a Join Geometry node to combine the iris and pupil meshes.
            
    4. **Texturing:** Because a Mesh Circle has radial topology, it's very easy to create procedural textures for it. You can use the Position of the vertices and a Vector Math node set to 'Distance' (from the center) to create a gradient that can be used for coloring. You can also use the atan2() function on the X and Y positions to get an angle, which is perfect for creating the radial streaks seen in an iris.