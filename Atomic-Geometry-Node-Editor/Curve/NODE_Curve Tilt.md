- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** For each control point on a curve, this node outputs the tilt value, which is the rotational angle (in radians) of the curve's normal around its tangent. This is essentially the "twist" of the curve at that point.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **Tilt (Socket - Output):** A float field representing the tilt angle in radians for each control point.
        
- **Practical Application:** This node allows you to align instanced geometry to the specific twist of a curve, which is essential for creating organic objects like vines with leaves.
    
    1. First, you create a curve that represents your main vine. In Edit Mode, you use the "Tilt" tool (Ctrl+T) to give the vine a natural, spiraling twist along its length.
        
    2. Next, you use Resample Curve to create evenly spaced points along the vine where you will place leaves.
        
    3. Use an Instance on Points node to place your leaf models on these points.
        
    4. **The Problem:** Without using the tilt information, all the leaves will stick out at the same angle, looking very unnatural and robotic, ignoring the vine's twist.
        
    5. **The Solution:** You need to construct a full rotation for the leaves.
        
        - First, use the Curve Tangent and Normal vectors to get the basic orientation.
            
        - Then, use the Curve Tilt node to get the specific twist angle at each point.
            
        - You can then use a Rotate Vector node to rotate the curve's Normal vector around its Tangent vector by the Tilt angle. This gives you the final, correct "up" direction for each leaf.
            
        - Feed these final tangent and rotated normal vectors into an Align Euler to Vector node to generate the final rotation for each leaf instance.
            
    6. The result is that the leaves now perfectly follow the twist of the vine, spiraling around it realistically, creating a much more believable and organic-looking plant.