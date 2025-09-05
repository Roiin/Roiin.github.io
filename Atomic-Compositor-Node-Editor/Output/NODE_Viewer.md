- **Editor:** Compositor Node Editor
    
- **Node Group:** Output
    
- **Core Function:** Provides a real-time preview of any point in the node tree, displaying the connected image data as a backdrop in the compositor or in the Image Editor. It is a non-destructive diagnostic and preview tool that does not affect the final render output.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** Receives the image stream you wish to inspect.
        
    - **Active State (Behavior):** Like the Composite node, only one Viewer node can be active at a time (indicated by a subtle icon in its header). The active viewer's content is what is displayed.
        
- **Practical Application:** The Viewer node is the single most essential tool for understanding and debugging your node tree. Its entire purpose is to let you "see" what each node is doing at every step.
    
    - **Molecular (Step-by-Step Debugging):** If your final composite looks wrong, the Viewer is your best friend. You can connect it to the output of each node in your chain, one by one.
        
        - Connect to Render Layers: Is my base render correct?
            
        - Connect to ID Mask: Is my mask for the character working?
            
        - Connect to Color Balance: Is my color correction being applied correctly?
            
        - This allows you to instantly pinpoint exactly which "atom" in your "molecule" is causing the problem.
            
    - **Molecular (Visualizing Data Passes):** The Viewer is the only way to see non-color data. By connecting the Depth or Normal pass from a Render Layers node directly to the Viewer, you can see the raw data map. This is crucial for verifying that your depth information is correct before you feed it into a Defocus node or for understanding what your Cryptomatte pass looks like.
        
    - **Organic (A/B Comparison Workflow):** The shortcut feature is a game-changer. Imagine you are trying to decide between two blur effects.
        
        1. Create two branches in your node tree, one for each blur effect (Blur vs. Bokeh Blur).
            
        2. Select the Blur node and press Ctrl+1. This creates and assigns Viewer #1.
            
        3. Select the Bokeh Blur node and press Ctrl+2. This creates and assigns Viewer #2.
            
        4. Now, by simply pressing the 1 and 2 keys on your keyboard, you can instantly flip back and forth between the two results in the backdrop, allowing for a rapid and direct visual comparison without ever touching your mouse. This dramatically speeds up creative decision-making.