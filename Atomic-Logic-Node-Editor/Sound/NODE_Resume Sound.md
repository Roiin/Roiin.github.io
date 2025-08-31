- **Editor:** Logic Node Editor
    
- **Node Group:** Sound
    
- **Core Function:** Resumes playback of a previously paused sound from the exact point it was stopped.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Sound):-** A reference to the sound to be resumed.
        
    - **Output (Done):** A flow control pulse that activates after the sound resumes.
        
- **Practical Application:** Used in conjunction with Pause Sound to un-pause audio when the player exits a menu and returns to the game.