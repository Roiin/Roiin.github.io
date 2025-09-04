**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Rotates entire hair curves around a specified axis, effectively twisting them in place.

**Key Properties & Settings:**

- **Factor (Input):** A global multiplier for the rotation Angle.
    
- **Angle (Input):** The amount of rotation to apply, in radians.
    
- **Axis (Input):-** A vector that defines the axis of rotation for each curve. By default, it uses the tangent at the root, which causes the hair to spin around its own base.
    
- **Random Offset (Input):** Adds a random amount to the Angle for each individual hair curve, preventing a uniform, robotic look.
    
- **Lock Ends (Input):** When enabled, the rotation axis is defined by the line connecting the root and the tip of the curve. This is useful for rotating flat, ribbon-like hairs.
    

**Practical Application:**  
This node is useful for controlling the orientation or "roll" of hairs that have a non-circular profile, such as creating a field of grass where the blades need to be twisted.

- **The Goal:** To add natural variation to a field of procedurally generated grass by making each blade twist randomly around its own vertical axis.
    
- **The Problem:** When you instance a flat grass blade model on a field, all the blades will have the same orientation, facing the same direction. This looks extremely artificial. You need to introduce a random "roll" to each blade.
    
- **The Solution:** Use the Rotate Hair Curves node to apply a random twist before instancing the blade geometry.
    
    1. First, generate the initial curves that will define the grass strands. These are typically straight vertical lines.
        
    2. Use a Rotate Hair Curves node.
        
        - Leave the Axis input disconnected to use the default (the curve's own tangent, which is "up" for vertical lines).
            
        - Set the main Angle to 0.
            
        - Set the Random Offset to 6.283 (which is 2 * PI, or a full 360-degree circle). This means each curve will be given an additional random rotation somewhere between 0 and 360 degrees.
            
    3. The output of this node is a set of curves, each with a unique rotation value stored as an attribute.
        
    4. You can now use these curves in a Set Hair Curve Profile or Instance on Points node with your grass blade model. The instanced blades will inherit this random twist, ensuring that the field of grass looks much more natural and less like a repeating pattern.