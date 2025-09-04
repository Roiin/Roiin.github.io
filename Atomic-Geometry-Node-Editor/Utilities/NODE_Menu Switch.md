**Editor:** Geometry Nodes Editor  
**Node Group:** Control (Switching)

**Core Function:** Selects and passes through one of its multiple data inputs based on a user-friendly dropdown menu, ensuring that only the nodes connected to the chosen input are evaluated.

**Key Properties & Settings:**

- **Type (Property):** Defines the data type for all sockets on the node (e.g., Geometry, Vector, Material).
    
- **Menu Items (Sidebar Interface):** In the Node Editor's sidebar (N-Panel), you can add, remove, rename, and reorder the menu options. Renaming an item here also renames the corresponding input socket on the node.
    
- **Menu (Input):** A special socket that, when connected to a Group Input node, exposes the custom dropdown menu in the modifier's interface.
    
- **Item Inputs (Dynamic):** A list of data sockets that are dynamically created and named based on the menu items defined in the sidebar.
    
- **Output (Output):** The single output that passes through the data from the input corresponding to the selected menu option.
    

**Practical Application:**  
This node is an enhanced version of the Index Switch, designed to create highly intuitive and professional-quality procedural assets. Imagine you are creating a "Procedural Window" asset. Instead of using a number to select the window style, you want to provide the user with a clear, descriptive dropdown menu.

- **The Goal:** To create a "Window Style" dropdown menu in the modifier panel that lets a user choose between "Archtop," "Modern," and "Porthole" window designs.
    
- **The Problem:** Using an Index Switch would require the user to memorize that 0 is Archtop, 1 is Modern, etc. This is unintuitive and poor design for a shareable asset.
    
- **The Solution:** The Menu Switch node is built to solve this exact user-interface challenge.
    
    1. Create a Menu Switch node and set its Type to Geometry.
        
    2. In the sidebar properties for the node, add three menu items and rename them to "Archtop", "Modern", and "Porthole". The node will update to show three inputs with these names.
        
    3. Connect the final geometry from your "Archtop" generator to the "Archtop" input socket. Do the same for the "Modern" and "Porthole" generators.
        
    4. Drag a connection from the Menu input of the Menu Switch node to an empty socket on your main Group Input node.
        
    5. Connect the single Output from the Menu Switch node to your final Group Output.
        

Now, when this node group is added as a modifier to an object, it will have a clean, professional dropdown menu labeled "Menu" (which you can rename in the group inputs). The user can simply select "Archtop," "Modern," or "Porthole" by name to instantly switch between the different, complex window geometries, providing a vastly superior user experience.