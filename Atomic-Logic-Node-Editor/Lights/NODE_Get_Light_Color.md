- **Editor:** Logic Node Editor
    
- **Node Group:** Lights
    
- **Core Function:** Retrieves the color of a specified Light object.
    
- **Key Properties & Settings:**
    
    - **Light Object (Socket):** An object input that takes a reference to a Light object in the scene.
        
    - **Color (Socket):** A 3D vector output representing the light's RGB color, with each channel ranging from 0.0 to 1.0.
        
- **Practical Application:** Used to query the current state of a light. You could use this to make a material emissively match the color of a nearby light source or to store a light's original color before temporarily changing it.