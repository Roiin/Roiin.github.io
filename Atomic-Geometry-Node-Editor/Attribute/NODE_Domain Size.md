- **Editor:** Geometry Node Editor
    
- **Node Group:** Geometry
    
- **Core Function:** Outputs the total number of elements for a selected component type (e.g., points, edges, faces) on an input geometry.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket):** The geometry whose components will be counted.
        
    - **Component (Property):** A dropdown selector to specify which geometry component to count (Points, Edges, Faces, etc.).
        
    - **Point Count (Socket):** Outputs the total number of points (vertices) in the geometry.
        
    - **Edge Count (Socket):** Outputs the total number of edges in a mesh.
        
    - **Face Count (Socket):** Outputs the total number of faces in a mesh.
        
    - **Face Corner Count (Socket):** Outputs the total number of face corners in a mesh.
        
    - **Spline Count (Socket):** Outputs the total number of splines in a curve object.
        
    - **Instance Count (Socket):** Outputs the total number of top-level instances.
        
- **Practical Application:** Can be used to make procedural systems responsive to mesh density. For example, connecting the Face Count to a Map Range node to automatically adjust the level of detail or the density of scattered objects based on how complex the input mesh is. It's a key node for creating adaptive and scalable geometry tools.