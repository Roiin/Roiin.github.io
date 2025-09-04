- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Texture
    
- **Core Function:** Generates simple, smooth gradients across a coordinate space. It's the primary tool for creating linear or radial falloffs.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket - Input):** The coordinate space to evaluate the gradient in. By default, uses the object's Position.
        
    - **Type (Property):** The core control that defines the gradient's shape:
        
        - **Linear:** A straight gradient along the X-axis.
            
        - **Quadratic / Easing:** Smoother, non-linear variations of the linear gradient.
            
        - **Diagonal:** A straight gradient from one corner to the opposite.
            
        - **Spherical:** A 3D radial gradient that is white (1.0) at the center (0,0,0) and fades to black (0.0) as the distance from the center increases.
            
        - **Radial:** A circular gradient that sweeps around the Z-axis, like a clock face.
            
    - **Color / Factor (Sockets - Output):** The resulting gradient, provided as both a color and a grayscale float.
        
- **Practical Application:** The 'Spherical' gradient is perfect for creating proximity-based effects that are centered on an object. Imagine you have a magical creature, and you want to instance smaller "wisp" particles in a cloud around it, with the wisps being largest near the creature and fading away to nothing further out.
    
    1. First, distribute a large cloud of points in a volume around your creature.
        
    2. **The Goal:** To control the scale of the wisp instances based on their distance from the main creature.
        
    3. You need to evaluate the gradient relative to the creature's position, not the world origin. Take the Position of your particle points and subtract the Location of your creature (from an Object Info node). This gives you a vector pointing from the creature to each particle.
        
    4. Feed this relative vector into the Vector input of a Gradient Texture node set to 'Spherical'.
        
    5. The Factor output is now a perfect spherical falloff centered on your creature. It's 1.0 at the creature's center and fades to 0.0 with distance.
        
    6. You can use a Map Range or Color Ramp to fine-tune this falloff, then plug the result directly into the Scale input of an Instance on Points node.
        
    7. **The Result:** A cloud of wisps that are densest and largest right next to the creature, and which gracefully fade away in size and density with distance, creating a beautiful and dynamic aura effect.