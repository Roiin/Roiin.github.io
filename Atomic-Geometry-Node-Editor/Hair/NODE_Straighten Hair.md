**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Deformation)

**Core Function:** Interpolates the shape of each hair curve to a straight line connecting its root and its tip.

**Key Properties & Settings:**

- **Amount (Input):** The primary control for the straightening effect. At 0.0, the curve is unchanged. At 1.0, the curve becomes a perfectly straight line between its start and end points. Values in between produce a partial straightening.
    
- **Shape (Input):** A falloff that controls the straightening strength along the length of each hair. For example, you could straighten the root of a hair while leaving the tip curly.
    
- **Preserve Length (Input):** When enabled, this ensures that the hair does not shrink to the direct-line distance between the root and tip, but instead maintains its original length as it straightens.
    

**Practical Application:**  
This node is useful for blending out other deformers or for creating specific effects where hair needs to transition from a complex shape to a simple one. A great example is simulating an animal's fur becoming wet.

- **The Goal:** To make the fur on a wet animal, like a waterlogged fox, transition from its normal fluffy, curly state to a straightened, matted-down state.
    
- **The Problem:** The fox's dry fur has various noise and frizz deformers applied to give it volume. When wet, this volume should collapse, and the individual hairs should become straighter and clump together. You need a way to controllably "undo" the effects of the other deformers.
    
- **The Solution:** Use the Straighten Hair Curves node, driven by a "wetness" factor.
    
    1. Place the Straighten Hair Curves node near the end of your deformation chain.
        
    2. Create a single float input on your node group called "Wetness", ranging from 0.0 to 1.0.
        
    3. Connect this "Wetness" value directly to the Amount input of the Straighten Hair Curves node.
        
    4. Enable Preserve Length to prevent the fur from looking like it's shrinking.
        

Now, as you increase the "Wetness" slider from 0.0 to 1.0, the node will progressively straighten out all the curls, waves, and frizz that were created by the previous nodes. This collapses the fur's volume and makes it appear straighter and more clumped, creating a convincing "wet fur" effect with a single, simple control.