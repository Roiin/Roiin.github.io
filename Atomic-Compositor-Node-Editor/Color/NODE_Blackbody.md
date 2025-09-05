- **Editor:** Compositor Node Editor
    
- **Node Group:** Color
    
- **Core Function:** Converts a temperature value (in Kelvin) into a physically accurate RGB color, simulating the color of light emitted by an incandescent "black body" radiator. It provides a natural and intuitive way to generate realistic light and fire colors.
    
- **Key Properties & Settings:**
    
    - **Temperature (Socket):** The input temperature in Kelvin. Lower values produce deep reds and oranges, mid-range values produce yellows and whites, and very high values produce light blues.
        
- **Practical Application:** This node replaces guesswork with physics, allowing you to create natural-looking light colors for effects like fire, explosions, and lightbulbs.
    
    - **Molecular (Realistic Fire Color):** Instead of trying to guess the right shade of orange for a fire effect, you can use physically plausible values.
        
        1. Connect a Blackbody node to an RGB input.
            
        2. A temperature of around **1500K** will give you a deep, reddish-orange, perfect for the core of a fire or embers.
            
        3. A temperature of around **1800K** gives a brighter, more intense orange-yellow.
            
        4. By using a Noise texture to drive the Temperature input within a small range (e.g., 1400K-1600K), you can create a fire texture that flickers with realistic variations in color temperature.
            
    - **Molecular (Accurate Lightbulb Tints):** To color a glare or a light source to match a real-world light.
        
        - A standard incandescent lightbulb is around **2700K - 3300K** (warm, yellowish white).
            
        - A standard studio light or "neutral" white is around **5000K**.
            
        - Daylight is often approximated at **6500K** (a very neutral, slightly cool white).
            
        - An overcast sky is even cooler, around **7500K**.
            
        - By using these values, you can tint your Glare nodes or Mix node overlays to accurately simulate different types of lighting in your scene.
            
    - **Organic (Procedural Explosions):** To create a dynamic explosion that cools over time:
        
        1. Use a Time Curve node to create a curve that starts very high and rapidly falls off (e.g., from Y=1 to Y=0.2).
            
        2. Feed this Factor into a Map Range node. Map the input range of 0-1 to a Temperature range of, for example, 6000K down to 1200K.
            
        3. Use the output of the Map Range node to drive the Temperature of a Blackbody node.
            
        4. The result is a color that starts as an intense, bright white-hot flash (6000K), then quickly shifts to yellow, orange, and finally a deep red as the explosion "cools," all animated procedurally. This color can then be used to drive the color of your explosion's smoke and fire simulation in the compositor.