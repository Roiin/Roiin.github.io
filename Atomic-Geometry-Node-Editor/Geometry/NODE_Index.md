- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Read)
    
- **Core Function:** Outputs the current index (position in the list) for each element of the geometry, starting from 0. This index is dynamic and can change if the geometry's topology is altered (e.g., if elements are deleted or subdivided).
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Index (Socket - Output):** An integer field representing the current index of each element.
        
- **Practical Application:** The Index node is frequently used for creating procedural patterns. For example, to create a checkerboard pattern on a Grid primitive, you can use a Math node set to 'Modulo 2' on the Index of each face. This will output a 0 for even-indexed faces and a 1 for odd-indexed faces. This alternating 0-1 pattern can then be used as a selection mask to delete every other face or to assign alternating black and white materials, instantly generating the checkerboard effect.