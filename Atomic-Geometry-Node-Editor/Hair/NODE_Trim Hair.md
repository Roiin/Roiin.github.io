**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Shortens or extends hair curves to a specified target length or by a scale factor.

**Key Properties & Settings:**

- **Length Factor (Input):** A multiplier applied to the original length of each hair. A factor of 0.5 will make all hairs half their original length.
    
- **Replace Length (Input):** When a value is connected here, it overrides the original length entirely, forcing all selected hairs to become this exact length.
    
- **Mask (Input):** A boolean or float field that controls where the trim effect is applied. This allows you to trim hair in specific areas.
    
- **Random Offset (Input):** Subtracts a random amount from the final length of each hair, which is essential for creating a natural, uneven trim.
    
- **Scale Uniform (Input):** When enabled, the curve's points are scaled uniformly to reach the target length. When disabled (default), the curve is simply cut off at the end.
    

**Practical Application:**  
This node is a fundamental grooming tool, equivalent to a stylist's scissors. It is used to define the basic shape and length of a hairstyle or fur coat. A classic example is giving a character a specific haircut, like a bob.

- **The Goal:** To create a clean, even bob haircut for a character, where the hair is cut to a uniform length around the head.
    
- **The Problem:** When hair is first generated, it often has a uniform length that follows the contour of the scalp, which does not look like a deliberate haircut. You need to trim the longer hairs at the top of the head so they end at the same level as the shorter hairs at the nape of the neck.
    
- **The Solution:** Use the Trim Hair Curves node with a guide mesh to define the cutting line.
    
    1. First, generate the base hair on the character's head, combed down.
        
    2. Create a separate, invisible mesh shape that represents the desired silhouette of the bob haircut.
        
    3. Use a Geometry Proximity node to find the distance from each point on the hair curves to this guide mesh. The Distance can be used to create a Boolean mask: True for any hair outside the guide mesh and False for any hair inside.
        
    4. Connect this Boolean field to the Mask input of the Trim Hair Curves node.
        
    5. Now, the node will only affect the hairs that are "too long" (outside the guide shape).
        
    6. By setting the Length or Length Factor appropriately, you can trim these hairs so they end right at the boundary of the guide mesh. Add a small Random Offset to make the cut look less perfectly artificial.
        

The result is a clean haircut that follows the precise shape you defined with your guide object, allowing for a high degree of artistic control over the final hairstyle.