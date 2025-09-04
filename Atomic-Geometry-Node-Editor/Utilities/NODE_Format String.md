- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Constructs a new string by inserting values (floats, integers, or other strings) into a template. It uses Python-style formatting placeholders like {} or {name} to combine text and data without needing multiple Join Strings nodes.
    
- **Key Properties & Settings:**
    
    - **Format (Socket - Input):** The template string containing placeholders. For example, Frame: {} or Score: {points}.
        
    - **Value Inputs (Sockets):** Dynamic input sockets for the values to be inserted. New sockets are created by dragging a connection to the node or in the sidebar.
        
    - **Format Items (Sidebar):** A list in the N-panel to manage, rename, and change the data type of the value inputs.
        
    - **String (Socket - Output):** The final, formatted string.
        
- **Practical Application:** This node is perfect for creating dynamic, data-driven text displays, such as a "health bar" or status readout for a creature in a motion graphics piece.
    
    1. **The Goal:** To create a text object that always reads "Health: [current_health] / 100", where [current_health] is a value you can animate.
        
    2. **The Setup:**
        
        - Create a Group Input in your node tree to get an integer value from the modifier panel. Name it "Current Health".
            
        - Use the Format String node.
            
        - In the Format input, type the string: Health: {} / 100. The {} is the placeholder for your first input.
            
        - Connect your "Current Health" input to the first value socket on the Format String node.
            
    3. **The Geometry:** Connect the String output of the Format String node to a String to Curves node. This will convert your text into renderable 3D geometry.
        
    4. **The Result:** You now have a 3D text object that is dynamically linked to the "Current Health" value in your modifier panel. If you animate this value from 100 down to 25, the 3D text in the viewport will update every frame to read "Health: 99 / 100", "Health: 98 / 100", and so on. This is a powerful and efficient way to create procedural information displays.