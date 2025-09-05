- **Editor:** Compositor Node Editor
- **Node Group:** Utilities
    
- **Core Function:** Combines two separate image inputs, designated as Left and Right eye views, into a single, unified stereoscopic image stream.
    
- **Key Properties & Settings:**
    
    - Left ([Socket]): The image data intended for the left eye's view.
        
    - Right ([Socket]): The image data intended for the right eye's view.
        
- **Practical Application:**
    
    - **Molecular (Stereo Recombination):** This is the node's primary purpose. If you have processed your left and right eye views independently (for example, by separating them from a multi-view **Render Layers** node), this "atom" is the essential tool to merge them back into a single stereoscopic stream that Blender's other multi-view tools and output nodes can understand.
        
    - **Molecular (2D Element Placement):** To composite a 2D element (like a UI graphic or a lens flare) into a stereoscopic scene, you must give it parallax. Create a "molecule" by feeding your 2D element into two separate **Translate** nodes. Shift one slightly to the left and the other slightly to the right. Feed the left-shifted version into the **Left** input and the right-shifted version into the **Right** input of the **Switch View** node. The output is a new stereo element that appears to exist at a specific depth when composited over your main footage.
        
    - **Organic (Per-Eye VFX Workflow):** In high-end visual effects, sometimes an effect must be applied differently to each eye for realism. Consider an "organism" for adding a character's reflection into a car window in a stereo shot. The angle of reflection would be unique for each eye. You would build two parallel node trees: one for the left eye that composites the correctly distorted and positioned reflection, and a second tree for the right eye with its own unique reflection. The **Switch View** node is the final convergence point, taking the output of these two complex, parallel "organisms" and merging them into the final, convincing stereoscopic composite.
        
    - **Organic (Stereoscopic Conversion):** This node is fundamental to the "organism" of converting 2D footage to 3D. In that workflow, artists use rotoscoping and depth maps to separate a 2D image into multiple layers (e.g., foreground character, mid-ground car, background building). Each layer is then processed to create a left-eye view and a slightly offset right-eye view using **Displace** nodes driven by depth information. The **Switch View** node is used to recombine the left and right versions of each individual layer, which are then layered back together to construct the final stereoscopic image.