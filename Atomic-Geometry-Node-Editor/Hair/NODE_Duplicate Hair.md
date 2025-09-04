**Editor: Geometry Nodes Editor**  
**Node Group:** Hair Nodes (Generation)

**Core Function:** Generates multiple copies of each input hair curve within a specified radius, used to increase the density of a hairstyle.

**Key Properties & Settings:**

- **Amount (Input):** The number of duplicates to generate for each original "guide" curve.
    
- **Radius (Input):** The maximum distance from the original curve within which the duplicates will be created.
    
- **Seed (Input):** An integer used to randomize the placement of the duplicated curves.
    
- **Even Thickness (Input):** When enabled, this option adjusts the distribution of duplicates to create a more uniform density, which can prevent clumping.
    
- **Guide Index (Output):** An integer field that stores the index of the original guide curve from which each new curve was generated. This is useful for later clumping effects.
    

**Practical Application:**  
This node is part of a standard workflow for creating dense fur or hair. Instead of generating millions of individual hairs from the start (which is slow), you generate a smaller number of "guide" hairs and then use this node to fill in the density. This is how you would create the thick, dense undercoat of fur on an animal like a spider.

- **The Goal:** To create a dense, fuzzy coat of fur on a spider model, composed of thousands of hairs.
    
- **The Problem:** Generating and simulating thousands of individual hairs directly on the spider's surface can be very computationally expensive and slow.
    
- **The Solution:** Use a two-step process. First, generate a sparse set of guide hairs, then use Duplicate Hair Curves to create the final density.
    
    1. Use a Distribute Points on Faces node on the spider's mesh to create a few hundred points. Generate a short hair curve at each of these points. These are your "guide hairs".
        
    2. Groom these sparse guide hairs using nodes like Frizz or Noise to give them their basic character.
        
    3. Add a Duplicate Hair Curves node after the grooming.
        
    4. Set the Amount to a value like 20. This means each of your original guide hairs will now spawn 20 children, dramatically increasing the density.
        
    5. Set a small Radius to ensure the duplicated hairs are created very close to their parent guide.
        
    6. The Guide Index output is automatically generated. You can now use this index with a Clump Hair Curves node to make the duplicated hairs subtly clump back towards their original parent guide, creating a very natural, tufted fur effect.
        

This workflow is far more efficient than trying to manage a huge number of curves from the beginning and is the standard method for creating dense, realistic fur.