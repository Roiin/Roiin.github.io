- **Editor:** Geometry Node Editor
    
- **Node Group:** Attribute
    
- **Core Function:** Evaluates and "freezes" an attribute on a geometry at a specific point in the node tree, making that data available for use by subsequent nodes via a dedicated output socket.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The geometry on which the attribute will be captured.
        
    - **Value (Socket - Input):** The field to be evaluated and stored (e.g., position, normal, a procedural noise texture).
        
    - **Domain (Property):** The attribute domain (e.g., Point, Edge, Face, Instance) where the captured data will be stored.
        
    - **Data Type (Property):** The type of data being captured (e.g., Float, Vector, Boolean).
        
    - **Geometry (Socket - Output):** The output geometry, now carrying the captured attribute data as a temporary, anonymous attribute. **Crucially, this specific geometry output must be used for any downstream nodes that need to access the captured data.**
        
    - **Attribute (Socket - Output):** The output socket that provides the captured data itself, ready to be plugged into other nodes.
        
- **Practical Application:** This node is fundamental for transferring attribute data between different states or contexts of a geometry. **Example:** Imagine instancing rocks onto a procedural landscape. You want the rocks to inherit the color of the landscape at their specific location. You would use Capture Attribute on the landscape mesh to store its color attribute before the Instance on Points node. Then, you feed that captured Attribute (color) into the material of the instanced rocks, ensuring each rock is correctly colored based on the ground beneath it. Without this node, the instancing context would not have access to the original landscape's color data.