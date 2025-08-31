- **Editor:** Logic Node Editor
    
- **Node Group:** Sound
    
- **Core Function:** Immediately stops the playback of a specific sound.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Sound):** A reference to the sound to be stopped (often from the output of a Start Speaker or 3D Sound node).
        
    - **Output (Done):** A flow control pulse that activates after the sound is stopped.
        
- **Practical Application:** Used to cut off a looping sound when its source is disabled (e.g., stopping a fire's crackle when it's extinguished) or to interrupt a character's voice line.