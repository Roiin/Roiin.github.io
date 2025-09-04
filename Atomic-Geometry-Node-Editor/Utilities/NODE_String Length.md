- **Editor:** Geometry Nodes Editor
    
- an - **Node Group:** Utilities (String)
    
- **Core Function:** For a given string, this node outputs an integer representing the total number of characters it contains.
    
- **Key Properties & Settings:**
    
    - **String (Socket - Input):** The source string to be measured.
        
    - **Length (Socket - Output):** An integer representing the character count of the input string.
        
- **Practical Application:** This node is essential for creating procedural text effects that need to adapt to the size of the input text, such as auto-sizing a background panel for a creature's nameplate.
    
    1. **The Goal:** You are creating a nameplate for an animal. You want a 3D rectangular panel to always be the perfect size to fit behind the animal's name, no matter how long the name is.
        
    2. **The Setup:**
        
        - You have an input string for the animal's name (e.g., "Gryphon").
            
        - You use a String to Curves node to generate the 3D text.
            
    3. **The Problem:** The background panel needs to know how wide the text is.
        
    4. **The Solution:**
        
        - Use the String Length node on the name string. This gives you the number of characters (e.g., 7 for "Gryphon").
            
        - This character count can be used as a direct proxy for the width of the text. You can multiply it by an average character width (e.g., 0.8) to get a good approximation of the total length of the generated 3D text.
            
        - Use a Cube or Grid primitive to create your background panel. Feed your calculated width into the Size X input of the cube.
            
    5. **The Result:** A perfectly responsive system. If you change the input name from "Gryphon" to the much longer "Hippogriff," the String Length node's output will increase, which in turn increases the X-size of the background panel, ensuring it always fits the text perfectly.