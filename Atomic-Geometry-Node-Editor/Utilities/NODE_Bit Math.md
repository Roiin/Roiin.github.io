**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Performs low-level bitwise operations, such as AND, OR, and NOT, on 32-bit integer inputs.

**Key Properties & Settings:**

- **Operation (Dropdown):** Selects the bitwise function to perform.
    
    - **And:** Outputs a 1 in each bit position where both input integers have a 1.
        
    - **Or:** Outputs a 1 in each bit position where at least one of the input integers has a 1.
        
    - **Not:** Inverts the bits of the input integer.
        
    - **Shift:** Moves the bits of the first integer to the left or right.
        
    - **Rotate:** Rotates the bits of the first integer, wrapping them around.
        
- **A (Input):** The first integer value.
    
- **B (Input):** The second integer value, used for two-input operations like And and Or.
    

**Practical Application:**  
This node is ideal for managing multiple Boolean (on/off) options for a procedural asset using a single integer. This is a technique known as "bitmasking." Imagine you are building a complex procedural window and want to control several features like having an arch, a central mullion, or grilles.

- **The Goal:** To use a single integer slider to turn multiple features of a procedural window on or off.
    
- **The Problem:** Adding a separate Boolean checkbox for every single feature can make the node group's interface very cluttered and difficult to manage.
    
- **The Solution:** You can assign each feature to a specific bit of an integer (e.g., bit 0 for the arch, bit 1 for the mullion). The Bit Math (And) operation can then be used to check if a specific feature's bit is "turned on" in the master control integer.
    
    1. Let's define our features: Arch = 1 (binary 001), Mullion = 2 (binary 010).
        
    2. Create an integer input for your node group called "Window Features". If the user enters 3 (binary 011), it means they want both an arch and a mullion.
        
    3. To check if the arch should be built, use a Bit Math node set to And.
        
        - Connect the "Window Features" integer (3) to input A.
            
        - Connect an integer 1 (our arch "mask") to input B.
            
        - The result of 3 AND 1 is 1.
            
    4. Use a Compare node to check if this result is greater than zero. Since it is, the output is True. This Boolean can now be used in a Switch node to either create or bypass the geometry for the window's arch.
        
    5. Repeating this process with a mask of 2 for the mullion also yields a True result, while a mask of 4 (for a different feature) would yield False.
        

This method allows you to pack a large number of on/off toggles into a single, efficient integer attribute, keeping your interfaces clean and your logic organized.