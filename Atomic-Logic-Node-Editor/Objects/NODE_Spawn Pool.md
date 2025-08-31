- **Editor:** Logic Node Editor
    
- - **Node Group:** Objects Part 6
        
- **Core Function:** Manages a pre-allocated "pool" of objects to enable high-performance spawning, bypassing the costly process of creating and destroying objects in real-time.
    
- **Key Properties & Settings:**
    
    - **Input (Spawn):** A flow control input to trigger the spawning of one object from the pool.
        
    - **Input (Spawner):** An object whose position/rotation is used as the spawn point.
        
    - **Setting (On Startup):** If checked, the pool is created when the game starts.
        
    - **Setting (Simple):** Likely a toggle for a more basic pooling behavior.
        
    - **Setting (Object Instance):** The object that the pool will be filled with (e.g., a bullet).
        
    - **Setting (Amount):** The number of objects to create and hold in the pool.
        
    - **Setting (Life):** The lifespan in seconds for a spawned object before it is automatically returned to the pool.
        
    - **Setting (Visualize):** A debug option to see the pool's objects.
        
    - **Output (Spawned):** The object that was just activated and deployed from the pool.
        
- **Practical Application:** A critical optimization tool. Instead of using Add Object for every bullet in a machine gun, you create a pool of 50 bullets at the start. Firing simply takes an inactive bullet from the pool, activates it, and moves it. This is essential for preventing lag when many objects are needed quickly.