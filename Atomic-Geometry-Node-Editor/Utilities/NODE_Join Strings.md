- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Concatenates (joins) multiple input strings into a single output string. It can also insert a Delimiter string between each of the joined elements.
    
- **Key Properties & Settings:**
    
    - **Delimiter (Socket - Input):** A string that is placed between each of the input strings. For example, a comma or a space.
        
    - **Strings (Multi-Socket - Input):** A dynamic socket that accepts multiple string inputs. The final string is assembled in the top-to-bottom order of the connections.
        
    - **String (Socket - Output):** The final, combined string.
        
- **Practical Application:** This node is essential for assembling text from different procedural sources, like creating a descriptive label for a procedurally generated creature.
    
    1. **The Goal:** To create a label that reads "Species: [Name], Age: [Age]", where the name and age are generated procedurally.
        
    2. **The Setup:**
        
        - You have a String input node for the creature's name (e.g., "Gargoyle").
            
        - You have a Value to String node that has converted a procedurally generated age (e.g., the integer 342) into a string.
            
        - Use the Join Strings node.
            
        - For the Delimiter, you want a comma followed by a space, so you input ,.
            
    3. **The Connections (in order):**
        
        - Connect a String node containing "Species: " to the first input.
            
        - Connect your "Gargoyle" string to the second input.
            
        - Now the delimiter will be added.
            
        - Connect a String node containing "Age: " to the third input.
            
        - Connect your "342" string (from Value to String) to the fourth input.
            
    4. **The Result:** The String output of the Join Strings node will be the perfectly assembled text: "Species: Gargoyle, Age: 342". You can now feed this into a String to Curves node to display it.