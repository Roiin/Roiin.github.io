- **Editor:** Logic Node Editor
    
- **Node Group:** Values > Vector
    
- **Core Function:** Deconstructs a 3D vector into its individual X, Y, and Z float components.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** The 3D vector input.
        
    - **X / Y / Z (Sockets):** Three separate float outputs for each component.
        
- **Practical Application:** Used when you need to work with only one component of a vector. Example: To make a character jump, you get their current linear velocity vector, use Separate XYZ to isolate the X and Y components, and then use Combine XYZ to create a new vector with the original X/Y but a new, higher Z value.