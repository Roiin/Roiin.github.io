- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 6
    
- **Core Function:** Retrieves a child object from a parent's hierarchy based on its numerical position (index) in the list of children.
    
- **Key Properties & Settings:**
    
    - **Input (Parent):** The parent object to search within.
        
    - **Input (Index):** The integer representing the child's position, starting from 0.
        
    - **Output (Child):** The found child object.
        
- **Practical Application:** Useful when the order of children is fixed and known. For instance, in an object with multiple spawn points as children, you can cycle through them by incrementing an index value.