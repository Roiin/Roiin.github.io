- **Editor:** Logic Node Editor
    
- **Node Group:** File
    
- **Core Function:** Loads a font file (e.g., .ttf, .otf) from disk and provides a direct reference to it.
    
- **Key Properties & Settings:**
    
    - **Input (Font Picker):** A file browser interface within the node to select the desired font file.
        
    - **Output (Font):** The loaded font object, ready to be used by UI nodes.
        
- **Practical Application:** The necessary first step for using any custom font in your game's user interface. The output of this node is fed into a Create Label or other UI text node to set its typeface.