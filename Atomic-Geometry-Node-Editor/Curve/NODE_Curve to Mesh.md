- **Editor:** Geometry Nodes Editor
    
- **Node Group:** Curve (Operations)
    
- **Core Function:** The primary node for giving a curve physical volume. It extrudes a Profile Curve along the path of the main Curve, generating a solid mesh. If no profile is provided, it simply creates a chain of edges.
    
- **Key Properties & Settings:**
    
    - **Curve (Socket - Input):** The main curve that defines the path or length of the object.
        
    - **Profile Curve (Socket - Input):** A second, usually closed curve (like a Curve Circle) that defines the cross-sectional shape to be extruded.
        
    - **Scale (Socket - Input):** A field that can be used to scale the Profile Curve at different points along the main Curve. This is typically driven by the Radius attribute.
        
    - **Fill Caps (Socket - Input):** A Boolean. If True, it closes the open ends of the generated mesh with an N-gon, creating a manifold, solid object.
        
    - **Mesh (Socket - Output):** The resulting mesh geometry.
        
- **Practical Application:** This node is essential for modeling any object with a consistent profile, like an animal's horn.
    
    1. First, create a Curve Line or a Bézier curve to define the main sweeping shape of the horn. Use a Set Curve Radius node driven by an inverted Spline Parameter to make it thick at the base and thin at the tip.
        
    2. Next, create your Profile Curve. For a simple horn, a Curve Circle works well. For a more stylized, ridged horn, you could use a Star primitive.
        
    3. Connect the main horn curve to the Curve input of the Curve to Mesh node.
        
    4. Connect your Curve Circle or Star to the Profile Curve input.
        
    5. Connect the Radius attribute of the main horn curve to the Scale input.
        
    6. Enable Fill Caps.
        
    7. The result is a fully formed, 3D mesh of a horn. It perfectly follows the path of the main curve, has the cross-sectional shape of the profile curve, and is realistically tapered from thick to thin. You can easily create a vast variety of horns simply by changing the shape of the main curve or by swapping out the profile curve for a different shape.