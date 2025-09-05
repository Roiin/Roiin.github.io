- **Editor:** Compositor Node Editor
    
- **Node Group:** Output
    
- **Core Function:** Acts as the final and mandatory endpoint for the entire node tree. Whatever image stream is connected to this node becomes the official output for the render, visible in the final image file (e.g., PNG, EXR) and the render window.
    
- **Key Properties & Settings:**
    
    - **Image (Socket):** Receives the final, processed image stream. This socket is the culmination of all the preceding nodes in the graph.
        
    - **Active State (Behavior):** If multiple Composite nodes exist, only one can be active at a time (indicated by a red header). The active node is the one that will be used for the final render output.
        
- **Practical Application:** While it has no creative function on its own, its role in the workflow is absolutely critical. It is the "finish line" of the compositing process.
    
    - **Molecular (Final Output):** Every single compositing node tree, no matter how simple or complex, must terminate with this node. A simple workflow might be Render Layers -> Glare -> Composite. The result of the Glare node is what you will see in your final render. If this node is not connected, your final render will be a black image.
        
    - **Organic (A/B Testing and Versioning):** The "active state" behavior is a powerful workflow tool. In a professional setting, you might develop two or three different color grades for a shot (e.g., a "warm look," a "cool look," and a "desaturated look"). You can have your main image stream branch out to three different Color Balance chains, with each one feeding its own Composite node. By simply selecting one of the Composite nodes to make it active, you can instantly switch which "look" is sent to the final render without reconnecting any nodes. This is an extremely efficient way to manage different versions or conduct A/B testing with a client.