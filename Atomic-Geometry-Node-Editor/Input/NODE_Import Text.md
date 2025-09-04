- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Import)
    
- **Core Function:** Reads the entire content of a specified .txt file and outputs it as a single text string.
    
- **Key Properties & Settings:**
    
    - **Path (Socket - Input):** A string specifying the file path to the .txt file.
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **String (Socket - Output):** The full text content from the imported file as a single string.
        
- **Practical Application:** This is extremely useful for motion graphics. Imagine you need to create a title sequence where the text is provided by an external source. You can use the Import Text node to load a titles.txt file. The resulting string is then fed directly into a String to Curves node, which procedurally generates the text as 3D geometry. This workflow is highly efficient because if the title text needs to be changed, you only need to edit the external .txt file; the Blender scene will update automatically without needing to manually re-type anything.