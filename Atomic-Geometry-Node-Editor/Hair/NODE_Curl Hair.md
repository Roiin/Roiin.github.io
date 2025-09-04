**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Guides)

**Core Function:** Deforms hair curves into a spiral or helical "curl" shape, wrapping them around designated guide curves.

**Key Properties & Settings:**

- **Guide Index (Input):** An integer field that assigns each hair to a specific curl group. All hairs with the same Guide Index will be wrapped into the same curl.
    
- **Factor (Input):** A global multiplier for the strength of the curling effect.
    
- **Radius (Input):** Controls the overall radius of the helical curl.
    
- **Frequency (Input):** Controls the tightness of the curl. A higher frequency creates more twists over the same length.
    
- **Curl Start (Input):** A value from 0 to 1 that defines how far down the strand the curling effect begins, allowing you to have a straight root and a curly tip.
    
- **Random Offset (Input):** Adds a random phase shift to the curl for each hair, preventing all the curls from looking perfectly synchronized and identical.
    

**Practical Application:**  
This node is designed for creating pronounced, structured curls, as opposed to the more chaotic waves from a Hair Curves Noise node. It's ideal for creating stylized curly hairstyles.

- **The Goal:** To create a head of hair composed of well-defined, corkscrew curls for a character.
    
- **The Problem:** While noise can create waves, it's difficult to get a consistent, repeating helical shape. You need a specialized deformer that can wrap strands into a tight, regular spiral.
    
- **The Solution:** Use the Curl Hair Curves node after defining a set of guides.
    
    1. First, generate a sparse set of guide hairs on the character's head. These guides will define the overall flow and length of the final curls.
        
    2. Use a Duplicate Hair Curves node to generate the required density. This will also conveniently create the Guide Index map you need, ensuring the duplicated hairs are grouped around their parent guides.
        
    3. Add the Curl Hair Curves node. It will automatically use the Guide Index map.
        
    4. Adjust the Radius to control how "wide" the corkscrews are.
        
    5. Adjust the Frequency to control how "tight" the corkscrews are.
        
    6. Use a Random Value node connected to the Random Offset input. This is a crucial step for realism, as it will make each curl start at a slightly different point in its rotation, breaking up the artificial uniformity.
        

The result is a full head of hair where each clump of strands is twisted into a distinct, helical curl. This provides a high level of artistic control for creating a wide variety of curly hairstyles, from loose ringlets to tight coils.