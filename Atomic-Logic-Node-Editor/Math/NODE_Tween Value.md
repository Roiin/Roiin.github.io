- **Editor:** Logic Node Editor
    
- **Node Group:** Math
    
- **Core Function:** Smoothly animates a value from its current state to a target state over a specified duration, with easing options.
    
- **Key Properties & Settings:**
    
    - **Input (From):** The starting value.
        
    - **Input (To):** The target value.
        
    - **Input (Duration):** The time in seconds for the transition.
        
    - **Setting (Type):** The data type to tween (Float, Vector, etc.).
        
    - **Setting (On Demand/Curve):** Controls the easing of the transition (linear, ease-in, etc.).
        
    - **Output (Done):** A flow control pulse when the tween starts.
        
    - **Output (Reached):** A flow control pulse when the tween finishes.
        
    - **Output (Result):** The animated value at the current frame.
        
    - **Output (Factor):** The current progress of the tween (0.0 to 1.0).
        
- **Practical Application:** The core of smooth, non-physics-based animations. Used for opening doors, moving UI elements, changing camera FOV smoothly, or animating the color of a light.