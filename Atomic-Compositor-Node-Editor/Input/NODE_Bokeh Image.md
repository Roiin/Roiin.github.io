- **Editor:** Compositor Node Editor
    
- **Node Group:** Input
    
- **Core Function:** Procedurally generates a custom shape that defines the aesthetic quality of out-of-focus highlights (bokeh). It is a specialized input designed to be plugged directly into the Bokeh Blur node.
    
- **Key Properties & Settings:**
    
    - **Flaps (Property):** Sets the integer number of "blades" for the virtual camera's iris diaphragm. A value of 6 creates a common hexagonal bokeh.
        
    - **Angle (Property):** Rotates the generated iris shape, which can be useful to avoid unnaturally aligned patterns in the blur.
        
    - **Roundness (Property):** Defines the curvature of the blades. A value of 0 creates sharp-cornered polygons (e.g., a perfect hexagon), while a value of 1 creates a perfect circle, regardless of flap count.
        
    - **Catadioptric Size (Property):** Simulates the "doughnut" shaped bokeh produced by catadioptric (mirror) lenses, creating a bright ring with a dark center.
        
    - **Color Shift (Property):** Introduces a slight chromatic aberration or color fringing to the bokeh shape, mimicking lens imperfections for added realism.
        
    - **Image (Socket):** Outputs the generated bokeh shape image.
        
- **Practical Application:** This node's sole purpose is to craft the artistic "flavor" of your depth of field effect. It turns a generic blur into a specific photographic style.
    
    - **Molecular (Cinematic Aperture Simulation):** The default blur is a simple circle. To emulate high-end cinema lenses, you might set Flaps to 8 or 9 and increase Roundness to about 0.8. This creates a soft, nearly circular bokeh that feels more organic and professional than a perfect digital circle.
        
    - **Molecular (Anamorphic Lens Emulation):** A hallmark of anamorphic lenses is vertically stretched, oval-shaped bokeh. This node cannot create an oval directly, but you can create the "molecule" for it.
        
        1. Start with a Bokeh Image node (e.g., 6 flaps, 0.7 roundness).
            
        2. Pipe its Image output into a Transform node.
            
        3. In the Transform node, uncheck "Uniform" and set the Y Scale to 0.5.
            
        4. Feed the result of the Transform node into the Bokeh input of your Bokeh Blur node. You have now successfully faked an anamorphic bokeh look.
            
    - **Molecular (Emulating Mirror Lenses):** To achieve the unique "doughnut bokeh" characteristic of mirror telephoto lenses (often used in vintage nature documentaries or spy films for their distinct look), simply increase the Catadioptric Size property. This is a very specific stylistic choice that can immediately evoke a certain mood or era.
        
    - **Organic (Custom Sci-Fi & Fantasy Highlights):** You can use this node for more than just realism. Set Flaps to 3 and Roundness to 0 to create sharp, triangular highlights. Or set Flaps to 5 for star-shaped highlights. This can be used to give magical effects or sci-fi environments a unique, stylized visual signature in their out-of-focus areas.