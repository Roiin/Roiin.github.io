**Editor:** Geometry Nodes Editor  
**Node Group:** Control (Zone)

**Core Function:** Executes a contained group of nodes a specified number of times in a loop, passing the output of one iteration as the input to the next.

**Key Properties & Settings:**

- **Iterations (Input):** An integer that determines the total number of times the loop will run.
    
- **Repeat Input / Repeat Output Nodes:** These two nodes define the start and end of the zone. Sockets on these nodes represent data that is "stateful"—it is passed from one iteration to the next. You can add more sockets for any data type you need to loop.
    
- **Iteration (Zone Data):** An output available inside the zone that provides the current loop number, starting from 0. This is useful for making changes that progress with each iteration.
    
- **Inspection Index (Property):** Allows you to view the data or geometry at a specific iteration number when using the Viewer Node.
    

**Practical Application:**  
Repeat zones are the core of any iterative or recursive modeling task, where an operation is built upon the result of the previous step. A classic example of this is generating the branching structure of a tree.

- **The Goal:** To generate a tree by starting with a single trunk and repeatedly adding smaller, rotated branches to the tips of the previous generation of branches.
    
- **The Problem:** A tree's structure is self-similar. A small branch is like a miniature version of the entire tree. This kind of recursive growth is impossible with a simple, linear node setup. You need a loop that can take the tree's current state, add a new layer of complexity, and feed that back into itself.
    
- **The Solution:** The Repeat zone provides this exact looping mechanism.
    
    1. Start with a simple mesh line for the trunk outside the zone. Connect it to the Geometry socket on the Repeat Input node.
        
    2. Set the Iterations to a value like 4 to create four levels of branching.
        
    3. **Inside the zone**, take the geometry from the previous iteration.
        
    4. Find the endpoints of all the curves in that geometry (e.g., using Endpoint Selection).
        
    5. On those endpoints, instance new, smaller, slightly rotated lines (the next generation of branches).
        
    6. Join the new branches with the input geometry.
        
    7. Connect this combined, more complex geometry to the Geometry socket on the Repeat Output node.
        

The zone will run this process four times. In the first loop, it adds branches to the trunk. In the second, it takes the trunk-and-branches and adds smaller branches to the tips of the first set. This continues, with each iteration adding a new level of detail. The final geometry that emerges from the zone is a complex, multi-layered branching structure created from a simple, repeated rule.