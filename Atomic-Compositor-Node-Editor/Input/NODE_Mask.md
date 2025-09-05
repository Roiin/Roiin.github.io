- **Editor:** Compositor Node Editor
    
- **Node Group:** Input
    
- **Core Function:** Imports a vector-based, animatable mask created in Blender's Image or Movie Clip Editor, providing a precise grayscale matte for isolating specific regions of an image.
    
- **Key Properties & Settings:**
    
    - **Mask Data-Block (Property):** The menu to select the specific Mask data-block you want to use.
        
    - **Size Source (Property):** Determines the mask's resolution. Scene Size makes it match the final render resolution, while Fixed uses an absolute pixel value.
        
    - **Use Feather (Property Checkbox):** Toggles whether to use the soft, feathered edges defined for the mask's splines.
        
    - **Motion Blur (Property Checkbox):** When enabled for an animated mask, it generates a blurred matte based on the mask's movement across multiple frames, essential for matching motion-blurred footage.
        
    - **Samples (Property):** Sets the quality of the motion blur. Higher values are smoother but slower to calculate.
        
    - **Shutter (Property):** Controls the duration (length of the blur streaks) for the motion blur effect.
        
    - **Mask (Socket):** Outputs a grayscale alpha matte (white for the area inside the mask, black for the outside, with gray values for feathered edges).
        
- **Practical Application:** This node is the digital equivalent of a precision scalpel, allowing for targeted adjustments and effects.
    
    - **Molecular (Secondary Color Grading):** This is its most common artistic use. Create a mask that follows an actor's face. Use the Mask output as the Factor for a Color Balance node to brighten their face, or a Hue Saturation Value node to subtly change their eye color, all without affecting the background. You could isolate a single red car in a black-and-white city scene this way.
        
    - **Molecular (Garbage Matte):** A critical step in green screen VFX. Often, a shot with a green screen will have lights, crew, or tracking markers visible at the edges of the frame. Use the Mask node to draw a rough, animated shape that completely removes these "garbage" elements before the footage is sent to the Keying node, resulting in a much cleaner final key.
        
    - **Organic (Controlled Depth of Field):** While the Defocus node uses Z-depth data for realistic DoF, sometimes you need artistic control.
        
        1. Duplicate your main footage stream. Heavily blur one version using a Blur node.
            
        2. Create a precise, animated mask that follows the one character or object you want to remain perfectly sharp.
            
        3. Use the Mask output as the Factor in a Mix node to combine the sharp and blurry versions. The result is a highly art-directed focus effect where your subject "pops" from a blurry background, a technique often used in commercials.
            
    - **Organic (Custom Animated Transitions):** Animate a mask's shape and position to create a custom transition. For example, animate a circular mask scaling up from the center of the screen to create a classic "iris wipe." Or animate a jagged-edged mask tearing across the screen. Use this animated Mask output as the Factor in a Mix node to transition between two different video clips.