**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Curls up the end of each hair curve into a tight roll, similar to a rolled-up scroll or a tendril.

**Key Properties & Settings:**

- **Factor (Input):** A global control for the strength of the rolling effect. At 0.0, the hairs are straight; at 1.0, they are fully rolled.
    
- **Roll Length (Input):** The length of the curve, measured from the tip, that will be used to form the roll.
    
- **Roll Radius (Input):** Controls the tightness of the resulting curl. A smaller radius creates a tighter roll.
    
- **Roll Taper (Input):a** A curve falloff that can modify the radius of the roll along its length, creating a more conical spiral shape.
    
- **Roll Direction (Input):** A vector that defines the axis around which the hair will be rolled.
    
- **Random Orientation (Input):** Adds a random variation to the Roll Direction for each hair, preventing all the rolls from looking identical.
    

**Practical Application:**  
This node is designed for very specific, stylized hair effects rather than general fur grooming. It is perfect for creating the coiled tendrils on a vine or the stylized, rolled-up hair of certain character designs. A great example would be creating the snaking, tendril-like hair of a gorgon.

- **The Goal:** To model a head of "hair" for a character that is composed of many small, snake-like tendrils, each of which is curled up at the tip.
    
- **The Problem:** Manually modeling and posing dozens or hundreds of tiny, curled tendrils is incredibly time-consuming. You need a procedural method that can apply this specific curling effect to a set of guide curves.
    
- The Solution: The Roll Hair Curves node can create this effect instantly.
    
    1. Start by generating a set of base hair curves on the character's head to define the length and general flow of the tendrils.
        
    2. Add a Roll Hair Curves node.
        
    3. Set the Roll Length to a significant portion of the hair's total length to create a prominent curl.
        
    4. Adjust the Roll Radius to get the desired thickness of the tendrils.
        
    5. Use the Random Orientation input, driven by a Random Value node, to ensure that each "snake" curls in a slightly different direction, which will look much more organic and chaotic.
        
    6. The Factor can be animated from 0 to 1 to create a dynamic effect of the tendrils curling and uncurling.
        

The result is a highly stylized and complex hairstyle that would be impractical to create by hand, achieved with a single, specialized node.