**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Guides)

**Core Function:** Pulls hair curves towards designated "guide" curves, creating clumps or tufts. This is a fundamental technique for creating natural-looking fur and hair.

**Key Properties & Settings:**

- **Guide Index (Input):** An integer field that assigns each hair curve to a specific guide. All curves with the same Guide Index will be part of the same clump. This is often the output from a Duplicate Hair Curves or Interpolate Hair Curves node.
    
- - **Factor (Input):** A global multiplier for the strength of the clumping effect.
        
- **Shape (Input):** A falloff curve that controls the clumping strength along the length of each hair. The classic clumping shape is to have a value of 0.0 at the root (no clumping at the skin) and 1.0 at the tip, pulling the ends of the hairs together.
    
- - **Tip Spread (Input):** Adds a small amount of random noise to the tips after clumping, which can prevent the clump from collapsing into a single, sharp point and make it look more natural.
        
- **Preserve Length (Input):** Ensures that hairs do not get stretched as they are pulled towards their guide curve.
    

**Practical Application:**  
Clumping is essential for breaking up the uniform appearance of dense fur and is a key step in simulating wet or matted hair. Imagine creating the fur for a spider.

- **The Goal:** To make the spider's dense fur look less like a uniform carpet and more like a collection of small, natural tufts.
    
- **The Problem:** After using Duplicate Hair Curves to create a dense coat, all the hairs are perfectly parallel and evenly spaced. Real fur naturally groups together into small clumps.
    
- **The Solution:** Use the Guide Index map created by the duplication process to drive a Clump Hair Curves node.
    
    1. Place the Clump Hair Curves node directly after the Duplicate Hair Curves node.
        
    2. The Duplicate Hair Curves node automatically generates a Guide Index attribute. The Clump Hair Curves node will use this map by default. This tells each duplicated hair to clump towards the original guide hair it was spawned from.
        
    3. Use the Shape input with a Float Curve node to define the clumping profile. Start the curve at the bottom left (0,0) and raise it to the top right (1,1). This will keep the roots of the hair at the skin but pull the tips together into a point.
        
    4. Adjust the Factor to control how tightly the clumps are formed. A small factor creates soft, subtle clumping, while a large factor creates sharp, spiky tufts.
        

The result is a much more realistic and detailed coat of fur. The uniform field of hair is broken up into thousands of tiny, tapered clumps, which catches the light more interestingly and gives the fur a sense of texture and depth.