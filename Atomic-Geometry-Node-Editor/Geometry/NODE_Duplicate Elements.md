- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Creates a specified number of copies for each selected element, placing all duplicates at the exact same location as the original. It also outputs a crucial Duplicate Index attribute to distinguish between the copies.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry containing elements to be duplicated.
        
    - **Selection (Socket - Input):** A boolean mask. Only elements where this is True will be duplicated.
        
    - **Amount (Socket - Input):** An integer field defining how many duplicates to create for each selected element.
        
    - **Domain (Property):** The type of element to duplicate (Point, Edge, Face, Spline, or Instance).
        
    - **Geometry (Socket - Output):** The new geometry, containing both the original elements and all their duplicates.
        
    - **Duplicate Index (Socket - Output):** The most important output. This is an integer field where the original element is index 0, the first copy is index 1, the second is index 2, and so on. This allows you to treat each copy differently.
        
- **Practical Application:** This node is perfect for creating procedural arrays, like a staircase.
    
    1. Start with a single cube mesh, scaled to the shape of one stair step.
        
    2. Use the Duplicate Elements node on this step. Set the Domain to 'Face' (or convert the step to an instance and use 'Instance'). Set the Amount to the desired number of steps, for example, 15. At this point, you have 15 steps all stacked in the same location.
        
    3. Connect a Set Position node after the Duplicate Elements node to move the copies.
        
    4. To create the staircase effect, you need to offset each duplicate based on its Duplicate Index. For the Offset input, multiply the Duplicate Index by a vector representing the rise and run of a single step (e.g., Y: 0.3, Z: 0.2).
        
    5. You can do this by feeding the Duplicate Index into a Vector Math node set to 'Scale'. The second vector in the scale node would be (0, 0.3, 0.2).
        
    6. The result is that the first step (index 0) is not moved. The second step (index 1) is moved up and forward by one step's worth. The third step (index 2) is moved by twice that amount, and so on, perfectly generating the entire staircase from a single step.