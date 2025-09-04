- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Point
    
- **Core Function:** Connects points from a point cloud to form one or more curve splines. It provides controls to group points into separate curves and to sort them, defining the order in which they are connected.
    
- **Key Properties & Settings:**
    
    - **Points (Socket - Input):** The source point cloud geometry.
        
    - **Curve Group ID (Socket - Input):** An integer field. All points sharing the same Group ID value will be connected together to form a single, distinct curve spline.
        
    - **Weight (Socket - Input):** A float field used to sort the points within each group. Points with a lower weight will come earlier in the curve, and points with a higher weight will come later.
        
    - **Curves (Socket - Output):** The resulting curve geometry.
        
- **Practical Application:** This node is perfect for generating connecting geometry, like the spiral threads of a spider web.
    
    1. **The Setup:** You have already created the radial support strands of your web. Now, you use Curve to Points on these strands to generate a series of concentric rings of points. Each ring of points has its own unique index.
        
    2. **The Goal:** You need to connect the points of each ring to form the continuous spiral threads.
        
    3. **The Problem:** Right now, your points are just an unorganized cloud. A simple Points to Curves will connect them in a meaningless order.
        
    4. **The Solution:**
        
        - Use the Points to Curves node.
            
        - **Grouping:** The Curve Group ID is the key. You need to assign an ID to each point that corresponds to which concentric ring it belongs to. You can capture this ring index from your earlier steps. Now, all points from ring #1 will form one curve, all points from ring #2 will form a second, and so on.
            
        - **Sorting:** Within each ring, you need to connect the points in the correct circular order. You can use the Weight input for this. A good sorting weight would be the angle of each point relative to the web's center. You can calculate this with the atan2() function on the points' X and Y positions.
            
    5. **The Result:** The node will first group the points by their ring ID, and then, within each ring, it will connect them in order of their angle. This creates a perfect set of continuous, spiral curves that form the main structure of the spider web.