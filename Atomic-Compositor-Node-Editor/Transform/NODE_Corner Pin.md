- **Editor:** Compositor Node Editor  
- **Node Group:** Transform
    
- **Core Function:** Distorts an image by mapping its four corners to four specified points. It allows for precise, manual perspective warping and is ideal for placing an image onto a non-rectangular or perspectivized flat surface.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The image to be distorted.
        
    - **Corner Sockets (BL, BR, TL, TR):** Four Vector input sockets representing the Bottom-Left, Bottom-Right, Top-Left, and Top-Right corners. You provide the X/Y coordinates where each corner of the input image should be pinned.
        
    - **Interactive Gizmo (Behavior):** When the node is selected and gizmos are enabled, four handles appear in the Viewer backdrop, allowing you to intuitively drag each corner pin to its desired location.
        
- **Outputs:**
    
    - **Image (Socket):** The final, perspectively distorted image.
        
    - **Plane (Socket):** A black-and-white mask of the resulting distorted shape.
        
- **Practical Application:** This node is essential for any task that requires fitting an image onto a surface in perspective, especially when motion tracking data isn't available or isn't suitable.
    
    - **Molecular (Manual Screen Replacement):** For a static or simple shot where a full plane track is overkill, the Corner Pin is perfect.
        
        1. Add the Corner Pin node to the image you want to place on a screen.
            
        2. Using the interactive gizmo in the Viewer, simply drag each of the four corner pins to the corresponding corners of the screen in your footage.
            
        3. The node will perfectly warp the image to fit. This is great for still photos or shots with very simple camera moves where you can manually animate the corner positions.
            
    - **Organic (Attaching to 4-Point Tracks):** This is its most powerful VFX application. The Plane Track Deform node uses a special "plane track," but you can also use four standard point trackers to drive a Corner Pin.
        
        1. In the Movie Clip Editor, create four separate Track Position tracks, one for each corner of the surface (e.g., the four corners of a painting on a wall).
            
        2. In the compositor, add a Corner Pin node.
            
        3. Add four Track Position nodes, each one set to one of your corner tracks.
            
        4. Connect the X/Y outputs of each Track Position node to the corresponding vector input on the Corner Pin node (you'll need Combine XYZ nodes to turn the X/Y into vectors).
            
        5. This "organism" creates a robust "four-corner pin" that will perfectly stick your image to the tracked surface, often providing more stability and control than a dedicated plane track.
            
    - **Organic (Creating Fake 3D Flips):** You can use the Corner Pin to animate a 2D layer as if it's a card flipping in 3D space.
        
        1. Start with the four corners in their normal rectangular positions.
            
        2. To make it look like it's rotating away from the camera, animate the X coordinates of the right-side pins (BR, TR) so they move inwards towards the left-side pins.
            
        3. The image will appear to turn and recede in perspective. This is a classic and computationally cheap motion graphics technique for creating pseudo-3D effects.