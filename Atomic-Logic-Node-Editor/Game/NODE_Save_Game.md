- **Editor:** Logic Node Editor
    
- **Node Group:** Game
    
- **Core Function:** Saves the current state of the game, including the positions and properties of objects with the "Actor" physics type and any game properties marked as persistent.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A Boolean input that triggers the saving process when True.
        
    - **File Path/Saves (Socket):** A string input specifying the name of the file to save to.
        
    - **Slot (Socket):** An integer input specifying the particular slot within the file to save the data, allowing for multiple save games.
        
    - **Done (Socket):** A flow control output that sends a pulse after the save command has been executed.
        
- **Practical Application:** Implemented at in-game save points or as an option in a pause menu. Activating the save point sets the Condition to True.