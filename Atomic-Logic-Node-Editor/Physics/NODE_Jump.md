- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 2 - Character
    
- **Core Function:** Triggers the jump action for a character physics object, applying an upward impulse.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control that triggers the jump on a rising edge (when it goes from false to true).
        
    - **Input (Object):** The character object that will perform the jump.
        
    - **Output (Done):** A flow control pulse that activates for one frame when the jump is initiated.
        
- - **Practical Application:** Connected to the player's jump button. Logic should first check if the character is on the ground (using Get Physics Info) before allowing this node to be triggered.