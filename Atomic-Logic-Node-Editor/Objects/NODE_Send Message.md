- **Editor:** Logic Node Editor
    
- **Node Group:** Objects Part 6
    
- **Core Function:** A communication node that sends a message from one object to another (or to all objects). This allows for decoupled logic systems.
    
- **Key Properties & Settings:**
    
    - **Input (Condition):** A boolean flow control to trigger the action.
        
    - **Input (From):** The object sending the message.
        
    - **Input (To):** The target object receiving the message. If left empty, the message is broadcast to all objects.
        
    - **Input (Subject):** The "title" of the message, used by the receiver to filter messages.
        
    - **Input (Body):** The content of the message, can be various data types.
        
    - **Output (Done):** A flow control pulse that activates after the message is sent.
        
- **Practical Application:** A pressure plate can send a message with the subject "Open Door" to a specific door object. This is a very flexible and powerful way to make game elements interact without being directly linked.