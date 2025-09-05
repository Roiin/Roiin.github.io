- **Editor:** Compositor Node Editor  
- **Node Group:** Filter
    
- **Core Function:** An adaptive filter designed to reduce "fireflies" (single, bright outlier pixels) and blotchy noise in an image. It works by analyzing the complexity of a pixel's neighborhood and applying a blur only to areas of low complexity (smooth surfaces), leaving detailed areas untouched.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input.
        
    - **Threshold (Socket):** The main control. This value determines what the node considers a "simple" area versus a "complex" one. Higher values will cause more of the image to be blurred.
        
    - **Neighbor (Socket):** A secondary threshold that can help preserve texture details.
        
    - **Fac (Socket):** A standard factor to blend between the original and the despeckled image.
        
- **Practical Application:** While largely superseded by the AI-based Denoise node for general render denoising, Despeckle is still a useful tool for specific problems, particularly firefly removal and for cleaning up procedural textures.
    
    - **Important Context (vs. Denoise node):** The Denoise node is a powerful, "smart" tool that reconstructs an image based on AI training data and is far superior for cleaning up general Cycles render noise. The Despeckle node is a simpler, statistical filter that is more like a "smart blur." Its strength lies in its speed and its ability to target only specific types of noise.
        
    - **Molecular (Firefly Removal):** This is its most effective use case. Sometimes a render will have isolated, super-bright pixels ("fireflies") that the main Denoise node might miss or smudge unnaturally.
        
        1. In your Render Properties, under Sampling -> Clamping, setting Indirect Light to a value around 10.0 is the best way to prevent fireflies.
            
        2. However, if you still have them, the Despeckle node can be used. It will identify these isolated bright pixels in an otherwise smooth area and average them out with their neighbors, effectively removing them.
            
    - **Molecular (Cleaning Procedural Textures):** When you generate a procedural Noise or Musgrave texture, it can sometimes have very high-frequency, "speckled" detail. If you want a smoother, more blotchy pattern, running the texture through a Despeckle node can be a quick way to simplify it and remove the fine-grained noise before using it as a mask or displacement map.
        
    - **Organic (Layered Denoising):** For very difficult, noisy shots, you can use Despeckle as a pre-filter.
        
        1. First, run your noisy render through a Despeckle node with a low threshold to specifically target and eliminate the worst fireflies.
            
        2. Then, take the output of the Despeckle node and feed it into the main Denoise node.
            
        3. This "molecule" pre-cleans the image of the most extreme noise, which can sometimes help the AI denoiser produce a cleaner and more stable final result.