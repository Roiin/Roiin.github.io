**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Matrix)

**Core Function:** Applies a projection matrix to a 3D position vector, transforming it into the 2D-like coordinate space of a camera or view.

**Key Properties & Settings:**

- **Vector (Input):** The 3D position vector in world space that you want to project.
    
- **Transformation (Input):** The projection matrix, which is typically a combination of a camera's view matrix and its perspective projection matrix.
    
- **Vector (Output):** The projected position. The X and Y components represent the point's coordinates in the 2D projection (e.g., screen space), while the Z component represents its depth.
    

**Practical Application:**  
This node is essential for creating effects that are dependent on the camera's viewpoint, such as making particles larger or smaller based on their position on the screen. Imagine you are creating a stylized vignette effect on a rhino model, where particles scattered on its skin shrink as they get closer to the edge of the camera's view.

- **The Goal:** To control the scale of particles on a rhino based on their distance from the center of the camera's screen.
    
- **The Problem:** The particles' positions are in 3D world space. To know where they are on-screen, you need to transform their 3D coordinates into the camera's 2D coordinate system.
    
- **The Solution:** The Project Point node performs this exact transformation.
    
    1. First, you need the camera's combined view-projection matrix. Use an Object Info node to select your main Camera. Multiply its Projection Matrix by its View Matrix (which is its inverted world transform).
        
    2. Get the Position of the points on your rhino model where particles are instanced.
        
    3. Use the Project Point node.
        
        - Connect the particle Position to the Vector input.
            
        - Connect the combined camera matrix to the Transformation input.
            
    4. The Vector output now contains the screen-space coordinates for each particle. The X and Y values will be near 0 for particles in the center of the view.
        
    5. Use a Vector Math (Length) node on this output vector to get a single float value representing each particle's distance from the screen's center.
        
    6. Use a Map Range node to invert and remap this distance. Map a small distance (e.g., 0.0) to a large scale (1.0) and a larger distance (e.g., 1.0) to a small scale (0.1).
        
    7. Feed this final value into the Scale input of your Instance on Points node.
        

The result is a dynamic vignette effect made of geometry. Particles on the rhino that are in the middle of your shot will be full-sized, and they will shrink smoothly as the camera moves and they approach the edge of the frame.