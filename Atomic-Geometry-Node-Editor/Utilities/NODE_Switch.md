**Editor:** Geometry Nodes Editor  
**Node Group:** Control (Switching)

**Core Function:** Acts as a simple gate, selecting and passing through one of two inputs (True or False) based on a boolean condition.

**Key Properties & Settings:**

- **Type (Property):** Determines the data type for the inputs and output (e.g., Geometry, Float, Vector, Material).
    
- **Switch (Input):** A boolean value that makes the decision. If True, the True input is used; otherwise, the False input is used.
    
- **False (Input):** The data that is passed to the output if the Switch is False.
    
- **True (Input):** The data that is passed to the output if the Switch is True.
    
- **Output (Output):** The data from either the True or False socket, depending on the condition.
    

**Practical Application:**  
This is one of the most fundamental control nodes, used for any binary (on/off) decision. It's the primary way to add optional features to a procedural asset. For example, imagine you are building a procedural window and you want to give the user a simple checkbox to add or remove a decorative arch at the top.

- **The Goal:** To create a "Has Arch" checkbox that toggles the existence of an arch on top of a base window frame.
    
- **The Problem:** The arch is a separate piece of geometry that should only be created and included in the final model if the user requests it. You need a node that can act as a simple "if/else" statement for your geometry.
    
- **The Solution:** The Switch node is the perfect tool for this.
    
    1. Create a Switch node and set its Type to Geometry.
        
    2. Create a Group Input checkbox and name it "Has Arch". Connect this Boolean output to the Switch input of the Switch node.
        
    3. Generate your base rectangular window frame geometry. Connect this geometry to the False input of the Switch node. This is the default state.
        
    4. Generate the geometry for the arch. Use a Join Geometry node to combine the base window frame with the new arch geometry.
        
    5. Connect this combined geometry (frame + arch) to the True input of the Switch node.
        
    6. Connect the final Output of the Switch node to your Group Output.
        

Now, when the "Has Arch" checkbox is off, the Switch node passes through the simple frame. When the box is checked, it flips to the True input, passing through the frame with the arch attached. Crucially, the nodes that generate the arch geometry are only ever evaluated when the box is checked, making this an efficient way to manage optional complexity.