- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry
    
- **Core Function:** Combines multiple, separate geometry data-streams into a single, unified output. It can merge different types of geometry (meshes, curves, points, etc.) into one data-stream. This is the primary method for assembling procedural objects from different parts.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** One or more geometry data-streams. New input sockets are created by dragging a connection into the blank socket on the node, allowing you to combine many branches at once.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Attribute & Material Merging:** The node intelligently combines attributes and materials from all inputs. For attributes with the same name but different data types, it up-converts to the more complex type (e.g., a float and a vector will result in a vector).
        
    - **Geometry (Socket - Output):** The single, combined geometry stream.
        
- **Practical Application:** This is the final assembly node for almost any complex procedural object. Imagine you are creating a simple procedural beetle. You would build its parts in separate, parallel branches of your node tree:
    
    1. **Branch 1 (Body):** Create the main abdomen and thorax from a couple of scaled and deformed UV spheres.
        
    2. **Branch 2 (Head):** Create the head and mandibles from smaller primitives.
        
    3. **Branch 3 (Legs):** Create a single leg from a series of extruded curves, then duplicate and transform it to create the other five legs.
        
    
    These three elements exist as independent geometries. To combine them into a single, movable beetle object, you connect the final output of each of these three branches into a single Join Geometry node. The output is now one unified geometry data-stream containing the complete beetle, ready to be passed on for final modifications, like assigning a single chitin material to the entire creature.