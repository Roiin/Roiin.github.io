- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Write)
    
- **Core Function:** Assigns a custom name to a geometry data-stream, which is visible in the Spreadsheet Editor. This is primarily used for organizing and debugging complex node trees.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry to be named.
        
    - **Name (Socket - Input):** A string input for the desired name.
        
    - **Geometry (Socket - Output):** The geometry, now carrying the new name.
        
- **Practical Application:** This node is invaluable for keeping complex projects organized. Imagine you are procedurally creating a window, which consists of two separate parts: the wooden frame and the glass panes.
    
    1. You generate the frame geometry and immediately connect it to a Set Geometry Name node, giving it the name "Window_Frame". You do the same for the glass, naming it "Window_Glass".
        
    2. Later, when you use a Join Geometry node to combine them, you might want to debug an issue. When you view the data stream before the join using a Viewer node, the spreadsheet will clearly label which geometry is which ("Window_Frame" or "Window_Glass").
        
    3. This prevents confusion and makes it much easier to inspect and verify the attributes of each part individually before they are merged.