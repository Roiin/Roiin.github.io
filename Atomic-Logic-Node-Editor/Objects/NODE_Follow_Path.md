- **Editor:** Logic Node Editor
    
- **Node Group:** Objects > Transformation
    
- **Core Function:** Constrains an object's movement to a predefined Curve object in the scene, moving it along the path.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** A flow control input that triggers the movement along the path.
        
    - **Condition (Socket):** A boolean input; movement only proceeds when this is True.
        
    - **Moving Object (Socket):** The object that will be moved.
        
    - **Rotating Object (Socket):** An optional object that will be rotated to face the path's direction as it moves. Often the same as the Moving Object.
        
    - **Path Points (Socket):** Expects a reference to a Curve object that defines the path.
        
    - **Loop (Checkbox):** If checked, the object will return to the start of the path after reaching the end.
        
    - **Continue (Checkbox):** If checked, the object will remember its position on the path and resume from there when the node is re-triggered.
        
    - **Optional Navmesh (Socket):** An object input for a navigation mesh to be used in conjunction with the path.
        
    - **Move as Dynamic (Checkbox):** If checked, uses physics forces for movement.
        
    - **Lin Speed (Socket):** A float controlling the linear speed along the path.
        
    - **Reach Threshold (Socket):** A float defining the distance from the endpoint at which the path is considered "complete".
        
    - **Look At (Checkbox):** Enables the object to orient itself towards a target while following the path.
        
    - **Rot Speed (Socket):** A float controlling the rotational speed (how quickly it turns to follow the path's curves).
        
- **Practical Application:** Ideal for creating non-interactive, predictable movement like moving platforms, patrol routes for guards, or cinematic camera fly-throughs.