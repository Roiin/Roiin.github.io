- **Editor:** Logic Node Editor
    
- **Node Group:** Values
    
- **Core Function:** Compares a Float input against a series of threshold Case values and outputs a corresponding Result value.
    
- **Key Properties & Settings:**
    
    - **Mode (Dropdown):** In your screenshot, this is set to Equal. It likely has other modes like Greater Than or Less Than.
        
    - **Float (Input Socket):** The float value to be tested.
        
    - **Result (Socket):** The data output corresponding to the first successful comparison.
        
    - **Default (Socket):** The value to output if no comparison is met.
        
    - **Case A, Case B, ... (Sockets):** The float threshold values for comparison. Each case has a corresponding output socket next to it for the result.
        
- **Practical Application:** Perfect for creating tiered results. For example, determining a player's rank based on their final score. If Score > 10000 (Case A), output the string "Rank S". If Score > 5000 (Case B), output "Rank A", and so on.