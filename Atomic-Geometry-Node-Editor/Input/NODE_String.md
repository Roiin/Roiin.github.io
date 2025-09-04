- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Constant)
    
- **Core Function:** Outputs a user-defined text string.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **String (Property):** A text field on the node used to enter the desired string value.
        
    - **String (Socket - Output):** The text string defined in the property.
        
- **Practical Application:** This node is crucial for organizing complex node trees and avoiding errors. For example, if you create a custom attribute called "growth_mask" with a Store Named Attribute node, you will later need to access it by that exact name. By using a single String node (containing "growth_mask") and plugging its output into both the storing and reading nodes, you guarantee the name is identical and prevent typos. This makes the setup more robust and easier to update, as the attribute name only needs to be changed in one central location.