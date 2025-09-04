- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Extracts detailed parameters and properties (like focal length, clipping distances, and sensor size) from a specified camera object.
    
- **Key Properties & Settings:**
    
    - **Camera (Socket - Input):** The camera object from which to retrieve data. This is typically connected to an Active Camera node.
        
    - **Projection Matrix (Socket - Output):** Outputs a 4x4 matrix representing the camera's full projection transform.
        
    - **Focal Length (Socket - Output):** The camera's focal length in millimeters.
        
    - **Sensor (Socket - Output):** A 2D vector representing the camera sensor's width and height in millimeters.
        
    - **Shift (Socket - Output):** A 2D vector for the camera's horizontal and vertical shift.
        
    - **Clip Start (Socket - Output):** The distance to the camera's near clipping plane.
        
    - **Clip End (Socket - Output):** The distance to the camera's far clipping plane.
        
    - **Focus Distance (Socket - Output):** The distance from the camera to its point of focus, used for depth of field.
        
    - **Is Orthographic (Socket - Output):** A Boolean that is True if the camera is in orthographic mode.
        
    - **Orthographic Scale (Socket - Output):** The viewing scale used when the camera is in orthographic mode.
        
- **Practical Application:** To create a visual representation of a camera's view frustum in the 3D viewport. You can use the Focal Length and Sensor size to calculate the dimensions of the near and far clipping planes. Then, use the Clip Start and Clip End values to position these planes correctly in 3D space. By connecting these planes with edges, you can procedurally generate a 3D mesh that perfectly outlines what the camera can see. This is extremely useful for debugging camera-based effects or for planning shots in a complex scene.