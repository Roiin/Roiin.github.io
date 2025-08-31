- **Editor:** Logic Node Editor
    
- **Node Group:** Time
    
- **Core Function:** Functions as a metronome or a repeating timer. As long as its Condition is true, it will emit a pulse from its Out socket at a regular interval.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean that enables or disables the pulsing.
        
    - **Input (Gap):** A float for the time in seconds between each pulse.
        
    - **Output (Out):** A flow control pulse that activates at each interval.
        
- **Practical Application:** Used for any periodically repeating action: a flashing warning light, an enemy firing projectiles every 3 seconds, or a character taking poison damage every second.