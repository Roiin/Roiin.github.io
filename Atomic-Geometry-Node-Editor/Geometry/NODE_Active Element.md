- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Identifies the single "active" element (typically the last one selected in Edit Mode) and outputs its index. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Domain (Property):** A dropdown to specify which element type to check for an active member (Point, Edge, Face).
        
    - **Index (Socket - Output):** The integer index of the single active element.
        
    - **Exists (Socket - Output):** A Boolean that is True if an active element of the specified domain exists, and False otherwise.
        
- **Practical Application:** Imagine creating a custom "Spider Web" tool. The user would enter Edit Mode on a wall object, select a single vertex where they want the web to originate, and then run your tool.
    
    1. The Active Element node (with its domain set to 'Point') provides the Index of this single, last-selected vertex.
        
    2. This Index is then used with a Sample Index node to get the exact Position of that vertex.
        
    3. This position becomes the central anchor point from which the tool can procedurally draw the radial and spiral threads of the spider web.
        
    4. The Exists output can be connected to a Warning node, so if the user runs the tool without an active vertex, a helpful message like "Please select a starting point for the web" appears.