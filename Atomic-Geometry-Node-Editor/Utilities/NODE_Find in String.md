- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Utilities (String)
    
- **Core Function:** Searches an input String for a specific Search substring and outputs the starting position (index) of the first match and the total Count of all matches.
    
- **Key Properties & Settings:**
    
    - **String (Socket - Input):-** The source string to be searched.
        
    - **Search (Socket - Input):** The substring to find within the String.
        
    - **First Found (Socket - Output):** An integer representing the index of the first character of the first match. If no match is found, this value is -1.
        
    - **Count (Socket - Output):** An integer representing the total number of non-overlapping times the Search string appears.
        
- **Practical Application:** This node is a powerful tool for parsing complex, semi-structured text. Imagine you have a long string describing a creature's attributes, like "SPECIES:Griffin WINGSPAN:12m DIET:Carnivore".
    
    1. **The Goal:** You want to extract the value for "WINGSPAN", which is "12".
        
    2. **The Problem:** The length of the species name can change, so you can't use a fixed Slice String position. You need to find the data dynamically.
        
    3. **The Solution:**
        
        - Use the Find in String node. String is your data string. Search for the key "WINGSPAN:". The First Found output will give you the index where "WINGSPAN:" starts.
            
        - You know "WINGSPAN:" is 9 characters long. You can add 9 to the First Found index to find the starting position of the value ("12").
            
        - Use another Find in String node to search for the next key, " DIET:". The First Found index of this search tells you where the wingspan value ends.
            
        - Now you have the start index and the end index of the "12m" substring. You can calculate its length (end - start).
            
        - Finally, use a Slice String node with your calculated start Position and Length to extract just the "12m" part. (You could then use further string manipulation to remove the "m").
            
    4. The Find in String node was the essential first step that allowed you to locate your data within a larger, more complex block of text.