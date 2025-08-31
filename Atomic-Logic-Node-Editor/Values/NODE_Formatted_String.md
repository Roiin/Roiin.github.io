- **Editor:** Logic Node Editor
    
- **Node Group:** Values
    
- **Core Function:** Creates a new string by inserting input values into a specified format template.
    
- **Key Properties & Settings:**
    
    - **Format String (Field):** A text field where you define the template using placeholders like {}.
        
    - **Input Sockets (A, B, ...):** Dynamic data inputs that correspond to the placeholders in the format string.
        
    - **String (Output Socket):** The final, formatted string.
        
- **Practical Application:** A powerful and clean way to construct complex UI text. Example: Format String is "Ammo: {} / {}", with input A being current ammo and B being max ammo, to produce the output "Ammo: 25 / 100".