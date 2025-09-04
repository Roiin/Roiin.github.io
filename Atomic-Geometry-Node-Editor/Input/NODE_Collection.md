- **Editor:** Geometry Node Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Imports all objects from a specified Collection into the node tree, typically as a set of instances, allowing for procedural scattering and assembly.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Collection (Property):** An interface field to select the desired asset collection from the Blender scene.
        
    - **Separate Children (Property):** A Boolean toggle. If enabled, parent-child relationships are broken, and all objects in the collection hierarchy are treated as individual instances.
        
    - **Reset Children (Property):** A Boolean toggle. If enabled, the transforms of child objects are reset relative to their parents.
        
    - **Pick Instance (Property):** A Boolean toggle. If enabled, one object is chosen at random from the collection for each instance point, rather than instancing the entire collection at once.
        
    - **Instances (Socket - Output):** The primary output, providing the objects from the collection as usable instances.
        
- **Practical Application:** This is a cornerstone of modular world-building. For example, create a collection named "Rubble_Kit" containing various pieces of broken stone and debris. Use the Collection Info node to bring this kit into a Geometry Node setup and scatter the instances across a terrain or around a destroyed structure, instantly populating the scene with varied, contextually appropriate detail. The Pick Instance option is crucial here for ensuring variety.