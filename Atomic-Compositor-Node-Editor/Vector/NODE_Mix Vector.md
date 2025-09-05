- **Editor:** Composite Node Editor
- **Node Group:** Vector
    
- **Core Function:** Blends between two input vectors (A and B) based on a blending factor.
    
- **Key Properties & Settings:**
    
    - Factor ([Socket]): A float or vector that controls the influence of each input. A factor of 0 uses Vector A, a factor of 1 uses Vector B.
        
    - A ([Socket]): The first input vector.
        
    - B ([Socket]): The second input vector.
        
    - Data Type ([Property]): Must be set to Vector for this node's vector-specific functionality.
        
    - Factor Mode ([Property]): Defines how the Factor input is interpreted.
        
        - Uniform: A single float value is used to mix all three vector components (X, Y, Z) equally.
            
        - Non-Uniform: Requires a vector input for Factor, allowing you to mix the X, Y, and Z components with different amounts independently.
            
    - Clamp Factor ([Property]): When checked, limits the Factor input to the 0.0 to 1.0 range, preventing extrapolation.
        
    - Result ([Socket]): The final output vector resulting from the mix.
        
- **Practical Application:**
    
    - **Molecular (Texture Coordinate Blending):** A fundamental texturing "molecule" is to mix two different texture coordinate systems to break up patterns. Feed the UV output from a **Texture Coordinate** node into Vector A and the Generated output into Vector B. Use a **Noise Texture** as the Factor. The result is a blended coordinate system that can be fed into any **Image Texture** to seamlessly hide texture repetition across a large surface.
        
    - **Molecular (Simple Positional Transition):** In Geometry Nodes, this node is the easiest way to animate a transition. Feed the Position vector of your geometry into input A and a target position vector (e.g., from another object using an **Object Info** node) into input B. By animating the Factor from 0 to 1, you create a smooth linear interpolation of every point from its start to its end position.
        
    - **Organic (Localized Procedural Deformation):** This node is the heart of many non-destructive damage and deformation "organisms." In Geometry Nodes, feed the original Position into input A. For input B, create a displaced vector by adding a **Noise Texture** to the original Position. Now, for the Factor, use a texture map, a vertex group, or the output of an **Ambient Occlusion** node. The result is a powerful setup where the noise-driven displacement only appears in the white areas of the factor mask, creating realistic rust, dents, or organic growth in a completely procedural and controllable way.
        
    - **Organic (Dynamic Wind Field Simulation):** To create a more believable motion "organism," you can blend vector fields. Create a simple "wind" vector (e.g., using **Combine XYZ** with a value in the X direction) and plug it into input A. Create a "turbulence" vector by plugging a **4D Noise Texture** (with an animated W value) into input B. You can then use another, larger-scale **Noise Texture** as the Factor. This creates a system where the base wind blows consistently, but pockets of procedural turbulence are mixed in, resulting in much more natural and complex particle or foliage motion.