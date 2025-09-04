- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** For each top-level instance, this node outputs its final rotation as an XYZ Euler vector, with the angles measured in radians.
    
- **Key Properties & Settings:**
    
    - **(This node has no input sockets.)**
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Rotation (Socket - Output):** An XYZ Euler vector field representing the final rotation of each instance.
        
- **Practical Application:** This node is perfect for creating secondary effects that are aligned with your instances. Imagine you have a flock of bird instances, each with a unique, dynamic rotation to follow a flight path. You want to add a stylized "wind trail" curve behind each bird.
    
    1. First, you create your flock of bird instances.
        
    2. Use the Instance Rotation node to get the final rotation of each bird.
        
    3. Use the Instances to Points node to get the final position of each bird.
        
    4. Now, create a Curve Line. For its Start position, use the bird's position. For its End position, you need to calculate a point behind the bird.
        
    5. You can do this by taking a vector pointing backwards (e.g., [0, -5, 0]) and rotating it by the bird's rotation. Use a Vector Rotate node with the Rotation output from the Instance Rotation node to do this. Then add this rotated vector to the bird's position.
        
    6. The result is a new set of curve lines, each one trailing directly behind a bird and perfectly matching its orientation. This creates a dynamic motion trail that updates automatically with the birds' animation.