- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Applies or removes lens distortion based on the precise distortion coefficients (K1, K2, K3) calculated in the Movie Clip Editor. It is the technically correct and most accurate way to match the lens distortion between CG elements and live-action footage.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The image or footage to be distorted or undistorted.
        
    - **Movie Clip (Property):** Selects the movie clip that contains the pre-calculated lens distortion model.
        
    - **Distortion Method (Property):** The critical switch for the node's function.
        
        - Undistort: Removes the distortion from the input image. This is used on the live-action plate to make it rectilinear (have perfectly straight lines).
            
        - Distort: Applies the distortion to the input image. This is used on a clean CG render to make it match the distortion of the original footage.
            
- **Practical Application:** This node is the heart of a professional VFX workflow for integrating CG into live-action. Its entire purpose is to solve the problem of mismatched lens characteristics between the real camera and the perfect virtual camera.
    
    - **Important Context (The Workflow):** You never composite clean CG onto a distorted plate. You must make them match first. There are two primary workflows:
        
    - **Organic (Workflow A - Distort CG):**
        
        1. In the Movie Clip Editor, use the Grid Detection or manual line tools to accurately calculate the lens distortion of your footage.
            
        2. In the compositor, take your clean CG render (from Render Layers).
            
        3. Feed it into a Movie Distortion node set to Distort. Select the correct movie clip.
            
        4. The output is now a distorted version of your CG that has the exact same lens properties as your footage.
            
        5. Alpha Over this distorted CG onto your original, distorted live-action footage for a perfect match.
            
    - **Organic (Workflow B - Undistort/Redistort Plate - Recommended):** This is the industry-standard method as it allows for easier compositing and transformations in a clean, rectilinear space.
        
        1. **Undistort:** Take your live-action footage and feed it into a Movie Distortion node set to Undistort. The output is a clean, straight-lined version of your plate.
            
        2. **Composite:** Do all your compositing work here. Alpha Over your clean CG element, add effects, perform transformations, etc. Everything is easier because you're not working with curved lines.
            
        3. **Redistort:** Take the final output of your composite and feed it into a second Movie Distortion node, this time set back to Distort.
            
        4. This "organism" re-applies the original, correct lens distortion to the entire shot, ensuring that both the live-action and CG elements are warped identically for a seamless final result. This is a non-destructive and highly flexible pipeline.