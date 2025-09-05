- **Editor:** Compositor Node Editor  
- **Node Group:** Mask
    
- **Core Function:** Generates a simple, animatable elliptical or circular mask. It is a fundamental procedural tool for creating vignettes, circular mattes, and soft-edged spotlights.
    
- **Key Properties & Settings:**
    
    - **Width / Height (Sockets):** Controls the dimensions of the ellipse as a fraction of the total image width. Keeping Width and Height equal will produce a perfect circle.
        
    - **X / Y (Sockets):** Sets the position of the ellipse's center. (0.5, 0.5) is the exact center of the screen.
        
    - **Rotation (Socket):** Rotates the ellipse around its center point.
        
    - **Interactive Gizmo (Behavior):** When the node is selected and gizmos are enabled, a visual handle appears in the Viewer backdrop, allowing you to intuitively position, scale, and rotate the mask with the mouse.
        
- **Outputs:**
    
    - **Mask (Socket):** The final black-and-white elliptical mask.
        
- **Practical Application:** This node is the go-to for any effect that requires a circular or oval shape, especially vignettes and localized adjustments.
    
    - **Molecular (Procedural Vignette):** This is its most common and powerful use.
        
        1. Create an Ellipse Mask and scale it to be slightly smaller than the full frame (e.g., Width/Height of 0.9).
            
        2. Feed the Mask output into a Blur node with a large value to create very soft, feathered edges.
            
        3. Invert the blurred mask.
            
        4. Use this final mask to Multiply a dark color over your image, or as the Factor in a Mix node to blend in a darkened version of your image. This "molecule" creates a perfect, fully controllable vignette.
            
    - **Molecular (Spotlight Effect):** To draw the viewer's eye to a specific character or object:
        
        1. Create an Ellipse Mask and position it over your subject.
            
        2. Blur the mask to create a soft falloff.
            
        3. Use this blurred mask as the Factor for a Color Balance or Exposure node to brighten the area inside the circle, creating a "spotlight" effect.
            
    - **Organic (Animated Transitions):**
        
        - **Iris Wipe:** Create a circular Ellipse Mask (equal Width/Height). Animate the Width and Height values from 0 up to a large number (e.g., 2.0) to create a classic "iris in" or "iris out" transition.
            
        - **Clock Wipe:** Use a Gradient node set to Angular. Multiply this with a circular Ellipse Mask. The result is a radial gradient that can be animated with a Color Ramp to create a "clock wipe" transition.
            
    - **Organic (Faking a Magnifying Glass):**
        
        1. Create a circular Ellipse Mask and position it.
            
        2. Duplicate your image stream. On one branch, use a Transform node to scale the image up slightly.
            
        3. Use a Mix node. Connect the original image to the top, the scaled-up version to the bottom, and the circular mask to the Factor. The result is a circular area that appears magnified. Composite a magnifying glass frame on top to complete the effect.