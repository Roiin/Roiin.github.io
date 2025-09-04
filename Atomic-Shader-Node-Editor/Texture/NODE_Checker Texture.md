**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a classic, two-color checkerboard pattern composed of alternating squares.

**Key Properties & Settings:**

- **Color (Output):** The full-color checkerboard pattern, using Color 1 and Color 2.
    
- **Factor (Output):** A powerful black-and-white mask where one set of squares is white and the other is black. This is essential for driving other effects or mixing other nodes.
    
- **Color 1 / Color 2:** The two alternating colors that make up the pattern.
    
- **Scale:** Controls the frequency or size of the squares. Higher values result in smaller, more numerous squares across the surface.
    
- **Vector:** Input for the texture coordinate system (e.g., from a Texture Coordinate node). Defaults to Generated coordinates if left unconnected.
    

**Practical Application:**  
This node's true power lies in using its Factor output as a mask to control other procedural effects. It is perfect for creating a parquet floor with alternating **wood grain**.

The problem is that a single wood texture applied to a floor will have the grain running in only one direction, which looks artificial for a parquet floor where tiles are laid perpendicularly. You need a way to rotate the wood grain on every other tile. The Checker Texture is the ideal solution.

1. Create your procedural wood grain texture. A common method is using a Noise Texture stretched along one axis with a Mapping node. This will be your "Grain A".
    
2. Duplicate the Mapping node and set its Z-axis rotation to 90 degrees. This will create your perpendicular "Grain B".
    
3. Add a Mix Color node to blend between the two wood grain textures. Plug "Grain A" into the top slot and "Grain B" into the bottom.
    
4. Add a Checker Texture node. Connect its Factor output to the Fac of the Mix Color node.
    
5. The result is a perfect parquet pattern. The white squares of the checker mask will select the "Grain A" texture, and the black squares will select the "Grain B" texture, creating a floor where each tile has a wood grain running perpendicular to its neighbors, all driven by a single material.