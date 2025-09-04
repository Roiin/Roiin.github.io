- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry
    
- **Core Function:** Converts each separate input geometry data-stream into a distinct, self-contained instance. This is a highly efficient alternative to Join Geometry when the goal is to create a collection of separate objects for instancing, rather than a single, merged mesh.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** One or more geometry data-streams. Each separate input link becomes a single output instance.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Instances (Socket - Output):** A list of instances, where each instance corresponds to one of the input geometry links.
        
- **Practical Application:** This node is essential for creating a library of procedural assets to be scattered. Imagine you want to procedurally generate a varied city skyline.
    
    1. First, you create three distinct building types in parallel branches of your node tree:
        
        - A tall, thin skyscraper (e.g., from a scaled cube with an array of windows).
            
        - A wide, medium-height office block (another scaled cube with a different façade).
            
        - A small, simple residential house.
            
    2. Instead of joining them, you feed the final geometry of each of these three building types into a single Geometry to Instance node. The output of this node is now a list containing exactly three items: [skyscraper_instance, office_block_instance, house_instance].
        
    3. Now, you use a Distribute Points on Faces node on a large ground plane to create your city grid. You connect the Instances output of the Geometry to Instance node to the Instance input of an Instance on Points node.
        
    4. Crucially, you check the Pick Instance box on the Instance on Points node. The result is that for each point on your city grid, Blender will now randomly pick one of your three procedurally generated buildings to place there, instantly creating a diverse and varied cityscape from just a few procedural assets.