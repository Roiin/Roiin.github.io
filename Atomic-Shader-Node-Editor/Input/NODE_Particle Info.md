**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Input

**Core Function:** Provides access to the properties of the parent particle (like age, speed, or a random value) for use within the material of an object being instanced by that particle.

**Key Properties & Settings:**

- **Random (Output):** Generates a unique grayscale value (from 0 to 1) for each particle instance, allowing for randomized variation in the material.
    
- **Age (Output):** Outputs the current age of the particle in frames.
    
- **Lifetime (Output):** Outputs the total lifespan of the particle in frames. The ratio of Age / Lifetime is extremely powerful, creating a 0-to-1 gradient that maps to the particle's life cycle.
    
- **Velocity (Output):** Outputs the speed and direction of the particle. This can be used to create motion-based effects, like stretching a material in the direction of travel.
    

**Practical Application:**  
This node is essential for creating dynamic, evolving materials on instanced objects. Imagine creating a stream of glowing embers or **molten lava** sparks shooting from a fire. Each spark should be born white-hot, cool to a dull red, and then fade to black as it dies.

The problem is that a standard material is static; it cannot change over time. Every spark would have the same color and brightness for its entire life, which looks completely unrealistic. The Particle Info node is the solution.

1. Create a simple Emission shader for the spark material.
    
2. Use a Math node set to Divide. Connect the Age output of the Particle Info node to the top input and the Lifetime output to the bottom input. This creates a normalized 0-to-1 "life progress" value for each particle.
    
3. Connect this result into the Fac of a ColorRamp.
    
4. Set the ColorRamp's gradient to go from bright yellow/white on the left (birth), to orange, then to a deep red on the right (death).
    
5. Plug this ColorRamp into the Color input of the Emission shader. Now, as each particle instance ages, its material will automatically travel along this color gradient, creating a perfect cooling and fading effect. The Random output could be used to slightly vary the hue of each spark, ensuring no two are identical.