- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Topology)
    
- **Core Function:** For each control point in a curve object that contains multiple splines, this node identifies which spline the point belongs to. It acts as a lookup tool to get spline-level information from a point-level context.
    
- **Key Properties & Settings:**
    
    - **Point Index (Socket - Input):** The index of the control point to be queried. By default, this uses the Index of the current point being evaluated.
        
    - **Curve Index (Socket - Output):** The primary output; an integer representing the index of the spline (or "curve") that the specified point is a part of.
        
    - **Index in Curve (Socket - Output):** The point's local index within its own spline, starting from 0.
        
- **Practical Application:** This node is essential for creating varied effects across multiple splines in a single object. Imagine you are creating an octopus, where all eight tentacles are drawn as separate splines within a single curve object.
    
    1. **The Goal:** You want to give each of the eight tentacles a slightly different random color or thickness.
        
    2. **The Problem:** A standard Random Value node will give a different random value to every single point on all the tentacles, resulting in a chaotic, rainbow-colored mess. You need one consistent random value for each entire tentacle.
        
    3. **The Solution:** Use the Curve of Point node. The Curve Index output will be 0 for all points on the first tentacle, 1 for all points on the second, and so on.
        
    4. Feed this Curve Index into the ID socket of a Random Value node.
        
    5. The Random Value node will now generate only eight unique random numbers. The value for every point on the first tentacle will be the same, the value for every point on the second tentacle will be the same but different from the first, and so on.
        
    6. You can now use this consistent, per-tentacle random value to drive the Hue in a color shader or to control the overall thickness in a Set Curve Radius node, allowing you to easily add natural variation to your creature.