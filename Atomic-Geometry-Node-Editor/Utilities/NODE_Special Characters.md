**Editor:** Geometry Nodes Editor  
**Node Group:** Utilities (String)

**Core Function:** Outputs special string characters, such as line breaks or tabs, that cannot be typed directly into a standard String node.

**Key Properties & Settings:**

- **Line Break (Output):** Outputs a newline character (\n). When combined with other strings, this character forces any subsequent text to start on a new line.
    
- **Tab (Output):** Outputs a tab character. This is typically used to create a horizontal indentation at the beginning of a line of text.
    

**Practical Application:**  
This node is fundamental for creating formatted, multi-line text for procedural objects. For example, imagine you are generating a series of informational placards for different animal models, and you need a consistent two-line format for each one: the scientific name on the top line and the common name below it.

- **The Goal:** To create a clean, two-line text label for a rhinoceros model that reads:  
    Ceratotherium simum  
    White Rhinoceros
    
- **The Problem:** Within a single String node, you cannot press 'Enter' to create a line break. The text will always output as a single, continuous line.
    
- **The Solution:** The Special Characters node provides the necessary Line Break character. You would use a Join Strings node to combine the different parts of your label in the correct order:
    
    1. A String node containing the text "Ceratotherium simum".
        
    2. The Line Break output from the Special Characters node.
        
    3. A String node containing the text "White Rhinoceros".
        

When this combined string is passed to a String to Curves node, it will be rendered correctly with the proper line break, creating a professional and readable two-line label for the rhino model.