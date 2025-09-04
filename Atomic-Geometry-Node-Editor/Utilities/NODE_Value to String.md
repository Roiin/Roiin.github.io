- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Converts a numerical input (either an Integer or a Float) into its string representation.
    
- **Key Properties & Settings:**
    
    - **Data Type (Property):** A toggle to switch the input socket between Integer (whole numbers) and Float (decimal numbers).
        
    - **Value (Socket - Input):** The numerical value to be converted.
        
    - **Decimals (Socket - Input):** (Float mode only) An integer that controls how many decimal places are included in the output string.
        
    - **String (Socket - Output):** The text representation of the input number.
        
- **Practical Application:** This node is a necessary component whenever you need to display a procedurally calculated number as text. Imagine you want to create a "damage counter" that appears over a creature's head, showing the total number of scales it has.
    
    1. **The Calculation:** You use a Domain Size node on your creature's mesh (with the Component set to 'Face') to get the total number of faces, which corresponds to the number of scales. This gives you an integer value.
        
    2. **The Goal:** You need to display this number as part of a text object that says "Scales: [number]".
        
    3. **The Problem:** The Join Strings or Format String nodes require string inputs, but your scale count is an integer.
        
    4. **The Solution:**
        
        - Use the Value to String node. Set its Data Type to 'Integer'.
            
        - Connect the Face Count output from the Domain Size node to the Value input.
            
        - The String output of this node is now the text version of your number (e.g., "1572").
            
    5. You can now feed this string into a Join Strings node along with the text "Scales: " to create your final, complete label, ready to be converted into curves. The Value to String node was the essential bridge between the numerical calculation and the text assembly.