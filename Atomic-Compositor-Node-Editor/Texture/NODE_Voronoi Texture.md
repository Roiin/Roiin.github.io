- **Editor:** Compositor Node Editor  
- **Node Group:** Texture
    
- **Core Function:** Generates a variety of cellular and geometric patterns based on Worley noise. It excels at creating organic-looking cells, cracked surfaces, crystal formations, and geometric mosaics.
    
- **Key Properties & Settings:**
    
    - **Vector (Socket):** The input texture coordinates.
        
    - **4D (Mode) / W (Socket):** In 4D mode, the W socket allows you to animate the pattern, making the cells shift and evolve over time.
        
    - **Feature (Property):** The most important setting, as it completely changes the node's output. Key features include:
        
        - F1: The standard Voronoi pattern. Color output gives flat-colored cells. Distance gives a gradient from the center of each cell outwards.
            
        - Distance to Edge: Outputs a grayscale map that is white at the cell borders and black in the center. This is the most useful feature for creating crack and vein patterns.
            
        - Smooth F1: A version of F1 with built-in smoothing, creating rounded cells with a soft falloff.
            
    - **Distance Metric (Property):** Changes the mathematical calculation for distance, which alters the shape of the cells. Euclidean is the standard circular/organic look. Manhattan and Chebychev create squarish, more geometric cells. Minkowski is a versatile in-between.
        
    - **Scale (Socket):** Controls the overall size and density of the cells.
        
    - **Randomness (Socket):** Controls the placement of the cell points. A value of 1.0 is a chaotic, organic pattern. A value of 0.0 arranges the points in a perfect, rigid grid.
        
- **Outputs (Dynamic):**
    
    - **Distance (Socket):** A grayscale output, its meaning depends on the selected Feature.
        
    - **Color (Socket):** A color output, typically providing a random solid color for each cell.
        
    - **Position (Socket):** A vector output that gives the coordinate of the center point of each cell.
        
- **Practical Application:** The Voronoi node is the "atom" of cellular division and cracking. It's the starting point for anything that looks like stylized crystals, dried mud, scales, or biological cells.
    
    - **Molecular (Cracked Earth / Veins / Lightning):** This is a classic and powerful use.
        
        1. Set the Feature to Distance to Edge. The Distance output is now a network of white lines on a black background.
            
        2. Feed this Distance output into a Color Ramp. By sliding the black and white stops very close together, you can create a high-contrast map with very thin, sharp crack lines.
            
        3. This crack map can be used as a displacement map to create 3D cracks, or as a mask to mix in a different color or emissive glow for veins or lightning effects.
            
    - **Molecular (Stained Glass / Geometric Mosaic):**
        
        1. Set the Feature to F1. The Color output gives you a pattern of random, flat-colored cells.
            
        2. To create the "leading" between the glass panes, use the Distance to Edge output (from a second Voronoi node or by using F2-F1 math) to create a black line pattern, and then Add it on top of the Color output.
            
    - **Organic (Water Caustics):** The animated Voronoi is perfect for faking water caustics.
        
        1. Set the Feature to Smooth F1. Use the Distance output.
            
        2. Set the Dimensions to 4D. Animate the W value to make the cells gently shift and change over time.
            
        3. The result is a soft, evolving, cell-like pattern that, when projected onto a surface, strongly resembles the bright patterns of light at the bottom of a swimming pool.
            
    - **Organic (Procedural Crystals):**
        
        1. Set the Distance Metric to Chebychev or Manhattan and Randomness to a low value to get angular, geometric cell shapes.
            
        2. Use the Color output to get flat-colored crystal shapes.
            
        3. Use the Position output to feed into another Noise Texture. This will give each crystal cell its own unique internal texture, adding a layer of realism. Combine these results for a complex, procedural crystal material.