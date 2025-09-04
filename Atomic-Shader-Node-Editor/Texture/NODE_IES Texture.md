**Editor:** Shader Editor (Light Context)  
**Engine(s) Supported:** [Cycles & Eevee]  
**Node Group:** Texture

**Core Function:** Replicates the real-world light distribution pattern of a specific light fixture by using an industry-standard IES data file.

**Key Properties & Settings:**

- **Factor (Output):** The primary output. It provides a grayscale intensity value that precisely matches the light distribution pattern from the IES file. This must be connected to the Strength input of an Emission shader in a light's node tree.
    
- **Mode (Property):** Determines how the IES file is loaded. External (most common) loads a file from your hard drive. Internal uses an IES profile saved within the blend-file's text blocks.
    
- **Strength (Input):** A simple multiplier that can be used to increase or decrease the overall brightness of the IES profile without altering its pattern.
    
- **Vector (Input):** Defines the coordinate system for projecting the light pattern. It defaults to the light's normal direction, which is correct for most use cases.
    

**Practical Application:**  
This node is an indispensable tool for architectural visualization, where lighting realism is paramount. A standard Blender Point or Spot light emits a perfectly uniform, mathematically simple pattern (a perfect sphere or cone), which looks artificial. Real-world light fixtures (like a recessed downlight or a designer lamp) cast complex, specific patterns of light and shadow.

The problem is how to accurately simulate these unique, real-world light patterns. The IES Texture node is the solution.

1. First, you would download the specific .ies file for a real light fixture from the manufacturer's website (e.g., Philips, Osram).
    
2. In Blender, select a Point Light, go to its Object Data Properties, and enable Use Nodes. This will give you an Emission shader in the Shader Editor.
    
3. Add an IES Texture node. Leave its mode set to External and open the .ies file you downloaded.
    
4. Connect the Factor output of the IES Texture node to the Strength input of the Emission shader.
    
5. The result is a dramatic increase in realism. Your generic Point Light will now cast the exact, intricate, and physically accurate light pattern of the real-world fixture it represents. This adds a level of authenticity to an architectural render that is impossible to achieve with standard lights, correctly simulating how a specific product will actually illuminate a space.