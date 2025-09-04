**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Deforms hair curves using a 3D noise texture, which is ideal for creating natural-looking waves, curls, and clumps.

**Key Properties & Settings:**

- **Distance (Input):** Controls the amplitude or maximum magnitude of the noise displacement.
    
- **Scale (Input):** Controls the frequency of the noise pattern across the surface of the mesh. A low Scale creates large, gentle waves, while a high Scale creates smaller, tighter crimps.
    
- **Shape (Input):** A falloff that controls the noise strength along the length of each hair, from root to tip.
    
- **Cumulative Offset (Input):** When enabled, the noise offset is applied cumulatively along the curve. This causes the hair to follow a wandering, snake-like path, which is great for creating tangled or matted effects.
    
- **Preserve Length (Input):** Ensures the hair strands maintain their original length after being deformed by the noise.
    

**Practical Application:**  
This node is used to add medium-to-large scale variations to a hairstyle, moving beyond the fine detail of Frizz. It's perfect for breaking up the smooth, uniform look of combed fur. Imagine you are creating the mane for a lion.

- **The Goal:** To give the lion's mane a natural, slightly unkempt appearance with large, soft waves, rather than having it look like perfectly straight, combed hair.
    
- **The Problem:** After setting the basic hair length and combing direction, the mane looks too neat and uniform. The individual hairs are too parallel and lack the characteristic waviness that gives a real mane its volume and character. Frizz Hair Curves is too chaotic and small-scale for this effect.
    
- **The Solution:** Apply a Hair Curves Noise node to introduce a structured, wave-like pattern.
    
    1. Place the node in the chain after the initial combing and grooming has been done.
        
    2. Use a low Scale value. This is the most important step for creating large, gentle waves.
        
    3. Adjust the Distance to control the "waviness" of the mane. A smaller distance gives subtle waves, while a larger distance creates more pronounced curls.
        
    4. Use the Shape control to make the waves less intense near the scalp and stronger towards the ends of the hair, which is a more natural growth pattern.
        

The result is a mane that is no longer composed of straight, perfect strands. Instead, it has a natural, flowing wave running through it, which catches the light more realistically and gives the hairstyle a sense of volume and authenticity.