- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Geometry (Operations)
    
- **Core Function:** Removes elements from a geometry based on a Boolean selection. It can be configured to delete individual points, edges, faces, splines, or entire instances.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket - Input):** The source geometry from which elements will be removed.
        
    - **Selection (Socket - Input):** A Boolean field that acts as a "delete mask". Any element where this field evaluates to True will be deleted.
        
    - **Domain (Property):** Determines the type of element to target for deletion:
        
        - **Point:** Deletes individual vertices.
            
        - **Edge:** Deletes edges (can leave floating vertices).
            
        - **Face:** Deletes faces.
            
        - **Spline:** Deletes entire curves within a curve object.
            
        - **Instance:** Deletes entire instances.
            
    - **Mode (Property):** Provides finer control when the Domain is set to 'Face':
        
        - **All:** Deletes the faces and any vertices/edges that are no longer part of another face (creates clean holes).
            
        - **Only Faces:** Deletes only the faces, leaving their boundary edges and vertices behind.
            
- **Practical Application:** This node is perfect for architectural modeling, such as creating window cutouts in a building's façade.
    
    1. Start with a Grid primitive that has been subdivided to represent the wall with many potential window locations.
        
    2. To select which faces to delete, you can create a procedural pattern. For example, use the Index of the faces and a Math node set to 'Modulo'. You can use this to select every 4th face in a row, creating a regular grid of True values.
        
    3. Feed this Boolean pattern into the Selection input of the Delete Geometry node.
        
    4. Set the Domain to 'Face' and the Mode to 'All'.
        
    5. The result is that all the selected faces are cleanly removed from the wall, creating a perfect grid of openings ready for you to procedurally insert window frames. This technique allows you to quickly generate complex building facades that are easy to modify just by changing the math in your selection pattern.