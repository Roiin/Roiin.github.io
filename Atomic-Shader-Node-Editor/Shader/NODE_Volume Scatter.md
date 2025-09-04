**Editor:** Shader Editor  
**Engine(s) Supported:** [Cycles & Eevee] (Note: Some Phase functions are Cycles Only)  
**Node Group:** Shader

**Core Function:** Simulates light scattering within a volume, creating effects like fog, mist, clouds, or murky water where the medium itself becomes visible when illuminated.

**Key Properties & Settings:**

- **Volume (Output):** The shader's only output. It must be connected to the Volume input of a Material Output (for a contained volume object) or World Output (for global fog).
    
- **Density (Input):** The most important control. It determines the thickness or particle count of the volume. For global fog, very small values are needed. For dense smoke, higher values are used.
    
- **Color (Input):** The color of the light after it has been scattered. For neutral fog or steam, this is typically white.
    
- **Anisotropy (Input):** Controls the direction of the light scattering. A value of 0 scatters light uniformly. A positive value causes "forward scattering," making the volume glow when viewed from behind a light source (like steam). A negative value causes "backward scattering."
    
- **Phase (Property):** Selects the physical algorithm for scattering. Henyey-Greenstein is the versatile default. Others like Rayleigh (Cycles Only) are for fine atmospheric particles, and Mie (Cycles Only) is for larger particles like those in clouds or fog.
    

**Practical Application:**  
This node is the fundamental tool for creating atmospheric perspective and environmental fog. Imagine you are creating a vast outdoor scene, like a mountain range or a dense forest.

The problem is that in a default 3D render, the air is perfectly clear. A mountain 10 kilometers away will be just as sharp and contrasted as a tree 10 meters away. This looks fake and kills the sense of immense scale. You need to simulate the haze of a real atmosphere. The Volume Scatter node is the solution.

1. Switch to the Shader Editor's "World" context.
    
2. Add a Volume Scatter node.
    
3. Connect its Volume output directly to the Volume input of the World Output node. This will fill your entire scene's "empty" space with a scattering medium.
    
4. Set the Color to a very light gray or a slightly bluish-white to simulate atmospheric haze.
    
5. Critically, set the Density to a very low value, such as 0.005. High values will fill your scene with an opaque white-out. The effect must be subtle to be realistic.
    
6. The result is immediate and powerful. Objects close to the camera are clear, but as they get further away, they will progressively fade into the fog, losing contrast and taking on the color of the volume. This single node adds a profound sense of depth, scale, and mood to any large-scale environment.