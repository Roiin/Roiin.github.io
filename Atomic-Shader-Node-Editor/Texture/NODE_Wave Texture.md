**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Generates a procedural pattern of parallel bands or concentric rings, which can be warped with built-in noise distortion.

**Key Properties & Settings:**

- **Color / Factor (Outputs):** Provides the wave pattern as either a color gradient or a grayscale factor. The Factor is typically used to drive ColorRamp or Bump nodes.
    
- **Type (Property):** The primary control, switching between two distinct modes:
    
    - **Bands:** Creates straight, parallel lines.
        
    - **Rings:** Creates concentric circles radiating from a central point.
        
- **Bands/Rings Direction (Property):** Determines the orientation of the pattern. X, Y, or Z aligns bands perpendicular to that axis. Spherical causes rings to radiate outwards from the object's origin.
    
- **Distortion (Input):** The most powerful artistic control. It adds noise to the pattern, warping the perfectly straight bands or clean rings into organic, wavy shapes. Detail, Detail Scale, and Roughness further refine this distortion.
    
- **Scale (Input):** Controls the frequency or spacing of the waves. Higher values create more, thinner lines.
    
- **Wave Profile (Property):** Switches between a smooth Sine wave profile (like ripples) and a sharp Saw profile (like a repeating ramp).
    

**Practical Application:**  
This node is the definitive tool for creating procedural **wood grain**, specifically the growth rings seen on the cross-section of a cut log.

The problem with using a stretched Noise Texture is that while it can create the grain for a wooden plank, it cannot create the characteristic concentric circles of a tree's growth rings. You need a pattern that radiates from a central point. The Wave Texture node is the perfect solution.

1. Start by adding a Wave Texture node to your material.
    
2. Set its Type to Rings and the Rings Direction to Spherical. This will create a pattern of perfect circles emanating from the object's origin.
    
3. Real tree rings are not perfect circles; they are irregular and wavy. This is where the node's power lies. Increase the Distortion value to a moderate amount (e.g., 5.0). This will warp the rings with noise, making them look far more organic and natural. Adjust the Detail Scale to control the "waviness" of the distortion.
    
4. Connect the Factor output of the Wave Texture to the Fac input of a ColorRamp node. In the ColorRamp, define the colors for the light and dark bands of the wood.
    
5. Plug the ColorRamp's Color output into the Base Color of a Principled BSDF. The result is a highly realistic and art-directable procedural texture of wood end-grain, which would be impossible to create with other noise types.