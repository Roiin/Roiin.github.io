- **Editor:** Logic Node Editor
    
- **Node Group:** File
    
- **Core Function:** Loads a sound file (e.g., .wav, .mp3, .ogg) from disk and provides a direct reference to it.
    
- **Key Properties & Settings:**
    
    - **Input (Sound File Picker):** A file browser interface within the node to select the desired audio file.
        
    - **Output (Sound File):** The loaded sound object, ready to be used by any of the sound playback nodes (Start Speaker, 3D Sound, etc.).
        
- **Practical Application:** The standard way to reference any audio that will be played in the game. You use this node to load a sound effect or a music track, and then pass its output to the appropriate sound node to play it.