- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Read)
    
- **Core Function:** Analyzes an input curve object and outputs the total accumulated length of all its splines as a single float value.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The source curve to be measured. If not connected, it defaults to the geometry the modifier is on.
        
    - **Length (Socket - Output):** A single float value representing the total length of the curve.
        
- **Practical Application:** This node is perfect for creating procedural systems that adapt to a curve's overall size. Imagine you are building a fence along a winding path defined by a curve, and you want the fence posts to always be spaced approximately 2 meters apart, regardless of the path's length.
    
    1. Use the Curve Length node on your path curve to get its total length (e.g., 53.4 meters).
        
    2. Use a Math node to divide this total length by your desired spacing (53.4 / 2.0 = 26.7).
        
    3. Use another Math node set to 'Round' or 'Floor' to convert this into a whole number for the post count (e.g., 27).
        
    4. Feed this calculated count directly into the Count input of a Resample Curve node.
        
    5. The Resample Curve node now automatically generates the exact number of points needed to maintain that consistent 2-meter spacing. You can then instance your fence post models onto these points. Now, if you make the path curve longer or shorter in Edit Mode, the number of fence posts will update automatically to match.