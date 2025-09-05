- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** An advanced, AI-accelerated filter that removes noise (graininess) from renders, particularly those made with path-tracing engines like Cycles. It allows artists to achieve clean, production-quality images with significantly lower render sample counts, dramatically reducing render times.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The main noisy color input from your Render Layers (the "beauty pass").
        
    - **Normal (Socket):** An optional but highly recommended input for the Denoising Normal render pass. Providing this data helps the AI preserve fine geometric details and sharp edges.
        
    - **Albedo (Socket):** An optional but highly recommended input for the Denoising Albedo render pass. This "pure color" data helps the AI preserve texture detail and prevent blotchiness in the final result.
        
    - **HDR (Property Checkbox):** When enabled, it correctly processes color values outside the standard 0-1 range (like bright lights, emissives, and world backgrounds). This should almost always be enabled for modern workflows.
        
    - **Prefilter (Property):** Determines how the Normal and Albedo passes are handled. Accurate is the best choice for noisy renders, as it cleans the guiding passes before denoising the main image, leading to the best detail preservation.
        
- **Practical Application:** This node is a cornerstone of any modern Cycles rendering workflow. Its primary purpose is to save immense amounts of time.
    
    - **Molecular (Production Denoising):** This is its essential and intended use.
        
        1. In your View Layer Properties, under Passes -> Denoising Data, enable Denoising Normal and Denoising Albedo.
            
        2. In the compositor, connect the Image, Denoising Normal, and Denoising Albedo outputs from your Render Layers node to the corresponding inputs on the Denoise node.
            
        3. The output of this node is your new, clean "beauty pass" that you should use for the rest of your composite. This "molecule" allows you to render scenes at 128 or 256 samples and get a result that looks as clean as if it were rendered with 1000+ samples.
            
    - **Organic (Denoising Individual Passes):** For maximum quality and control, you can denoise individual light passes before recombining them.
        
        1. Enable the Diffuse Direct, Diffuse Indirect, Glossy Direct, etc., passes in your View Layer.
            
        2. Use a separate Denoise node for each of these passes (they can all be guided by the same Denoising Normal and Albedo passes).
            
        3. Reconstruct your final image by Adding these now-clean passes back together. This can sometimes preserve detail better than denoising the combined "beauty pass," especially in complex lighting scenarios.
            
    - **Organic (Denoising External Footage):** While optimized for Cycles, the denoiser can also be used on noisy video footage or photos.
        
        1. Load your noisy footage with an Image or Movie Clip node.
            
        2. Connect it to the Image input of the Denoise node (you will not have Normal or Albedo passes in this case).
            
        3. The node will analyze the image and attempt to remove the grain. While not as effective as a dedicated video denoiser, it can be a surprisingly useful tool for cleaning up noisy plates in a pinch.