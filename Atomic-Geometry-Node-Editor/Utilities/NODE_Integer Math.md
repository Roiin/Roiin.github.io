**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Performs a variety of mathematical operations, such as addition, multiplication, and modulo, specifically on integer values.

**Key Properties & Settings:**

- **Operation (Dropdown):** Selects the mathematical function to perform on the inputs. Key operations include:
    
    - **Add/Subtract/Multiply/Divide:** Standard arithmetic functions.
        
    - **Minimum/Maximum:** Outputs the smaller or larger of two integer inputs.
        
    - **Modulo:** Outputs the remainder of a division. This is extremely useful for cyclical operations and pattern generation.
        
    - **Power:** Raises the first integer to the power of the second.
        
- **Value (Inputs):** One or more integer sockets. The number of inputs depends on the selected operation.
    
- **Value (Output):** The single integer result of the calculation.
    

**Practical Application:**  
The Modulo operation in this node is fundamental for creating repeating patterns. A classic example is generating a procedural brick wall with a running bond pattern, where every other row is shifted horizontally.

- **The Goal:** To create a staggered brick pattern by offsetting every odd-numbered row.
    
- **The Problem:** When you create a grid of points to instance bricks onto, they are perfectly aligned. You need a procedural way to identify and select "every other row" to move it.
    
- **The Solution:** The Modulo operator can determine if a row index is even or odd.
    
    1. Start with a Grid primitive. The row number for any point can be calculated by taking its Index and dividing it by the number of vertices in the X-direction (using an Integer Math: Divide operation).
        
    2. Take the resulting Row Index and feed it into another Integer Math node set to Modulo. Set the second input value to 2.
        
    3. The Result of this Row Index % 2 operation will be 0 for all even rows (0, 2, 4...) and 1 for all odd rows (1, 3, 5...).
        
    4. Use a Compare node to check if the result equals 1. This creates a Boolean selection that is True only for the points in the odd-numbered rows.
        
    5. Use this Boolean selection to drive a Set Position node, moving the selected points horizontally by half a brick's width.
        

When you instance your brick models onto this modified grid of points, they will be perfectly staggered, creating a classic, realistic brick wall pattern.