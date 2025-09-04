**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles Only]  
**Node Group:** Shader

**Core Function:** Intercepts incoming light rays and "teleports" them to a new position and/or direction within the scene, enabling the creation of portals and other "impossible space" visual effects.

**Key Properties & Settings:**

- **BSDF (Output):** The standard shader output.
    
- **Position (Input):** The most critical input. This vector defines the new starting point in 3D space where the teleported ray will continue from.
    
- **Direction (Input):** The second critical input. This vector defines the new direction in which the teleported ray will travel from its new starting position.
    
- **Color (Input):** Allows you to tint the light that passes through the portal, useful for adding a colored shimmer effect.
    

**Practical Application:**  
This node is designed for creating visual effects that defy normal physics, most famously a magical portal or a "bigger on the inside" doorway. Imagine you want to create a glowing doorway in a wall that, instead of leading into the next room, looks directly into a completely different location, like an outdoor forest scene.

The problem is that you can't just cut a hole in the wall; you need to render the view from an entirely different part of your 3D world onto the surface of the doorway. The Ray Portal BSDF is the solution.

1. Create two objects that will act as the portal's entrance and exit points (e.g., two planes named "Portal_Entrance" and "Portal_Exit"). Place the "Portal_Entrance" in the wall and the "Portal_Exit" in the middle of your forest scene, facing the view you want to see.
    
2. Assign a new material to the "Portal_Entrance" object. In the shader, use the Ray Portal BSDF node.
    
3. The magic is in feeding the Position and Direction inputs. You need a node setup that calculates where an incoming camera ray would be if it were at the "Portal_Exit" instead. This typically involves using Object Info nodes to get the location and rotation of both portals and Vector Math nodes to transform the ray's initial position and direction from the entrance to the exit.
    
4. When you render, any camera ray that hits the "Portal_Entrance" plane is not rendered. Instead, the shader teleports it to the "Portal_Exit" plane in the forest, with its direction correctly transformed. The ray then continues on its path from there, capturing the forest scene.
    
5. The final result is that when you look at the doorway, you see a perfect, real-time view of the forest, creating a seamless and convincing portal effect.