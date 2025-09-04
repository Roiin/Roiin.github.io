**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Shader

**Core Function:** Renders the object as a completely transparent mask, punching a hole through all other objects and the background behind it in the final render.

**Key Properties & Settings:**

- **Holdout (Output):** The standard shader output. When connected to the Material Output, it flags the object to be rendered as a holdout mask, creating an area of zero alpha in the final image.
    

**Practical Application:**  
This node is a critical tool for visual effects compositing, specifically for integrating live-action footage with CG elements. Imagine you have filmed an actor and need to place them behind a 3D-rendered pillar made of **wood grain**.

The problem is that without a holdout, the rendered pillar will always appear in front of the live-action footage when composited. You would need to manually create a mask (rotoscope) for the actor in a separate program to composite them correctly, which is very labor-intensive. The Holdout node provides an elegant solution.

1. Create a simple 3D model that roughly matches the actor's form and animation (this is often called a "holdout matte").
    
2. Assign the Holdout shader to this stand-in model's material.
    
3. In your 3D scene, place the detailed wooden pillar and position the animated holdout model in front of it, aligned with the actor in your footage.
    
4. When you render the scene, the wooden pillar will render normally, but where the holdout model is, there will be a perfect, person-shaped hole of pure transparency in the image.
    
5. Finally, in your compositing software, you simply layer this CG render over your original video footage. The real actor will show through the hole, making it appear as if they are seamlessly integrated into the 3D scene and standing behind the pillar.