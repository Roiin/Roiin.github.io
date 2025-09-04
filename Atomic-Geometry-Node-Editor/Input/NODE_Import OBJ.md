- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Import)
    
- **Core Function:** Loads the geometry from an external .OBJ file and makes it available in the node tree as a collection of instances.
    
- **Key Properties & Settings:**
    
    - **Path (Socket - Input):** A string input specifying the file path to the .OBJ file.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Instances (Socket - Output):** A set of instances, where each instance corresponds to a separate object defined within the .OBJ file.
        
- **Practical Application:** This is ideal for using pre-made "kitbash" sets. An artist could have an .OBJ file named sci-fi_greebles.obj that contains 20 different small, detailed parts (vents, panels, pipes, etc.). Using the Import OBJ node, all 20 parts are loaded as a list of instances. This list can then be fed into an Instance on Points node, allowing the artist to procedurally scatter a wide variety of these details across the surface of a spaceship model, adding complexity very quickly from a single source file.