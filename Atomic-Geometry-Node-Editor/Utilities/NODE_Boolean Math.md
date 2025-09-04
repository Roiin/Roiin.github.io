**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Performs a logical operation (such as AND, OR, NOT) on two boolean inputs to produce a single boolean output.

**Key Properties & Settings:**

- **Operation (Dropdown):** The logical function to be applied. The most common are:
    
    - **And:** Outputs True only if both inputs are True.
        
    - **Or:** Outputs True if at least one input is True.
        
    - **Not:** Outputs the opposite of the first input (the second input is ignored).
        
    - **Not Equal (XOR):** Outputs True if the inputs are different from each other.
        
- **Boolean (Inputs):** Two sockets for the Boolean values to be compared.
    
- **Boolean (Output):** The single Boolean result of the logical operation.
    

**Practical Application:**  
This node is fundamental for combining multiple conditions to create complex selections. Imagine you are procedurally adding fur to a zebra model. You want the fur to grow only on the white stripes, and only on the zebra's back, not its underbelly.

- **The Goal:** To create a single selection mask that isolates only the vertices on the zebra's back that are also part of a white stripe.
    
- **The Problem:** You can create a selection for the zebra's back (e.g., based on vertex height and normal direction). You can also create a separate selection for the white stripes (e.g., based on a color attribute). You need a way to combine these two separate masks to find the areas where they overlap.
    
- **The Solution:** The Boolean Math node in And mode is the perfect tool for this.
    
    1. First, generate a Boolean field for "Is on Back". This might involve checking if a vertex's Z-position is above a certain value.
        
    2. Second, generate another Boolean field for "Is White Stripe". This would likely come from comparing a color attribute against a threshold.
        
    3. Connect both of these Boolean results into a Boolean Math node.
        
    4. Set the Operation to And.
        
    5. The node will output True only for the vertices that satisfy both conditions. This combined Boolean field is the precise selection mask you need. You can now use it in a Distribute Points on Faces or Instance on Points node to ensure the fur only grows in the desired locations.