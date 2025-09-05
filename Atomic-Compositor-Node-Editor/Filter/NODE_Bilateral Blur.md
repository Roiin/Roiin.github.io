- **Editor:** Compositor Node Editor
    
- **Node Group:** Filter (Blur)
    
- **Core Function:** An advanced "edge-aware" blur. It smooths out surfaces and noise within an image but intelligently stops or reduces the blur when it encounters a sharp edge, thus preserving important details.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The image to be blurred.
        
    - **Determinator (Socket):** This is the "brain" of the node. It's a separate grayscale or color input that the node uses to decide where the edges are. If left unconnected, the node uses the input Image itself as the determinator.
        
    - **Iterations (Socket):** The number of times the blur is applied. Higher values give a smoother, more painterly result but take longer to process.
        
    - **Color Sigma (Socket):** A threshold that controls how similar colors must be to be blurred together. A higher value will blur across less similar colors, softening more details.
        
    - **Spatial Sigma (Socket):** Controls the overall radius or size of the blur in pixels.
        
- **Practical Application:** This node is a problem-solver, primarily used for high-quality denoising and creating stylized, non-photorealistic effects.
    
    - **Molecular (High-Quality Denoising):** This is its most powerful and common use, especially for noisy render passes like Ambient Occlusion (AO) or Indirect Lighting.
        
        1. Take your noisy AO pass and plug it into the Image socket.
            
        2. To get a perfect result, you need a clean "map" of your object's edges. The best determinator is often a combination of the Normal pass and the Depth pass.
            
        3. Plug this clean edge map into the Determinator socket.
            
        4. The node will now heavily blur the AO pass, smoothing out all the noise, but it will use the Normal and Depth information to perfectly preserve the sharp contact shadows and edges. This gives you a clean, noise-free AO pass in a fraction of the time it would take to render it with high samples.
            
    - **Molecular (Beauty Retouching):** It can be used as a "digital skin softener." By creating a soft mask around a character's face and applying a gentle Bilateral Blur, it can smooth out skin texture and blemishes while preserving the sharp edges of the eyes, nose, and mouth, resulting in a clean but not overly "plastic" look.
        
    - **Organic (Painterly / Toon Shader Effect):** By increasing the Iterations and Spatial Sigma to high values, you can create a stylized, artistic effect. The blur will average out large areas of similar color, giving the image a smooth, painted appearance while keeping the main outlines of objects sharp. This can be the foundation for a non-photorealistic or "cel-shaded" look directly in the compositor.
        
    - **Organic (Controlled Light Bleed):** By using a heavily blurred version of your image as the Image input but the original sharp image as the Determinator, you can create a beautiful, edge-aware light bleed or bloom effect. The light will appear to softly wrap around the edges of objects in a much more organic way than a simple Glare or Blur node could achieve.