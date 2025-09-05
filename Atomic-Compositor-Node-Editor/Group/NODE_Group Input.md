- **Editor:** Compositor Node Editor
- **Node Group:** Group
    
- **Core Function:** Serves as the entry point for data into a custom node group, exposing parameters that can be controlled from outside the group.
    
- **Key Properties & Settings:**
    
    - **Sockets (Output):** This node has no fixed sockets. Its output sockets are dynamically created and defined in the Sidebar's Group tab when editing a node group. Each socket you create here becomes an input on the exterior of the group node.
        
- **Practical Application:** This node is fundamental for creating a reusable, custom "Lightwrap" effect. A lightwrap simulates the way bright background light spills around the edges of a foreground element, integrating it more realistically.
    
    1. Start with your foreground element with an alpha channel and a separate background image. Create the core lightwrap logic: blur the background, key the blurred background by the foreground's alpha, and then screen this result over the foreground.
        
    2. Select all the nodes that make up this effect (e.g., **Blur**, **Keying**, **Mix** nodes) and press Ctrl+G to create a group. Blender will automatically create a **Group Input** and **Group Output** node inside.
        
    3. The new group needs inputs. Drag a connection from the empty socket on the **Group Input** node to the Image input of the **Blur** node (for the background) and to the Image input of the final **Mix** node (for the foreground).
        
    4. You also want to control the effect's intensity. Drag another connection from the empty socket on the **Group Input** node to the Size input of the **Blur** node.
        
    5. Press N to open the Sidebar, go to the Group tab, and rename the inputs for clarity: "BG", "FG", and "Wrap Size".
        
    6. The result is a custom "Lightwrap" node. When you use it in your main node tree, it has clear inputs for your background and foreground plates, and a simple slider to control the size of the effect, hiding all the complex logic within.