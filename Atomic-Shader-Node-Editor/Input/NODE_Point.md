**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Input

**Core Function:** Provides access to per-point attributes like position, radius, and a random value for shading point cloud objects.

**Key Properties & Settings:**

- **Random (Output):** The primary output for creating variation. It generates a unique grayscale value (from 0 to 1) for each individual point in the point cloud.
    
- **Radius (Output):** Outputs the radius value of each point.
    
- **Location (Output):** Outputs the world-space position of each point.
    

**Practical Application:**  
This node is specifically designed to add variation to materials on point cloud objects. Imagine creating a vast, glittering starfield using a point cloud, where each point represents a distant star.

The problem is that without variation, every star will have the identical color and brightness, leading to a flat, repetitive pattern that looks artificial. The Point Info node is the solution for introducing this necessary chaos.

1. Start with a simple Emission shader, as stars emit light.
    
2. Connect the Random output of the Point Info node to the Fac input of a ColorRamp node.
    
3. Set the ColorRamp's gradient to represent different stellar types, for example, from a dim red to a warm yellow, and finally to a brilliant blue-white.
    
4. Plug the output of this ColorRamp into the Color input of the Emission shader.
    
5. Additionally, you can connect the Random output to a Math node set to Multiply to control the Emission Strength. This will make some stars appear much brighter than others.
    
6. The result is a dynamic and believable starfield where each point has a unique color and intensity, transforming a uniform grid of points into a natural-looking cosmos, all controlled by a single, efficient material.