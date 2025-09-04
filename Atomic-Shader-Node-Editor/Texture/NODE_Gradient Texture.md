**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates smooth, procedural gradients that transition across an object's texture coordinates in various shapes like linear, spherical, or radial.

**Key Properties & Settings:**

- **Factor (Output):** The primary output, providing a grayscale gradient from black (0.0) to white (1.0). This is ideal for controlling the Fac input on Mix Shader or ColorRamp nodes.
    
- **Gradient Type (Property):** The core control that defines the shape of the gradient.
    
    - **Linear:** Creates a simple, straight-line gradient across one axis.
        
    - **Spherical:** Creates a gradient that radiates outwards from the object's origin, appearing as a white dot in the center that fades to black.
        
    - **Radial:** Creates a circular gradient that sweeps around the Z-axis, like a clock face.
        
- **Vector (Input):** Specifies the coordinate system for the gradient. Connecting a Texture Coordinate node's Generated or Object output is the standard workflow. This can be further modified with a Mapping node to rotate or reposition the gradient.
    

**Practical Application:**  
This node is perfect for creating materials that change their properties along a specific axis. It is the ideal tool for simulating **molten lava** that cools as it flows.

The problem with a simple emission shader for lava is that it has a uniform color and temperature, which looks static and fake. Real lava is hottest at its source and cools to a dark, solid crust as it moves away. You need a way to create this temperature gradient. The Gradient Texture node is the solution.

1. Start with a Principled BSDF for your lava material.
    
2. Add a Gradient Texture node and set its Type to Linear. To control its direction, you will likely need to use a Mapping node between your Texture Coordinate node and the Gradient Texture's Vector input. This allows you to rotate the gradient to match the "flow" direction of your lava.
    
3. Connect the Factor output of the Gradient Texture to the Fac input of a ColorRamp node.
    
4. Define the temperature gradient on the ColorRamp. Set the left side (representing the gradient's start) to a bright, white-hot yellow. Transition it through orange, then a deep red, and finally to a dark, cooled black on the right side.
    
5. Connect the ColorRamp's Color output to both the Base Color and the Emission Color inputs of your Principled BSDF.
    
6. The result is a dynamic and realistic lava flow. The material is brightest and most emissive at one end and gradually cools and darkens along the length of the gradient, perfectly simulating the loss of heat.