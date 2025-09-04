- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Searches an input String for all occurrences of a Find substring and replaces them with a Replace string.
    
- **Key Properties & Settings:**
    
    - **String (Socket - Input):** The source string to be modified.
        
    - **Find (Socket - Input):** The text to search for.
        
    - **Replace (Socket - Input):** The text that will be substituted in place of the Find text.
        
    - **String (Socket - Output):** The new string with the replacements made.
        
- **Practical Application:** This node is very useful for formatting data that you import from external sources. Imagine you have imported a text file (.txt) containing a list of creature names for a bestiary display, but the file uses underscores instead of spaces (e.g., "Giant_Spider", "Cave_Troll").
    
    1. **The Goal:** To automatically replace all the underscores with spaces to make the names readable.
        
    2. Use an Import Text node to load your list of names. If the list is multi-line, you might need to process it line by line.
        
    3. Use the Replace String node.
        
        - The String input is the text from the imported file.
            
        - The Find input is a string containing a single underscore: _.
            
        - The Replace input is a string containing a single space: .
            
    4. The String output is now a clean, readable version of the names ("Giant Spider", "Cave Troll").
        
    5. You can then feed this cleaned-up string into a String to Curves node to display it. This procedural cleanup is much more efficient than manually editing the source file or the text within Blender.