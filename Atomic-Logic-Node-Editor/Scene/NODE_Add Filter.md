- **Editor:** Logic Node Editor
    
- **Node Group:** Scene Part 2 - Post FX
    
- **Core Function:** Adds a selected 2D post-processing filter to the render stack.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A Boolean flow control to trigger the action.
        
    - **Setting (Filter Dropdown):** A list of available filters, including FXAA, HBAO, SSAO, Vignette, Brightness, Chromatic Aberration, Grayscale, Levels, Mist, Blur.
        
    - **Input (Pass Index):** The integer index where the filter will be placed in the stack.
        
    - **Output (Done):** A flow control pulse that activates after the filter is added.
        
- **Practical Application:** The primary way to enable visual effects. For example, adding a Grayscale filter when the player's health is critical, a Vignette when entering a dark area, or a Blur effect during a dizzying cinematic sequence.