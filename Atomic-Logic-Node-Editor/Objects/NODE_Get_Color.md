- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Get Attribute
    
- **Core Function:** Retrieves the "Object Color" property of a specified object. This color can be used in the material shader tree via the "Object Info" node.
    
- **Key Properties & Settings:**
    
    - **Object (Socket):** The target object.
        
    - **Color (Socket):** A 4D vector (RGBA) output representing the object's color.
        
- **Practical Application:** A simple way to pass a color from logic nodes into an object's material. You can get this color to check the object's "team" or "state" if you are using object color for such purposes.