**Editor:** Shader Editor 
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Input

**Core Function:** Calculates contact shadows by darkening areas where geometry is close together, simulating the absence of ambient light in tight crevices and corners.

**Key Properties & Settings:**

- **AO (Output):** The primary output. It provides a grayscale mask where black represents fully occluded areas (crevices, contact points) and white represents fully exposed surfaces.
    
- **Color (Output):** A colorized version of the AO output, tinted by the Color input socket.
    
- **Distance:** The most critical setting. It defines the maximum distance (in Blender units) to search for nearby surfaces. A small distance creates tight, sharp lines in corners, while a larger distance produces softer, broader shadows.
    
- **Only Local:** When enabled, the node only calculates occlusion caused by the object's own geometry, ignoring all other objects in the scene.
    
- **Inside:** Inverts the effect, causing the node to highlight exposed convex edges instead of occluded concave corners.
    

**Practical Application:**  
The Ambient Occlusion node is fundamental for adding procedural wear and grime to a material. Imagine creating a piece of old, painted machinery where dust and **rust** have accumulated in the crevices.

The problem is how to make this grime appear only in the recessed areas where it would naturally collect, rather than being uniformly applied. The AO node is the solution.

1. Create two distinct materials: a base "Painted Metal" shader and a "Rust" shader.
    
2. Use a Mix Shader node to combine them.
    
3. Connect the AO output of the Ambient Occlusion node to the Fac input of the Mix Shader.
    
4. The result is immediate and intuitive: The black areas of the AO map (the crevices and corners) will reveal the "Rust" shader, while the white, exposed surfaces will remain "Painted Metal." By adjusting the Distance property, you can control how far the rust "creeps" out from the edges. For finer control, a ColorRamp node can be placed between the AO node and the Mix Shader to crush the whites and blacks, creating a sharper, more defined mask for the rust.