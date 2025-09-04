**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Remaps an input float value using a customizable curve widget, allowing for non-linear transformations.

**Key Properties & Settings:**

- **Value (Input):** The float value to be remapped. The node uses this as the X-coordinate on the curve graph to find the corresponding Y-coordinate.
    
- **Curve (Widget):** The primary interface for defining the remapping function. By adding and manipulating points, you draw a curve that dictates the output value for any given input.
    
- **Factor (Input):** A mixing factor that blends between the original input Value and the remapped value from the curve. A factor of 1.0 uses the full curve output.
    
- **Float (Output):** The final float value after being processed by the curve and the factor.
    

**Practical Application:**  
This node is perfect for artistically controlling the distribution of instanced objects. Imagine you are procedurally growing a tree and want to define the profile of where branches can spawn along the trunk—fewer at the very bottom, more dense in the middle, and tapering off again at the top.

- **The Goal:** To create a non-uniform, organic distribution of branches along a tree trunk.
    
- **The Problem:** A simple Distribute Points on Faces will spread the branch points evenly, which looks unnatural. You need to control the probability of a branch appearing at a certain height.
    
- **The Solution:** The Float Curve node can create a "probability profile" based on the trunk's height.
    
    1. Start with a line or cylinder representing the tree trunk. Get the Z-component of each point's position using a Separate XYZ node.
        
    2. Normalize this height to a 0-1 range using a Map Range node. This will be the input for the curve.
        
    3. Feed this normalized height into the Value input of the Float Curve node.
        
    4. In the curve widget, draw a shape that reflects your desired distribution: start the curve low on the left (bottom of the trunk), raise it in the middle, and lower it again on the right (top of the trunk).
        
    5. The Float output of this node is a value between 0 and 1 that represents the desired branch density at that height.
        
    6. You can now use this output as a selection mask. For example, use a Delete Geometry node on the points and compare the curve's output to a Random Value. Where the curve is high, more points will be kept; where it's low, more will be deleted.
        
    7. Instance your branch models on the remaining points.
        

The result is a tree with a natural, clumping distribution of branches that you can easily and visually art-direct by simply changing the shape of the curve.