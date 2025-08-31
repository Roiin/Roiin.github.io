- **Editor:** Logic Node Editor
    
- **Node Group:** Sound
    
- **Core Function:** A comprehensive node for playing a sound file with full control over its 3D positional audio properties.
    
- **Key Properties & Settings:**
    
    - **Input (Sound File):** The audio file to be played.
        
    - **Input (Position):** A vector (X, Y, Z) defining the sound's location in world space.
        
    - **Input (Pitch):** A float controlling the playback speed/pitch (1.0 is normal).
        
    - **Input (Volume):** A float controlling the sound's volume (1.0 is normal).
        
    - **Setting (Use Occlusion):** If checked, the sound will be muffled by intervening objects.
        
    - **Setting (Once):** If checked, the sound plays once; otherwise, it loops.
        
    - **Setting (Ignore Timescale):** If checked, the sound's pitch is not affected by changes in the game's timescale.
        
    - **Output (On Start):** A flow control pulse that activates when the sound begins playing.
        
    - **Output (On Finish):** A flow control pulse that activates when the sound finishes playing.
        
- **Practical Application:** Ideal for playing environmental or non-object-specific sounds, such as a disembodied voice in a horror game or the ambient sound of wind in a large, open area.