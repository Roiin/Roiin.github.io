- **Editor:** Logic Node Editor
    
- **Node Group:** Logic Part 1 - Trees
    
- **Core Function:** Dynamically attaches a Logic Tree resource to an object at runtime. The tree is added but not automatically started.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (Target Object):** The object that will receive the new Logic Tree.
        
    - **Input (Node Tree):** The Logic Tree to be added.
        
    - **Setting (Initialize):** If checked, the tree's internal "On Init" event will run upon being added.
        
    - **Output (Done):** A flow control pulse that activates after the tree is added.
        
- **Practical Application:** Granting a new behavior to an object mid-game, such as adding a "Burning" logic tree to a character hit by a fire spell, or giving an enemy a "Fleeing" behavior when their health is low.