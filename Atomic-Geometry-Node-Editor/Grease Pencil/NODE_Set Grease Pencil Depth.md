- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Grease Pencil (Write)
    
- **Core Function:** Sets the global depth ordering method for a Grease Pencil object, determining whether strokes are sorted by their layer order or by their actual position in 3D space.
    
- **Key Properties & Settings:**
    
    - **Grease Pencil (Socket - Input):** The source Grease Pencil geometry.
        
    - **Depth Order (Property):** The core control for the node:
        
        - **2D Layers:** Forces strokes to be drawn according to their layer order in the layer stack, from top to bottom. This is the traditional 2D animation method, where layers on top always render in front, regardless of their 3D position.
            
        - **3D Location:** Renders strokes based on their actual distance from the camera, like standard 3D objects. Strokes that are closer to the camera will correctly render in front of strokes that are further away, even if they are on a "lower" layer.
            
    - **Grease Pencil (Socket - Output):** The Grease Pencil geometry with the new depth order setting applied.
        
- **Practical Application:** This node is crucial when combining 2D and 3D animation techniques. Imagine you have a 2D animated character drawn in Grease Pencil walking through a 3D environment with pillars.
    
    1. **The Problem:** By default, Grease Pencil objects might use '2D Layers', meaning the entire character (all its layers) will either render completely in front of a pillar or completely behind it. The character cannot realistically walk around the pillar.
        
    2. **The Solution:** You use the Set Grease Pencil Depth node and set the Depth Order to '3D Location'.
        
    3. You also need to give the character's layers some actual depth separation in 3D space. For example, you might procedurally set the "Left_Arm" layer to be at Y=0.1, the "Torso" at Y=0.0, and the "Right_Arm" at Y=-0.1.
        
    4. Now, as the character walks past a pillar, their "Left_Arm" (which is physically closer to the camera) will correctly render in front of the pillar, while their "Torso" and "Right_Arm" will be correctly obscured behind it. This node is the key to enabling true 3D interaction for Grease Pencil characters.