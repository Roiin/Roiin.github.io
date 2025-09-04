- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Write)
    
- **Core Function:** Programmatically sets the selection state of geometry elements. It takes a Boolean field as input and forces the selection in Edit Mode to match it. **Note: This node is context-specific and can only be used when creating custom tools with Geometry Nodes, not in standard object modifiers.**
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry whose selection state will be modified.
        
    - **Selection (Socket - Input):** A Boolean field. Elements where this field is True will become selected; elements where it is False will be deselected.
        
    - **Domain (Property):** The element type (Point, Edge, Face) on which the selection will be set.
        
    - **Geometry (Socket - Output):** The geometry with the updated selection state.
        
- **Practical Application:** This node allows you to create intelligent selection tools that would be tedious to use manually. Imagine building a custom tool called "Select Upward Faces" for an architectural model.
    
    1. The user has a complex model with many roofs, ledges, and floors. They run your tool.
        
    2. Inside the tool's node graph, you take the Normal of every face.
        
    3. You use a Vector Math node set to 'Dot Product' to compare each face's normal to a pure "up" vector (0, 0, 1). A result close to 1.0 means the face is pointing straight up.
        
    4. You use a Compare node to create a Boolean result: True for any face where the dot product is greater than, for example, 0.9.
        
    5. This Boolean result is plugged directly into the Selection input of the Set Selection node (with its domain set to 'Face').
        
    6. The final result for the user is that after running the tool, every perfectly flat, upward-facing surface on their entire model is instantly selected, making it incredibly easy to assign a single "snow" or "dust" material to all of them at once.