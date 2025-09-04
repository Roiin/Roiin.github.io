- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Topology)
    
- **Core Function:** For a specified spline, this node sorts all of its control points based on a weight value and then outputs the index of the point at a specific rank in that sorted list (e.g., the 1st, 2nd, or last point).
    
- **Key Properties & Settings:**
    
    - **Curve Index (Socket - Input):** An integer specifying which spline to search within (in a multi-spline object).
        
    - **Weights (Socket - Input):** A field of values used to sort the points. Points with lower weights are ranked first. By default, this uses the point's index.
        
    - **Sort Index (Socket - Input):** An integer that picks a point from the sorted list. A value of 0 picks the point with the lowest weight, 1 picks the second-lowest, and so on.
        
    - **Point Index (Socket - Output):** The primary output; the original index of the single control point that was selected.
        
    - **Total (Socket - Output):** The total number of control points on the specified spline.
        
- **Practical Application:** This node is perfect for finding and placing objects at specific key locations on a curve, like attaching a lantern to the lowest point of a hanging chain.
    
    1. Imagine you have a curve object containing several separate splines, each representing a hanging chain or vine.
        
    2. **The Goal:** You want to procedurally find the single lowest point of each individual chain and instance a lantern there.
        
    3. You would iterate through each spline (using its index as the Curve Index).
        
    4. Use the Points of Curve node. To find the lowest point, you need to sort by the Z-position. So, you connect the Z component of the Position node to the Weights input.
        
    5. You want the point with the lowest Z-position, which will be the first in the sorted list. So, you set the Sort Index to 0.
        
    6. The Point Index output now gives you the index of the single lowest point for that specific chain.
        
    7. You can then create a selection that is True only for this index and use it with an Instance on Points node to place your lantern. Repeating this for each spline ensures every chain gets a lantern at its lowest point, no matter how it's shaped or positioned.