- **Editor:** Compositor Node Editor  
- **Node Group:** Mask
    
- **Core Function:** **[DEPRECATED]** The original implementation of the Cryptomatte system in Blender. It generates accurate, anti-aliased mattes for objects or materials by requiring a direct connection to the specific Cryptomatte render pass data channels.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The standard color input (beauty pass).
        
    - **Crypto<XX> Sockets:** A series of dedicated input sockets (Crypto00, Crypto01, etc.). These **must be manually connected** to the corresponding CryptoObject00, CryptoObject01, etc., render passes from the Render Layers node. This is the primary difference from the modern node.
        
    - **Add/Remove (Buttons):** The eyedropper interface for picking objects/materials from the Pick output in a Viewer.
        
    - **Matte ID (Property):** A text field listing the selected IDs.
        
- **Outputs:**
    
    - **Image (Socket):** The input Image with the generated matte applied as an alpha channel.
        
    - **Matte (Socket):** The raw, high-quality, black-and-white grayscale matte.
        
    - **Pick (Socket):** A colored visualization of the Cryptomatte data, used for picking IDs.
        
- **Practical Application:** This node has been entirely superseded by the modern Cryptomatte node. Its documentation is primarily for understanding and updating older .blend files.
    
    - **IMPORTANT NOTE:** The modern Cryptomatte node is superior in every way. It automatically finds the necessary render pass data without requiring manual connections, making it significantly easier and cleaner to use. If you encounter this legacy node in a file, the recommended action is to **delete it and replace it with the modern Cryptomatte node**.
        
    - **Legacy Workflow (for reference):** The "molecule" for using this node was more cumbersome:
        
        1. In View Layer Properties, enable the Cryptomatte Object pass. This would expose multiple outputs on the Render Layers node (e.g., CryptoObject00, CryptoObject01, CryptoObject02).
            
        2. Add a Cryptomatte (Legacy) node.
            
        3. Manually connect the Image output to the Image input.
            
        4. Manually connect CryptoObject00 to Crypto00, CryptoObject01 to Crypto01, and so on for all available passes.
            
        5. Connect the Pick output to a Viewer node.
            
        6. Use the Add/Remove eyedroppers to select objects.
            
        7. Use the Matte output for compositing.
            
    - This manual connection process was prone to error and cluttered the node graph, which is precisely the problem the modern node was designed to solve.