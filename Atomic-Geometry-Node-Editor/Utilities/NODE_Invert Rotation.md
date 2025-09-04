**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Rotation)

**Core Function:** Calculates the opposite of an input rotation, effectively "undoing" it.

**Key Properties & Settings:**

- **Rotation (Input):** The standard rotation value to be inverted.
    
- **Rotation (Output):** The resulting inverted rotation.
    

**Practical Application:**  
This node is essential for converting directions from world space into an object's local, rotated space. Imagine you are creating a procedural animal eye that rotates to look at a target. You also want to add a specular highlight to the eye's surface that correctly reflects a static light source in the scene.

- **The Goal:** To correctly orient a highlight on the surface of a moving eyeball so that it always appears to reflect a fixed light source.
    
- **The Problem:** The eyeball itself has a rotation to look at its target. The highlight is a piece of geometry on the eyeball's surface, so it inherits this rotation. The direction of the light source, however, exists in world space. You cannot directly align the highlight to the world light's direction because they are in different coordinate systems.
    
- **The Solution:** You must find out what the light's direction is relative to the rotated eyeball. This requires bringing the world light vector into the eyeball's local space by applying the inverse of the eyeball's rotation.
    
    1. First, calculate the Eyeball_Rotation needed to point the eye at its target (e.g., using Align Rotation to Vector).
        
    2. Feed this Eyeball_Rotation into an Invert Rotation node to get its inverse.
        
    3. Define the world direction vector of your light source (e.g., with a Vector node).
        
    4. Use a Vector Rotate node. Plug the light's world direction into the Vector socket and the inverted eyeball rotation into the Rotation socket.
        
    5. The output is the light's direction, but now expressed in the eyeball's local coordinates. You can now use this local direction vector with another Align Rotation to Vector node to orient the highlight instance correctly on the eye's surface.
        

No matter how the eyeball rotates to follow its target, the highlight will now shift its position on the surface realistically, always pointing towards the static world light.