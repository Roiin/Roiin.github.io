- **Editor:** Logic Node Editor
    
- **Node Group:** Input > Gamepad
    
- **Core Function:** Activates the vibration/rumble feature of a connected gamepad.
    
- **Key Properties & Settings:**
    
    - **Done (Socket):** Flow control input.
        
    - **Condition (Socket):** Boolean to enable/disable the vibration.
        
    - **Index (Socket):** Integer to select the gamepad index (0 for player 1, etc.).
        
    - **Left/Right (Sockets):** Float values (0.0 to 1.0) to control the intensity of the low-frequency and high-frequency motors.
        
    - **Time (Socket):** Float value for the duration of the vibration in seconds.
        
- **Practical Application:** Provides physical feedback to the player, such as when taking damage, firing a powerful weapon, or during explosions.