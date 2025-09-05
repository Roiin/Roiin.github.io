- **Editor:** Compositor Node Editor
- **Node Group:** Utilities
    
- **Core Function:** Displays two input images side-by-side or top-to-bottom within a single **Viewer** node for direct visual comparison.
    
- **Key Properties & Settings:**
    
    - Factor ([Socket]): A value from 0 to 1 that controls the position of the dividing line between the two images.
        
    - Image ([Socket]): The first image input, typically displayed on the right (for a vertical split) or top (for a horizontal split).
        
    - Image ([Socket]): The second image input, displayed on the left (for a vertical split) or bottom (for a horizontal split).
        
    - Axis ([Property]): Determines if the split is vertical (**X**) or horizontal (**Y**).
        
- **Practical Application:**
    
    - **Molecular (Before & After Grade):** The most fundamental use for this node is to evaluate the effect of a color correction "molecule." Connect your raw render pass to one **Image** input and the output of your color grading nodes (e.g., **Color Balance**, **RGB Curves**) to the other. By piping this **Split** node into a **Viewer**, you can instantly see a side-by-side comparison, allowing for precise and interactive adjustments to the grade.
        
    - **Molecular (Matte Verification):** When pulling a key or creating a mask, it's crucial to check its quality against the final result. Connect the alpha channel output from a **Keying** node (or a chain of **Matte** nodes) to one input of the **Split** node, and connect your final composited image to the other. This allows you to simultaneously see the clean matte and how it's affecting the final composite, helping you spot edge issues or chatter.
        
    - **Organic (Workflow Sanity Check):** In a complex "organism" like a full keying and despill pipeline, the **Split** node is an essential diagnostic tool. You can use it to compare the original plate against the final keyed and despilled result, or to compare the core matte against the softer edge matte. This provides immediate visual feedback at critical stages, ensuring that each part of the complex process is working as intended before moving on.
        
    - **Organic (Shot Transition Planning):** As suggested in the manual, this node is excellent for ensuring visual continuity between shots. In the compositor, load the last frame of Shot A using an **Image** node and the first frame of Shot B in another. By feeding both into the **Split** node, you can compare composition, lighting, and color grading to ensure a smooth and non-jarring transition for the viewer.