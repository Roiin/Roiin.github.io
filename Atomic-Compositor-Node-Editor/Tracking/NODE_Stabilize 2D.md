- **Editor:** Compositor Node Editor
    
- **Node Group:** Distort
    
- **Core Function:** Applies 2D stabilization data (location, rotation, and scale) from the Movie Clip Editor to an image sequence. It is used to remove camera shake or to transfer motion from one element to another.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The image sequence or footage to be stabilized.
        
    - **Movie Clip (Property):** Selects the movie clip that contains the pre-calculated 2D stabilization data.
        
    - **Invert (Property Checkbox):** This is a critical feature. It reverses the stabilization motion. If the original stabilization moves the image left to counteract a camera pan to the right, Invert will apply a move to the right.
        
- **Outputs:**
    
    - **Image (Socket):** The transformed image, either stabilized or with motion applied.
        
- **Practical Application:** This node is the core of two very different but equally important professional VFX workflows: stabilizing shaky footage and transferring motion to CG elements.
    
    - **Molecular (Stabilizing Shaky Footage):** This is its most direct use.
        
        1. In the Movie Clip Editor, track a high-contrast feature in your shaky footage and enable 2D Stabilization.
            
        2. In the compositor, connect your shaky footage (from a Movie Clip node) to the Image input of the Stabilize 2D node.
            
        3. Select the correct movie clip. The output will be a rock-steady version of your footage. **Note:** This will cause black, empty borders to appear as the image moves to compensate. You will need to use a Transform node to scale the stabilized footage up slightly to hide these edges.
            
    - **Organic (The Professional "Stab/Comp/Destab" Workflow):** This is the gold standard for integrating CG elements into shaky footage. It produces a flawless result where the CG element perfectly inherits the camera's motion.
        
        1. **Stabilize:** First, stabilize your live-action plate using the Stabilize 2D node as described above. The output is a perfectly steady shot.
            
        2. **Composite:** Alpha Over your CG element (which is also perfectly steady) onto this stabilized plate. Because both are steady, the composite is easy and clean.
            
        3. **De-stabilize:** Take the output of your composite (CG + steady background) and feed it into a second Stabilize 2D node. This time, **check the Invert box**.
            
        4. This "organism" re-introduces the original camera shake to the entire composite. The result is an image where your CG element and the live-action footage share the exact same jitter and motion, making the integration completely seamless and believable.
            
    - **Organic (Transferring Motion to Graphics):** You can use the Invert function to make a graphic "stick" to a point in the footage without stabilizing the whole shot.
        
        1. Track a point where you want your graphic to be. Enable stabilization for that track.
            
        2. In the compositor, take your graphic (e.g., from a Text or Image node) and use a Transform node to place it.
            
        3. Feed the transformed graphic into a Stabilize 2D node with Invert checked.
            
        4. Alpha Over this result onto your original, shaky footage. The graphic will now inherit the inverse of the stabilization (the original shake), making it appear locked to the tracked point in the scene.