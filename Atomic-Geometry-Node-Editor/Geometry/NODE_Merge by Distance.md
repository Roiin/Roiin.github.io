- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Scans the input geometry and merges any selected points/vertices that are within a specified distance of each other, effectively welding them together. This is the procedural equivalent of the "Merge by Distance" tool in Edit Mode.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source mesh or point cloud to be processed.
        
    - **Selection (Socket - Input):** A boolean mask. Only vertices where this is True will be considered for merging.
        
    - **Distance (Socket - Input):** A float value that sets the maximum distance for two vertices to be considered "close enough" to merge.
        
    - **Mode (Property):**
        
        - **All:** Any two selected vertices within the distance threshold will be merged, even if they belong to separate, unconnected parts of the mesh.
            
        - **Connected:** Only merges vertices that are part of the same contiguous mesh island. This is useful for preventing separate objects from accidentally being welded together.
            
    - **Geometry (Socket - Output):** The cleaned-up geometry with the vertices merged.
        
- **Practical Application:** This node is invaluable when converting text into a 3D mesh for signs, logos, or titles.
    
    1. You start with a String to Curves node to generate your text, then a Fill Curve node to turn it into a flat mesh.
        
    2. **The Problem:** With many fonts, especially cursive or bold styles, the letters overlap. This creates messy, intersecting geometry with duplicate vertices, which can cause ugly shading artifacts (Z-fighting) and prevent operations like beveling from working correctly.
        
    3. **The Solution:** Place a Merge by Distance node immediately after the Fill Curve node.
        
    4. Set a very small Distance value (e.g., 0.001).
        
    5. The node will automatically find and weld all the overlapping vertices where the letters intersect, cleaning up the topology and creating a single, unified mesh. The shading artifacts disappear, and the resulting clean mesh is now ready for further procedural modeling, like being extruded to add thickness or beveled to add nice highlights.