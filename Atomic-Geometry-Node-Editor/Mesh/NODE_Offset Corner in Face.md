- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Mesh (Topology)
    
- **Core Function:** For any given face corner, this node finds the index of another corner within the same face by "walking" a specified number of steps around the face's vertex loop.
    
- **Key Properties & Settings:**
    
    - **Corner Index (Socket - Input):** The index of the starting corner for the "walk".
        
    - **Offset (Socket - Input):** An integer defining how many steps to take around the face loop. A value of 1 finds the very next corner, 2 finds the one after that, and so on. Negative values walk in the opposite direction.
        
    - **Corner Index (Socket - Output):** The index of the corner that was found after the offset was applied.
        
- **Practical Application:** This node is a key component for procedurally generating geometry based on face topology, like creating a beveled frame inside every quad face of an animal's cage.
    
    1. Start with a cage made of many quad faces.
        
    2. **The Goal:** For each quad, you want to create four new vertices, each one inset slightly from the original corners, and then connect them to form a smaller, inner frame.
        
    3. For each corner of a face, you need to know the position of the two adjacent corners to calculate the inset position.
        
    4. You can iterate through every corner of the mesh. For a corner with index i:
        
        - Use the Offset Corner in Face node with Offset = 1. The output is the index of the next corner (i+1).
            
        - Use another Offset Corner in Face node with Offset = -1. The output is the index of the previous corner (i-1).
            
    5. Now that you have the indices of the two neighboring corners, you can use Sample Index to get their Position.
        
    6. You can then calculate a new position for your frame's vertex by taking the original corner's position and moving it slightly towards the two neighbors.
        
    7. After calculating these four new inset points for each face, you can create new geometry from them. The Offset Corner in Face node was the essential tool that allowed you to "walk" around each face and gather the necessary neighborhood information.