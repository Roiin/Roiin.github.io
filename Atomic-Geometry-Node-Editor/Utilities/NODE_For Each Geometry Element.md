**Editor:** Geometry Nodes Editor  
**Node Group:** Control (Zone)

**Core Function:** Executes a contained group of nodes repeatedly, once for each element (e.g., each face, point, or instance) of an input geometry, and then combines the results.

**Key Properties & Settings:**

- **Domain (Property):** The most critical setting. It determines what type of element the zone will iterate over (e.g., Points, Faces, Splines, Instances).
    
- **Geometry (Input):** The source geometry whose elements will be processed one by one.
    
- **Selection (Input):** A Boolean field that filters which elements from the domain are processed by the zone.
    
- **Index (Zone Data):** An output available inside the zone that provides the index of the current element being processed. This is vital for creating unique variations.
    
- **Element (Zone Data):** An output available inside the zone that provides the geometry of the current element itself (e.g., a single face as a small mesh). This is powerful but can be performance-intensive.
    
- **Geometry (Output):** The main output socket on the zone's end node. All the geometry generated in each iteration is joined together here.
    

**Practical Application:**  
This zone is designed for situations where you need to generate a unique and complex piece of geometry for every part of a base mesh. Standard instancing creates identical copies, but this zone allows for bespoke creation. A perfect example is populating a window frame with unique, procedurally generated spider webs on each of its faces.

- **The Goal:** To generate a distinct, randomized spider web on every individual face of a window frame mesh.
    
- **The Problem:** You can instance a single web model on each face, but this looks repetitive and unnatural. To achieve true variation, a separate geometry-generating process must be run for each face.
    
- **The Solution:** The For Each Element zone is the exact tool for this job.
    
    1. The window frame geometry is connected to the zone's Geometry input.
        
    2. The Domain is set to Faces.
        
    3. **Inside the zone**, for each iteration, you get the single face geometry from the Element output.
        
    4. You can then build a unique web on this face. For example: distribute a few random points on the Element face, use the face Index to seed a Random Value node, move the points around with this randomness, and then connect them with curves to create tangled strands.
        
    5. The final curve geometry for that single web is connected to the Geometry output on the zone's end node.
        

The zone automatically runs this entire "web-making" subroutine for every face of the window frame, and then stitches all the individually crafted webs together into one final object. The result is a far more organic and detailed model than could be achieved with simple instancing.