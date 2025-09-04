- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Instances
    
- **Core Function:** Applies a scaling transformation to existing instances. This node multiplies the existing scale of each instance by the provided Scale value.
    
- **Key Properties & Settings:**
    
    - **Instances (Socket - Input):** The geometry containing the instances to be scaled.
        
    - **Selection (Socket - Input):** A Boolean mask. Only selected instances will be scaled.
        
    - **Scale (Socket - Input):** A vector that provides the scaling factor to be applied.
        
    - **Center (Socket - Input):** The point from which the instances will scale away. **To scale instances in place without moving them, this input should be connected to their own position.**
        
    - **Local Space (Socket - Input):** A Boolean. If True, the scaling is applied along the instance's own local axes. If False, it's applied along the world axes.
        
    - **Instances (Socket - Output):** The geometry with its instances scaled.
        
- **Practical Application:** This node is perfect for creating proximity-based growth animations. Imagine you have a field of flowers already instanced on a surface, and you want them to magically bloom and grow as a character (represented by an Empty) walks past them.
    
    1. First, you create your field of instanced flowers.
        
    2. Use an Object Info node to get the Location of your character's Empty.
        
    3. Calculate the Distance from the Empty to the position of each flower instance.
        
    4. Use a Map Range node to create a growth falloff. Map the Distance (e.g., from 0m to 5m) to an inverted Scale factor (from 1.0 down to 0.0). This means flowers within 5 meters will have some scale, and flowers right next to the Empty will have a full scale of 1.
        
    5. Use the Scale Instances node. Feed this calculated scale factor into its Scale input.
        
    6. **Crucially:** To prevent the flowers from flying away from the Empty as they scale, connect their own position into the Center input.
        
    7. The result is a beautiful, interactive animation. As you move the Empty through the field, a ripple of growth emanates from it, with flowers scaling up from zero to their full size as the character approaches and then shrinking back down as the character moves away.