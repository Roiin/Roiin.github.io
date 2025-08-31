- **Editor:** Logic Node Editor
- **Node Group:** Events
    
- **Core Function:** A single-use event trigger. When its Condition input is met, it waits for the very next logic tick and then sends a single pulse through its Out socket before deactivating.
    
- **Key Properties & Settings:**
    
    - **Condition (Socket):** A boolean input. The node will only execute if it receives a True value.
        
    - **Out (Socket):** A flow control output that activates once on the subsequent frame.
        
- **Practical Application:** Useful for creating a one-frame delay in a logic sequence, often to ensure other processes have completed their updates for the current frame before proceeding