- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Outputs the world-space position vector for each element of the input geometry. When evaluated on domains other than points (like faces or edges), the position is interpolated from the surrounding points.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Position (Socket - Output):** A vector field representing the location of each element.
        
- **Practical Application:** This node is fundamental for any operation that needs to know where geometry is located in space. A classic use case is creating a sphere from a cube:
    
    1. Start with a Cube primitive and connect a Set Position node to it.
        
    2. To calculate the new position, take the output of the Position node (which gives the location of each of the cube's vertices).
        
    3. Feed this into a Vector Math node set to 'Normalize'. This operation keeps the direction from the center to each vertex but sets its distance to exactly 1.0.
        
    4. Connect the result of the 'Normalize' operation into the Position input of the Set Position node.  
        The effect is that all vertices of the cube are pushed outwards to a uniform distance from the center, transforming the cube into a sphere. This demonstrates the core "read-modify-write" workflow for geometry manipulation.