- **Editor:** Compositor Node Editor
    
- **Node Group:** Color (Adjust)
    
- **Core Function:** Compresses a High Dynamic Range (HDR) image into a standard Low Dynamic Range (LDR) format suitable for viewing on a monitor. Its primary goal is to preserve visual detail in both the extreme highlights and deep shadows that would otherwise be clipped (blown out to white or crushed to black). **Note: This is a legacy node, largely superseded by Blender's modern Color Management system (like Filmic or AGX).**
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** The HDR image input, typically a 32-bit float OpenEXR file.
        
    - **Tonemap Type (Property):** Selects the algorithm used for the conversion.
        
        - Rh Simple: A faster, more basic method suitable for general use.
            
        - R/D Photoreceptor: A more complex, physically-based model that offers finer control.
            
- **Rh Simple Settings:**
    
    - **Key (Socket):** The most important setting. It defines the value that the image's average brightness will be mapped to. Lowering it darkens the image; raising it brightens it.
        
- **R/D Photoreceptor Settings:**
    
    - **Intensity (Socket):** A general brightness control.
        
    - **Contrast (Socket):** Controls the local contrast of the resulting image.
        
    - **Light/Chromatic Adaptation (Sockets):** Advanced controls for how the algorithm adapts to brightness and color across the image.
        
- **Practical Application:** While modern workflows handle this automatically, the node still has specific uses, particularly for artistic effects or handling unmanaged footage.
    
    - **Important Context (Modern Workflow):** In a standard Blender workflow using Filmic or AGX color management, you should not need this node. The View Transform in the Color Management settings already performs a high-quality tone mapping operation on your linear render data for display. The correct professional workflow is to composite in linear space and let the View Transform handle the final conversion.
        
    - **Molecular (Legacy HDR to SDR Conversion):** This is the node's original intended use. If you have an HDR image (e.g., an EXR from another software or a panoramic HDRI) that you need to save as a standard LDR image (like a JPEG or PNG) with the tone mapping "baked in", this node is the tool for the job. You would feed your EXR into the Tone Map node (usually starting with Rh Simple and adjusting the Key) and then connect the output to a File Output node.
        
    - **Molecular (Creating a Stylized "HDR Look"):** The term "HDR" is often associated with a hyper-detailed, high-contrast artistic style. This node can be used (or misused) to create that effect. By using the R/D Photoreceptor mode and pushing the Contrast value, you can create an image with exaggerated local contrast, which can be a deliberate stylistic choice for certain types of motion graphics or stylized renders.
        
    - **Organic (Processing Log Footage):** Sometimes you may receive video footage shot in a "Log" format, which is a very low-contrast, washed-out looking image that contains a lot of dynamic range. If this footage isn't being handled correctly by your scene's color management, the Tone Map node can be a "quick and dirty" tool to expand its contrast and bring it into a more visually pleasing range before you begin your primary color grading, acting as a manual "de-log" step.