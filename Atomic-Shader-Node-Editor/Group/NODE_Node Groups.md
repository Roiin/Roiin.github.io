**Editor:** All Node Editors (Shader, Compositor, Geometry Nodes, etc.)  
**Engine(s) Supported:** All  
**Node Group:** N/A (This is the container for node groups)

**Core Function:** A Group Node serves as a container, bundling a complex network of individual nodes into a single, reusable, and simplified custom node. This is fundamental for organizing node trees, hiding complexity, and creating custom tools that can be easily shared and reused.

**Key Properties & Settings:**

- **Encapsulation:** It takes a selection of connected nodes and collapses them into a single block.
    
- **Custom I/O:** You decide which inputs and outputs from the internal node network are exposed on the outside of the Group Node, creating a custom interface.
    
- **Reusability:** Once a node group is created, it can be instanced multiple times within the same node tree or even linked into different Blender files.
    

**Practical Application:**  
Imagine you've created a complex material setup for a specific type of metal, involving multiple textures, color ramps, and noise patterns to control roughness and color. This might involve 15-20 individual nodes.

1. Select all the nodes that make up your custom metal material (except for the initial Input nodes and the final Material Output node).
    
2. Group them together by pressing Ctrl+G.
    
3. You will now be "inside" the group. You can see the internal network. Use the Tab key to enter and exit the group.
    
4. Connect any internal sockets you need to control from the outside (like a master color or a wear-and-tear factor) to the empty Group Input node.
    
5. Connect the final output of your internal network (e.g., the BSDF shader output) to the empty Group Output node.
    
6. Use the Sidebar (N key) > Group tab to name your inputs and outputs descriptively.
    
7. Now, when you Tab back out, you have a single, clean "Custom Metal" node with only the essential controls you exposed. You can easily drop this into any other material without having to recreate the entire complex setup.