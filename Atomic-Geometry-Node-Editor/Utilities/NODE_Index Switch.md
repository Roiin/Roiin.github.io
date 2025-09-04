**Editor:** Geometry Nodes Editor  
**Node Group:** Control (Switching)

**Core Function:** Selects and passes through one of its multiple data inputs based on an integer Index value.

**Key Properties & Settings:**

- **Type (Property):** Determines the data type for all sockets on the node (e.g., Geometry, Float, Vector, Material, etc.).
    
- **Index (Input):** An integer that chooses which input to forward to the output. An index of 0 selects the first input, 1 selects the second, and so on.
    
- **Item Inputs (Dynamic):** A list of data inputs that are created as needed. Only the data connected to the socket chosen by the Index is processed, making this node very efficient.
    
- **Output (Output):** The single output that passes through the data from the selected input socket.
    

**Practical Application:**  
This node is the fundamental building block for creating procedural assets that can switch between different models or components. Imagine you are creating a single "Procedural Tree" asset for a library, but you want it to be able to generate a pine, an oak, or a birch tree from the same node group.

- **The Goal:** To create a single integer slider, "Tree Type," that switches the output of the node group between three completely different tree geometries.
    
- **The Problem:** You have three separate branches in your node tree, each generating a different type of tree. You need a clean, efficient way to select only one of these geometries to be the final output, without computing the other two.
    
- **The Solution:** The Index Switch node acts as a multi-way gate for your geometry.
    
    1. First, create an Index Switch node and set its Type to Geometry. It will create multiple geometry input sockets.
        
    2. Connect the final geometry of your pine tree generator to the first input (index 0).
        
    3. Connect your oak tree geometry to the second input (index 1).
        
    4. Connect your birch tree geometry to the third input (index 2).
        
    5. Create a single integer input for your main node group, name it "Tree Type," and set its range from 0 to 2.
        
    6. Connect this "Tree Type" slider to the Index input of the Index Switch node.
        
    7. Connect the single Output of the Index Switch node to the final Group Output.
        

Now, changing the "Tree Type" slider from 0 to 1 to 2 will instantly switch the output geometry between the pine, oak, and birch models. This is highly performant because Blender will only evaluate the nodes connected to the currently selected input, ignoring the other complex tree generators.