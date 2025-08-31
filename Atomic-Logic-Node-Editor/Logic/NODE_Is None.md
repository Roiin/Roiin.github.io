- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 3
    
- **Core Function:** Checks if a given input has no value (is "None" or null). This is used to verify the success or failure of operations that may not return a result.
    
- **Key Properties & Settings:**
    
    - **Input (Value):** The data socket to be checked.
        
    - **Output (If None):** A boolean output that is true if the input value is None.
        
- **Practical Application:** Used for error-checking and validating results. "Did my raycast hit an object? Check the 'Hit Object' output with Is None. If the result is false (meaning it's not None), then I can proceed to interact with the object I hit."