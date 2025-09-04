**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Converts a floating-point number into an integer using one of several rounding methods.

**Key Properties & Settings:**

- **Float (Input):** The float value to be converted.
    
- **Rounding Mode (Property):** Determines the logic used for the conversion:
    
    - **Round:** Rounds to the nearest integer (e.g., 2.7 becomes 3, 2.4 becomes 2).
        
    - **Floor:** Always rounds down to the nearest integer (e.g., 2.7 becomes 2).
        
    - **Ceiling:** Always rounds up to the nearest integer (e.g., 2.1 becomes 3).
        
    - **Truncate:** Removes the decimal part, effectively rounding towards zero (e.g., 2.7 becomes 2, -2.7 becomes -2).
        
- **Result (Output):** The final integer output.
    

**Practical Application:**  
This node is essential when you need to select a specific item from a collection using a continuous input like a slider or a texture. For instance, imagine you have a collection of three different window styles and you want to use a Noise Texture to randomly distribute these styles across the side of a building.

- **The Goal:** To randomly assign one of three distinct window styles (index 0, 1, or 2) to each window position on a building's façade.
    
- **The Problem:** A Noise Texture outputs a continuous float value (e.g., 0.68, 0.23, 0.95). The Instance Index socket, which selects which object to instance from a collection, requires a discrete integer. Directly plugging the noise texture into the index will result in implicit rounding that you can't control.
    
- **The Solution:** The Float to Integer node provides explicit control over this conversion.
    
    1. First, use a Map Range node to map the noise texture's output from its default 0-1 range to a 0-3 range (since you have 3 window styles).
        
    2. Connect the result of the Map Range node into the Float input of a Float To Integer node.
        
    3. Set the Rounding Mode to Floor. This is the most reliable method for this task, as it will convert any value from 0.0-0.99 into 0, 1.0-1.99 into 1, and 2.0-2.99 into 2.
        
    4. Connect the Result of this node into the Instance Index socket on your Instance on Points node.
        

This setup ensures that the continuous, random values from the noise texture are correctly and predictably converted into the specific integer indices needed to choose a window style, giving you a robust procedural system for adding variation to your building.