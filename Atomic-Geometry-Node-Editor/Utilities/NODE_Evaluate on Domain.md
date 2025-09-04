**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Field)

**Core Function:** Evaluates a field on a specified domain and interpolates the result to the current domain context, allowing data from one domain (e.g., Faces) to be used by another (e.g., Points).

**Key Properties & Settings:**

- **Domain (Property):** The attribute domain on which the input Value will be evaluated (e.g., Point, Edge, Face, Spline).
    
- **Value (Input):** The field to be evaluated on the chosen domain.
    
- **Value (Output):** The data from the input field, now evaluated on the specified domain and made available in the current context.
    

**Practical Application:**  
This node is key for creating effects where the properties of vertices are determined by the faces they belong to. Imagine you want to give an animal model, like a rhino, a stylized, low-poly, faceted appearance by moving all of its vertices to the center of their respective faces.

- **The Goal:** To transform a smooth rhino mesh into one with a distinct, faceted look, where each face is perfectly flat.
    
- **The Problem:** To achieve this, every vertex needs to know the center position of the face it is a part of. However, a vertex's Position exists on the Point domain, while the face's center is a concept that belongs to the Face domain. You need a way to bridge this gap.
    
- **The Solution:** The Evaluate on Domain node can retrieve the face-level data for each point.
    
    1. Start with your rhino mesh.
        
    2. Use a Set Position node, which operates on the Point domain.
        
    3. To determine the new position for each vertex, use an Evaluate on Domain node.
        
        - Set its Domain property to Face.
            
        - Connect the standard Position field into the Value input. When evaluated on the Face domain, the Position field automatically returns the average position of the face's vertices—its center.
            
    4. Connect the Value output from the Evaluate on Domain node directly into the Position input of the Set Position node.
        

This setup instructs every vertex to find the center of the face it belongs to and move to that exact location. All vertices of a single face will collapse to the same point, resulting in perfectly flat planes and giving the rhino model a hard-surface, stylized appearance.