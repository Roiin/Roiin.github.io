**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Field)

**Core Function:** Calculates and outputs the minimum and maximum values from a field of data over a given domain.

**Key Properties & Settings:**

- **Data Type (Property):** Sets the type of data to be compared: Float, Integer, or Vector.
    
- **Domain (Property):** The attribute domain (e.g., Points, Instances) over which the minimum and maximum are found.
    
- **Value (Input):** The field of values that will be evaluated.
    
- **Group ID (Input):** An integer field used to partition the calculation. Elements with the same ID are grouped together, and a Min/Max is found for each group independently.
    
- **Min (Output):** The lowest value found within a given group.
    
- **Max (Output):** The highest value found within a given group.
    

**Practical Application:**  
This node is essential for automatically normalizing a range of values, which is often required when working with shaders or color ramps. Imagine you are procedurally generating a tree and want to apply a color gradient along its height, so the base of the trunk is dark and the highest point is light.

- **The Goal:** To apply a color gradient that perfectly maps to the tree's actual height, regardless of how tall or short the tree is.
    
- **The Problem:** A Color Ramp node operates on a standard 0.0 to 1.0 range. A procedural tree's height, however, might be 5 units, 20 units, or any other value. If you directly use the Z-position of the tree's vertices as the factor for the color ramp, the gradient will be incorrect and "clamp" at the 1.0 meter mark, leaving the rest of the tree a solid color.
    
- **The Solution:** You need to remap the tree's height range to the color ramp's 0-1 range. The Field Min & Max node is the key to finding this range procedurally.
    
    1. First, isolate the height component of your tree's geometry by using a Separate XYZ node on the Position field and taking the Z output.
        
    2. Feed this Z value into the Value input of a Field Min & Max node.
        
    3. The Min output now holds the lowest Z-value of your tree, and the Max output holds the highest.
        
    4. Use a Map Range node.
        
        - Plug the Z value into the Value input.
            
        - Plug the Min from the Field Min & Max node into the From Min input.
            
        - Plug the Max into the From Max input.
            
        - Leave To Min at 0.0 and To Max at 1.0.
            
    5. The output of the Map Range node is a perfectly normalized value. Plug this into the Factor of your Color Ramp.
        

Now, the color gradient will dynamically stretch to fit the exact height of any tree you generate. The darkest color will always be at the very bottom and the lightest color at the very top, creating a robust and reusable material setup.