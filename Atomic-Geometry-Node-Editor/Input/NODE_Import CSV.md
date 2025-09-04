- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Input (Import)
    
- **Core Function:** Reads a Comma-Separated Values (CSV) file and converts its tabular data into a point cloud, automatically creating attributes from the numeric columns.
    
- **Key Properties & Settings:**
    
    - **Path (Socket - Input):** A string input for the file path to the CSV file.
        
    - **Delimiter (Socket - Input):** A string input for the single character used to separate values in the file (e.g., a comma).
        
    - **(This node has no user-configurable properties in the sidebar.)**
        
    - **Point Cloud (Socket - Output):** The resulting point cloud geometry, where each point corresponds to a row from the CSV file.
        
- **Practical Application:** This is an excellent tool for data visualization. Imagine you have a CSV file containing survey data for tree locations in a park, with columns for 'X_Position', 'Y_Position', and 'Tree_Height'. Using the Import CSV node, you can load this file to generate a point cloud where each point represents a tree. The 'Tree_Height' column is automatically imported as an attribute, which you can then use to control the scale of tree models instanced onto these points, accurately recreating a virtual version of the park based on real-world data.