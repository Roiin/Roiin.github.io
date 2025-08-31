- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Mouse
    
- **Core Function:** Triggers a coordination flow when mouse movement is detected.
    
- **Key Properties & Settings:**

	- **Movement (Socket):** Vector output providing the X and Y coordinates of the mouse.
	       
    - **Screen X (Socket):** A float input (0.0 to 1.0) for the horizontal position.
        
    - **Screen Y (Socket):** A float input (0.0 to 1.0) for the vertical position.
           
    - **Mode (Dropdown):** Determines the type of position data to output (Position, Movement, Wheel).
        
    - **Invert Y (Checkbox):** Inverts the Y-axis of the output position.
    
- **Practical Application:** If it is, the Position vector from the Mouse Moved node is used to continuously update the screen position of the inventory item's icon, creating the "drag" effect.