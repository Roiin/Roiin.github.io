**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Vector

**Core Function:** Provides a user-friendly interface to move (translate), rotate, and scale a vector, most commonly used to manipulate the coordinates of procedural textures.

**Key Properties & Settings:**

- **Vector (Input/Output):** The node takes a vector as input and outputs the transformed vector. It is typically placed between a Texture Coordinate node and the Vector input of a texture node.
    
- **Location (Input):** Moves the texture coordinates, which has the visual effect of sliding the texture pattern across the object's surface.
    
- -**Rotation (Input):** Rotates the texture coordinates, which visually rotates the texture pattern itself.
    
- **Scale (Input):** Scales the texture coordinates. This has an inverse visual effect: increasing the scale values makes the texture pattern appear smaller and more tiled, while decreasing them makes the pattern larger.
    
- **Vector Type (Property):** Determines the order of operations. Texture (the default) is the most intuitive for artists, as the transformations (move, rotate, scale) are applied in an order that feels like you are manipulating the texture itself. Point is the mathematically standard order.
    

**Practical Application:**  
This node is essential for gaining artistic control over procedural textures. By default, a Noise Texture is mapped to an object's coordinates in a fixed way. If you need to change its size or orientation, you must use a Mapping node.

Its most common use case is to create stretched patterns, which is the key to procedural **wood grain**. The problem is that a standard Noise Texture produces round, cloudy blobs, which looks nothing like the long, parallel fibers of wood. You need to stretch this noise pattern along one axis. The Mapping node is the only way to do this procedurally.

1. Start with a Noise Texture.
    
2. Add a Texture Coordinate node and a Mapping node.
    
3. Connect the nodes in sequence: Texture Coordinate -> Mapping -> Noise Texture. This feeds the coordinates through the mapping node before they are used by the noise.
    
4. In the Mapping node's Scale inputs, you can now control the texture's proportions. To create wood grain, you would set the scale to something like X=1, Y=1, and Z=20.
    
5. This action stretches the texture coordinates twenty times along the Z-axis. Visually, this squashes the noise pattern into long, thin streaks that perfectly mimic the fibrous appearance of wood grain. By adjusting the scale values and rotating the coordinates, you can control the direction and density of this grain with complete artistic freedom.