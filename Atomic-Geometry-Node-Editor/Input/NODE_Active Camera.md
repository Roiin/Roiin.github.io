- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides a direct reference to the scene's currently active camera object.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Active Camera (Socket - Output):** The currently active camera object.
        
- **Practical Application:** This is essential for creating camera-dependent effects and optimizations. For example, to implement a simple Level of Detail (LOD) system for a large field of instanced grass, you can use the Active Camera node along with an Object Info node to get the camera's location. By calculating the distance between each grass instance and the camera, you can use a Delete Geometry node to remove any instances that are beyond a certain range (e.g., 100 meters). This ensures that geometry far from the camera isn't processed, significantly improving viewport performance.