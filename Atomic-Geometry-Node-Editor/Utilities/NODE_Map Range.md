**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (Math)

**Core Function:** Remaps a numerical value from an input range to a new output range, with options for different interpolation styles.

**Key Properties & Settings:**

- **Value (Input):** The float or vector to be remapped.
    
- **From Min / From Max (Inputs):** Defines the source range. For example, if you are remapping a texture that outputs values from 0.0 to 1.0, these would be your From values.
    
- **To Min / To Max (Inputs):** Defines the target range. You can invert the range (e.g., mapping 0-1 to 1-0) to reverse an effect.
    
- **Interpolation Type (Property):** Controls the transition, with options like Linear, Smooth Step, and Smoother Step for easing effects.
    
- **Clamp (Checkbox):** When enabled, this ensures the output value will never go outside the To Min and To Max range, even if the input value is outside the From range.
    

**Practical Application:**  
This node is essential for converting one type of data into another, such as turning proximity distance into a scale factor. Imagine you want to create a field of grass that gets procedurally flattened around an animal, like a rhinoceros, as it walks through.

- **The Goal:** To make blades of grass scale down based on their closeness to a rhino, creating a parting effect.
    
- **The Problem:** The Geometry Proximity node can tell you the distance of each blade of grass from the rhino. This might be a raw value from 0.0 to 10.0 or more. This raw distance is not suitable for a Scale input, which typically needs a controlled value around 1.0.
    
- **The Solution:** The Map Range node is the perfect tool to translate distance into scale.
    
    1. Use a Geometry Proximity node, with the rhino as the Target, to get the Distance for each point where grass is instanced.
        
    2. Feed this Distance output into the Value input of the Map Range node.
        
    3. Set the From Min to 0.0 (the grass is touching the rhino).
        
    4. Set the From Max to a value like 2.0 (this is your "influence radius" of 2 meters).
        
    5. Set the To Min to a small number like 0.1 (the scale of fully flattened grass).
        
    6. Set the To Max to 1.0 (the normal, full scale of the grass).
        
    7. Crucially, enable the Clamp option. This ensures that any grass blade further than 2 meters away will have its scale clamped at 1.0, and not get any larger.
        
    8. Connect the Result of the Map Range node to the Scale input of your Instance on Points node.
        

Now, any grass within a 2-meter radius of the rhino will scale down smoothly, creating a convincing and interactive "parting the grass" effect.