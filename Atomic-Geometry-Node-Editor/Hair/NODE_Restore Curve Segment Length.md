**Editor:** Geometry Nodes Editor  
**Node Group:** Hair Nodes (Utility)

**Core Function:** Adjusts the points of a deformed curve to make the length of each individual segment match its length from a previous, undeformed state.

**Key Properties &Settings:**

- **Curves (Input):** The deformed curve geometry whose segment lengths you want to restore.
    
- **Factor (Input):** A multiplier for the strength of the restoration effect.
    
- **Reference Position (Input):** The crucial input. This requires a Position attribute that was captured before the deformation occurred, typically using a Capture Attribute node.
    
- **Pin at Parameter (Input):** A value from 0 to 1 that defines a point along the curve (0=root, 1=tip) that will be held in place, with the restoration propagating from that point.
    

**Practical Application:**  
This node is a more advanced alternative to the simple Preserve Length checkbox found on many deformer nodes. It offers more control for correcting length changes after a series of complex deformations. Imagine you have applied several noise and frizz deformers to a set of hair curves, and the combined effect has caused them to stretch and become unnaturally long.

- **The Goal:** To force the deformed, stretched hair curves back to their original, natural length without losing the shape of the deformation.
    
- **The Problem:** Simple Preserve Length options on individual nodes might not be sufficient if multiple deformations are interacting in complex ways. You need a definitive way to enforce the original length as a final step.
    
- **The Solution:** Use a Capture Attribute / Restore Curve Segment Length workflow.
    
    1. At the very beginning of your node tree, immediately after the initial hair curves are generated, use a Capture Attribute node to store their Position field. This captures the original, undeformed state. Let's call this captured attribute "Rest_Position".
        
    2. Proceed with all of your deformation nodes (Noise, Frizz, Clump, etc.). These operations may stretch the curves.
        
    3. At the very end of the deformation chain, add a Restore Curve Segment Length node.
        
    4. Connect your "Rest_Position" attribute (from step 1) into the Reference Position input.
        
    5. Typically, you would set Pin at Parameter to 0.0 to keep the roots of the hair locked to the scalp and have the length correction affect the rest of the strand.
        

The node will now look at each segment of the deformed curves, compare its length to the length of the corresponding segment in the "Rest_Position" data, and adjust the point positions to make the lengths match. This effectively rescales the curve back to its original length while preserving the detailed shape added by all the deformer nodes.