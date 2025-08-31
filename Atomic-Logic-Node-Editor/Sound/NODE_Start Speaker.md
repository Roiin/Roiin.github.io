- **Editor:** Logic Node Editor
    
- **Node Group:** Sound
    
- **Core Function:** Plays a sound originating from a specific object in the scene, which acts as a "speaker."
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Speaker):** The object from which the sound will emanate.
        
    - **Input (Sound):** The audio file to be played.
        
    - **Output (On Start):** A flow control pulse that activates when the sound begins playing.
        
    - **Output (On Finish):** A flow control pulse that activates when the sound finishes playing.
        
- **Practical Application:** The standard way to attach sounds to game elements. Used to make an NPC speak, a gun fire, a door creak, or a machine hum. The sound automatically moves with the speaker object.