- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Scene)
    
- **Core Function:** Provides the current scene time from the timeline, outputting it as either seconds or frames.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Seconds (Socket - Output):** The current time on the timeline, measured in seconds.
        
    - **Frames (Socket - Output):** The current frame number on the timeline. This can be a fractional value (e.g., 10.5) to support subframe accuracy for motion blur.
        
- **Practical Application:** This node is the foundation for any time-based animation within Geometry Nodes. For example, to create a continuously rotating windmill, you can take the Frames output and connect it to a Math node set to 'Multiply' to control the speed. The result can then be plugged into the Y-axis of a Combine XYZ node, which in turn drives the Rotation input of a Transform Geometry node. As the animation plays, the frame number increases, causing the windmill blades to rotate automatically.