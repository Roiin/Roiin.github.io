- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 1 - Trees
    
- **Core Function:** Forces a Logic Tree to execute a single update cycle ("tick"). This is distinct from Start Logic Tree, which makes the tree run continuously.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that must be true for the node to function.
        
    - **Input (Target Object):** The object on which the logic tree will be run for one cycle.
        
    - **Input (Node Tree):** A reference to the Logic Tree to be run.
        
    - **Output (Done):** A flow control pulse that activates after the single cycle is complete.
        
- **Practical Application:** Useful for turn-based games or situations requiring precise control, forcing an AI to re-evaluate its decisions at a specific moment rather than on its own internal clock.