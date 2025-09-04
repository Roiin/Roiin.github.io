- **Editor:** Geometry Node Editor
    
- **Node Group:** Attribute
    
- **Core Function:** Analyzes a specific attribute across a geometry and outputs calculated statistics (like mean, median, min, max) about its values.
    
- **Key Properties & Settings:**
    
    - **Geometry (Socket):** The geometry containing the attribute to be analyzed.
        
    - **Selection (Socket):** A boolean field to filter which elements (vertices, faces, etc.) are included in the calculation.
        
    - **Attribute (Socket):** The specific attribute field (e.g., 'position', 'scale', a custom attribute) to be evaluated.
        
    - **Data Type (Property):** Sets the calculation mode for Float (single value) or Vector (three values, calculated element-wise).
        
    - **Domain (Property):** Defines the attribute domain to evaluate (e.g., Points, Edges, Faces, Splines).
        
    - **Mean (Socket):** Outputs the average value of the attribute.
        
    - **Median (Socket):** Outputs the median (middle) value.
        
    - **Sum (Socket):** Outputs the sum of all attribute values.
        
    - **Min (Socket):** Outputs the minimum value found in the attribute set.
        
    - **Max (Socket):** Outputs the maximum value found in the attribute set.
        
    - **Range (Socket):** Outputs the difference between the Max and Min values.
        
    - **Standard Deviation (Socket):** Outputs the statistical standard deviation.
        
    - **Variance (Socket):** Outputs the statistical variance.
        
- **Practical Application:** Determine the bounding box of a procedural asset by finding the Min and Max of its position attribute. This can be used to automatically scale it, place it on the ground, or generate a simplified collider. It could also be used to find the average height (Mean) of a terrain patch to dynamically place foliage or water planes.