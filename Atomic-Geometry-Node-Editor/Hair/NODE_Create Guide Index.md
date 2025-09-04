**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Guides)

**Core Function:** Generates a "guide index" map by selecting a subset of curves to act as guides and then assigning every other curve to its nearest guide.

**Key Properties & Settings:**

- **Geometry (Input):-** The full set of hair curves from which guides will be chosen.
    
- **Guide Mask (Input):** A boolean selection that determines which curves are allowed to be chosen as guides.
    
- **Guide Distance (Input):** Sets a minimum distance between chosen guides. This is the primary method for controlling how many guides are selected. A larger distance results in fewer, more spread-out guides.
    
- **Group ID (Input):** An integer field that can be used to partition the guide selection. The process will only run among curves that share the same Group ID.
    
- **Guide Index (Output):** The main output. An integer field where the value on each curve is the index of its nearest guide.
    
- **Guide Selection (Output):** A boolean field that is True for the curves that were chosen to be guides and False for all others.
    

**Practical Application:**  
This node is used to procedurally define the "clumps" for a Clump Hair Curves or Braid Hair Curves node when you don't already have a guide map from a duplication process. It allows you to create clumps from a uniform field of hair.

- **The Goal:** To take a uniform field of generated grass curves and group them into natural-looking, randomly distributed clumps.
    
- **The Problem:** You have a dense field of grass, but it's too uniform. You want to apply a Clump Hair Curves node, but you don't have a Guide Index map because the hairs weren't created with a Duplicate or Interpolate node. You need to create this map from scratch.
    
- **The Solution:** Use Create Guide Index Map to procedurally select "leader" blades of grass.
    
    1. Start with your dense field of grass curves.
        
    2. Use a Create Guide Index Map node.
        
    3. Set the Guide Distance. This value will determine the approximate size of your clumps. A larger distance will create fewer, larger clumps.
        
    4. To add variation, you can connect a Random Value (Boolean) node to the Guide Mask. This will mean that only a random subset of the grass blades are even eligible to become guides, leading to a more irregular clumping pattern.
        
    5. The Guide Index output can now be fed directly into a Clump Hair Curves node.
        

The result is that the node will intelligently select a sparse subset of your grass blades to act as clump centers, and every other blade will be assigned to its closest center. When you then apply the clumping, the uniform field will naturally pull together into distinct, randomly placed tufts.