- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Extracts a portion (a "slice") of an input string, defined by a starting Position and a Length.
    
- **Key Properties & Settings:**
    
    - **String (Socket - Input):** The source string to be sliced.
        
    - **Position (Socket - Input):** The starting index for the slice. The first character is at index 0.
        
    - **Length (Socket - Input):** The number of characters to include in the slice.
        
    - **String (Socket - Output):** The new, extracted substring.
        
- **Practical Application:** This node is perfect for extracting specific data from a structured string, like getting a creature's unique ID from its full object name.
    
    1. Imagine you have a scene of procedurally generated animals, and each one is automatically named with a prefix and a unique ID number, like "Animal_001", "Animal_002", etc.
        
    2. **The Goal:** You need to extract just the number part ("001") to use as a seed for a Random Value node, giving each animal unique color variations.
        
    3. You have the full name of the object as a string.
        
    4. Use the Slice String node.
        
        - The String input is the object's name.
            
        - You know that the prefix "Animal_" is always 7 characters long. Therefore, the number always starts at index 7. So, you set the Position to 7.
            
        - You know the ID number is always 3 characters long. So, you set the Length to 3.
            
    5. The String output of this node is now just the number part (e.g., "001").
        
    6. You can use a (future) String to Value node to convert this back into an integer, which can then be used as a stable and unique Seed for randomizing the color or scale of each creature. The Slice String node allowed you to parse and extract a useful piece of data from a formatted text block.