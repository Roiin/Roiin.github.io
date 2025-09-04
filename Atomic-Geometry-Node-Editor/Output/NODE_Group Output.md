- **Editor:** Geometry Nodes Editor
    
- **Node Group:** output
    
- **Core Function:** Serves as the final exit point for a node group. It defines the primary geometry that the modifier will output and allows for the exposure of custom-calculated attributes to other parts of Blender, such as the Shader Editor or other modifiers.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The primary and mandatory input socket. The geometry data stream connected here is what will be passed out of the modifier and rendered in the viewport.
        
    - **Custom Sockets (Interface):** New output sockets can be created by dragging a connection from any preceding node into the blank, circular socket at the bottom of the node. This exposes that data stream as an output attribute.
        
    - **Sidebar Configuration (N-Panel):** When the node is selected, the "Group" tab in the sidebar (N-Panel) provides detailed controls for each output socket:
        
        - **Name:** Defines the public name of the output attribute. This is the name you will use to access it elsewhere (e.g., in the Shader Editor).
            
        - **Data Type:** Shows the type of data being passed through the socket (e.g., Geometry, Vector, Float, Boolean). This is usually determined automatically.
            
        - **Attribute Domain:** Specifies on which part of the geometry the attribute is stored (e.g., Point, Edge, Face, Instance). This is a critical setting.
            
        - **Tooltip:** Allows you to write a custom description for the output, which will appear when hovering over it in the modifier interface.
            
- **Practical Application:** This node is the bridge between procedural geometry and procedural shading. For instance, imagine you have created a procedural mountain mesh.
    
    1. Inside your Geometry Node tree, you calculate the steepness of the terrain for every face using the Z component of the Normal node.
        
    2. You drag a connection from this steepness calculation (a float value) to a new socket on the Group Output node.
        
    3. In the sidebar, you name this new output "slope_mask".
        
    4. Now, in the Shader Editor for the mountain's material, you can add an Attribute node, type "slope_mask" into its name field, and use the resulting factor to mix between a grass texture (for flat areas) and a rock texture (for steep areas).