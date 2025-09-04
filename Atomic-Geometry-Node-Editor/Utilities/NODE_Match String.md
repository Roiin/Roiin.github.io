- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Compares an input String against a Key string and outputs a Boolean True or False based on the chosen matching method.
    
- **Key Properties & Settings:**
    
    - **String (Socket - Input):** The source string to be searched or compared.
        
    - **Key (Socket - Input):** The substring or text to search for.
        
    - **Operation (Property):** The comparison method:
        
        - **Starts With:** Returns True if the String begins with the Key.
            
        - **Ends With:** Returns True if the String ends with the Key.
            
        - **Contains:** Returns True if the Key is found anywhere within the String.
            
    - **Result (Socket - Output):** The Boolean outcome of the comparison.
        
- **Practical Application:** This node is perfect for creating selection masks based on object naming conventions. Imagine you have a scene with many different types of creatures, and you want to apply a "dissolve" effect only to the ones that are ghosts. You have a naming convention where all ghost objects end with "_ghost" (e.g., "Horse_ghost", "Knight_ghost").
    
    1. **The Goal:** To create a Boolean attribute that is True only for the ghost objects.
        
    2. Use a Collection Info node to bring all your creature objects into the node tree.
        
    3. You need the name of each instanced object. You can get this by realizing the instances and accessing the name attribute.
        
    4. Use the Match String node.
        
        - The String input is the name attribute of each object.
            
        - The Key is the string "_ghost".
            
        - Set the Operation to 'Ends With'.
            
    5. The Result is now a Boolean field that is True for every face of the ghost creatures and False for everything else.
        
    6. You can now use this selection to drive the Selection input of a Delete Geometry node, with the deletion masked by an animated Noise Texture to create the dissolve effect. The Match String node allowed you to procedurally target specific objects for this effect based solely on their name.