### **Concept: Creating a New Group (Encapsulation)**

**Editor:** Geometry Nodes Editor  
**Node Group:** Group

**Core Function:** To combine a selection of nodes into a single, self-contained custom node, dramatically simplifying the main node graph and creating a reusable asset.

**Key Properties & Settings:**

- **Creation:** Select two or more nodes and press Ctrl-G.
    
- **Encapsulation:** The selected nodes are immediately moved into a new, isolated node tree. In the original node tree, they are replaced by a single, green node representing the new group.
    
- **Navigation:** Use the Tab key to enter and exit the currently selected group.
    
- **Naming:** The new node group can be named in the Node Editor's sidebar for easy identification in asset libraries.
    

**Practical Application:**  
This workflow is the most critical technique for managing complexity. Imagine you have just finished creating a procedural tree. Your main node graph is a sprawling network of 100+ nodes for the trunk, branches, twigs, and leaves. It is functional, but unreadable and impossible to reuse.

- **The Goal:** To clean up the messy 100-node tree generator and turn it into a single, portable "Procedural Tree" asset.
    
- **The Problem:** The graph is a "spaghetti" of connections. Finding the control for "Trunk Height" is a major task. If you wanted a second, different tree, duplicating all 100 nodes would be a nightmare.
    
- **The Solution:** Encapsulate the entire network into a group.
    
    1. In your main node graph, draw a selection box around all 100+ nodes that constitute your tree generator.
        
    2. Press Ctrl-G.
        
    3. Instantly, the entire mess is replaced by a single, clean green node. The node graph is now simple and readable.
        
    4. Press Tab to enter this new group. You can now use the Group Input and Group Output nodes to expose key parameters (like "Trunk Height" or "Leaf Density") and output the final "Tree Mesh".
        

You have successfully transformed a complex, one-off setup into a clean, reusable, and professional-grade asset. Your main graph is now incredibly simple, perhaps consisting only of your "Procedural Tree" node connected to the final scene output.