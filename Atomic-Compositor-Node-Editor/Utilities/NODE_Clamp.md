- **Editor:** Compositor Node Editor  
- **Node Group:** Utilities
    
- **Core Function:** Constrains or "clamps" an input numerical value, forcing it to stay within a specified minimum and maximum range. Any values below the minimum are raised to the minimum, and any values above the maximum are lowered to the maximum.
    
- **Key Properties & Settings:**
    
    - **Value (Socket):** The numerical input to be clamped.
        
    - **Min (Socket):** The lower boundary of the allowed range.
        
    - **Max (Socket):** The upper boundary of the allowed range.
        
- **Outputs:**
    
    - **Result (Socket):** The clamped value.
        
- **Practical Application:** The Clamp node is a "safety valve." It's used to prevent mathematical operations from producing extreme or invalid numbers (like negative colors or brightness values over 1.0) that could cause artifacts or errors in subsequent nodes.
    
    - **Molecular (Sanitizing Mask Values):** This is its most common and critical use. When creating masks, especially for use in Factor inputs, the values absolutely must be between 0 and 1. If you perform a Math (Multiply) operation on a mask that has some gray values, you could end up with values greater than 1.0. This can cause strange "over-mixing" artifacts.
        
        1. Perform your mask manipulation (e.g., Brightness/Contrast or Math).
            
        2. Immediately follow it with a Clamp node with Min=0 and Max=1.
            
        3. The output is now a "sanitized" mask that is guaranteed to be safe for use in any Factor input.
            
    - **Molecular (Controlling HDR Values):** When working with High Dynamic Range (HDR) images, some pixels can have brightness values far greater than 1.0 (e.g., the sun might have a value of 50.0). If you need to feed this data into a system that expects a Low Dynamic Range (LDR) input (0-1), a Clamp node is the simplest (though most destructive) way to do it. Clamping with Max=1 will "clip" all the highlights to pure white.
        
    - **Organic (Creating High-Pass Filters):** You can use Clamp to isolate specific value ranges. To create a mask of only the mid-tones:
        
        1. Take your grayscale image.
            
        2. Use a Math (Subtract) node to subtract 0.5.
            
        3. Use an Absolute Math node.
            
        4. Now, the brightest and darkest parts of your original image have high values, and the mid-tones are near zero.
            
        5. Use a Clamp node to keep only the values between, for example, 0 and 0.1, and a Map Range to expand this back to a 0-1 range. You have now isolated the mid-tones.