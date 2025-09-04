- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Operations)
    
- **Core Function:** Increases the resolution of a mesh while simultaneously smoothing it using the Catmull-Clark subdivision algorithm. This is the primary method for turning a low-poly blockout model into a high-poly, smooth, organic final shape.
    
- **Key Properties & Settings:**
    
    - **Mesh (Socket - Input):** The source mesh to be subdivided and smoothed.
        
    - **Level (Socket - Input):** An integer controlling the number of smoothing iterations. Higher levels result in a smoother and denser mesh.
        
    - **Edge Crease (Socket - Input):** A float field on the Edge domain (from 0 to 1). Edges with a crease value of 1 will remain sharp, resisting the smoothing effect.
        
    - **Vertex Crease (Socket - Input):** A float field on the Point domain (from 0 to 1). Pulls the smoothed surface towards the original vertex position.
        
    - **UV Smooth / Boundary Smooth (Properties):** Dropdown menus that provide fine-grained control over how the subdivision affects UV maps and the open edges of a mesh.
        
    - **Mesh (Socket - Output):** The new, high-resolution, smoothed mesh.
        
- **Practical Application:** This node is fundamental for creating smooth, organic creatures from simple block shapes. Imagine you are modeling a cartoon whale.
    
    1. **The Start:** You begin by creating a very simple, low-poly "blockout" of the whale's shape using a few stretched and scaled cubes. The shape is very faceted and ugly.
        
    2. **The Goal:** To turn this blocky form into a smooth, graceful, continuous surface.
        
    3. **The Solution:** Add the Subdivision Surface node.
        
    4. Set the Level to 2 or 3. The node will instantly average the positions of the vertices and add new geometry, transforming the blocky shape into a smooth, streamlined whale body.
        
    5. **Adding Detail:** The whale's tail fluke should have a sharp edge where it meets the tail. You can procedurally select the edges at the base of the fluke (e.g., based on their position) and use a Store Named Attribute to create an "edge_crease" attribute with a value of 1.0 on those edges. Feed this attribute into the Edge Crease input.
        
    6. The result is a model that is 99% smooth and organic, but has a sharp, defined crease exactly where it's needed, creating a much more appealing and professional-looking shape.