- **Editor:** Logic Node Editor
    
- **Node Group:** Physics Part 1 - Vehicle
    
- **Core Function:** Initializes a vehicle physics constraint on a chassis object, effectively turning a standard object into a functional vehicle simulation with wheels. This node is typically run once when the vehicle is first created.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the creation process.
        
    - **Input (Collider):** The main object that will serve as the vehicle's chassis/body.
        
    - **Input (Suspension, Stiffness, Damping, Friction, Wheel Mo...):** Float values that define the core physical properties of the vehicle's handling, such as suspension travel, springiness, and tire grip.
        
    - **Output (Vehicle Constraint):** The created vehicle physics constraint, which is used as an input for other vehicle control nodes.
        
    - **Output (Wheels):** A reference to the wheels associated with this vehicle constraint.
        
    - **Output (Done):** A flow control pulse that activates after the vehicle has been successfully created.
        
- **Practical Application:** The essential first step for any drivable vehicle. This node is used on game start or when a vehicle spawns to apply the special physics required to make it behave like a car.