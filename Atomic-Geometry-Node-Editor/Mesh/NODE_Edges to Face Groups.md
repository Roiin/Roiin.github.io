- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Read)
    
- **Core Function:** For a given mesh, this node analyzes a selection of "boundary" edges and assigns a unique integer ID to each contiguous group of faces that is enclosed by those boundaries. It essentially functions like a "paint bucket" tool, flooding areas with an ID.
    
- **Key Properties & Settings:**
    
    - **Boundary Edges (Socket - Input):** A boolean selection identifying the edges that act as "walls" or dividers.
        
    - **Face Group ID (Socket - Output):** An integer field on the Face domain. Every face within the same enclosed region will share the same unique ID.
        
- **Practical Application:** This node is perfect for creating varied patterns on surfaces, like a floor with randomized wooden plank textures.
    
    1. Start with a heavily subdivided Grid mesh for your floor.
        
    2. **The Goal:** You want to assign a different, randomly rotated wood texture to different "planks" or regions of the floor to break up the repetition.
        
    3. First, you need to define the "planks". You can create a Boolean selection for every 5th edge along the X-axis and every 10th edge along the Y-axis. These will be your Boundary Edges.
        
    4. Feed this selection into the Edges to Face Groups node. The Face Group ID output is now an integer field where each rectangular "plank" on your floor has its own unique ID.
        
    5. Use a Random Value node with the Face Group ID as its Seed. Set the type to 'Vector'. This will generate a unique, random XYZ vector for each plank.
        
    6. Store this random vector as a named attribute (e.g., "plank_rotation").
        
    7. In the Shader Editor, use an Attribute node to retrieve "plank_rotation". You can then use this to drive the Rotation input of a Mapping node that controls your wood texture's coordinates.
        
    8. The result is a floor where each procedurally defined plank has a unique, random wood grain orientation, creating a highly realistic and non-repetitive surface.