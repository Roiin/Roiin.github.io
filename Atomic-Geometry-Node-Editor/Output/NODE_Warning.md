- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utility
    
- **Core Function:** Displays a custom, conditional message (info, warning, or error) in the modifier's "Warnings" panel, providing feedback and guidance to the user.
    
- **Key Properties & Settings:**
    
    - **Show (Socket - Input):** A boolean input. The message will only be displayed if this socket receives a True value.
        
    - **Message (Property):** A text field directly on the node where you write the custom warning or information to be displayed.
        
    - **Warning Type (Property):** A dropdown selector to set the message's severity, which also changes the icon shown in the modifier panel (Info, Warning, Error).
        
    - **Show (Socket - Output):** A passthrough of the Show input socket. This allows you to check a condition and display a warning without interrupting the flow of boolean logic in your node tree.
        
- **Practical Application:** Imagine you've built a node group that creates a spiral staircase, but it only works correctly if the input "Step Count" is a positive number.
    
    1. You can take the "Step Count" input and use a Compare node to check if it's less than 1.
        
    2. The Boolean result of this comparison is plugged into the Show input of the Warning node.
        
    3. In the Warning node's message field, you write: "Error: Step Count must be 1 or greater." and set the Warning Type to 'Error'.
        
    4. Now, if a user tries to enter 0 or a negative number for the step count, a red error icon will appear in the modifier, clearly explaining what they need to fix. This makes your node group much more robust and easier for others (or your future self) to use correctly.