- **Editor:** Geometry Node Editor
    
- **Node Group:** Attribute
    
- **Core Function:** Permanently deletes a named attribute from an input geometry.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry from which the attribute will be removed.
        
    - **Name (Socket - Input):** A string input specifying the exact name of the attribute to delete (e.g., "my_vertex_group", "scale").
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Geometry (Socket - Output):** The modified geometry, now without the specified attribute.
        
- **Practical Application:** Primarily used for optimization and data management. After using a complex attribute (e.g., a vertex group named 'growth_mask') to procedurally generate foliage on a mesh, this node can be used to delete the 'growth_mask' attribute. This cleans up the final geometry, reduces memory usage, and prevents the now-unnecessary data from being processed by any subsequent nodes, improving performance.