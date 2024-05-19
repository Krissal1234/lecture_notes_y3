## Coordinate Space
coordinate space is essentially a system for locating points in a given environment

Object space
- the coordinate space relative to an individual object in a scene
	- In this space, the geometry of the object is defined with respect to its own local coordinate system
- primitives defined in this space (geometric shapes like vertices, edges and faces)
- Each object in a scene has its own object space, unique to that object, this space allows the object to be transformed independently of other objects in the scene
- object spaces depend upon objects

World Space
- A global coordinate system that encompasses the entire scene, it serves as a common reference frame for positioning and orienting objects relative to each other.
- Objects placed or transformed into world space
- Object-to-word transformation
	- This transformation typically involves combining the objects local transformation (e.g. rotation and translation, relative to its own space) with any transformations needed to position it within the world space

Camera Space
- Also known as the view space or eye space, it is a coordinate system that is specific to the viewpoint of the camera, it defines the space from which the scene is viewed
- specific setting, e.g. camera is at origin, y-axis is up direction etc.
- simplifies computation (like rendering pipeline)
	- simplifies computation such as determining visibility, performing clipping, and projecting objects onto the screen, these are more straightforward in camera space because they are based on the perspective of the viewer
- camera is located in world space
- inverse view transform converts from world to camera space

<font size=4>Homogenous Coordinates</font>
- Derived from the study of perspective
- found in various areas of computer graphics
- These coordinates extend the traditional cartesian coordiante system  by adding an additional dimension, which enables operations such as translations to be represented as matrix multiplications
	- Traditional cartesian coordinates:
		- In a traditional Cartesian coordinate system, points in space are represented using (x,y,z) coordinates. For example, a point in 3D space might be represented as (3,4,2), where x=3, y=4, and z=2.
		- Homogeneous coordinates add an extra dimension to the traditional Cartesian system. Instead of representing a point in 3D space as (x,y,z), it is represented as (x,y,z,w). 
- Points specify a location in 3d space
- vectors specify a direction, e.g. surface normal
	![[Pasted image 20240428144719.png|300]]
	- here 't' is a parameter that an range from 0 to infinity, '0' i the origin of the ray and 'd' is the direction vector of the ray
	
	
	In computer graphics, homogeneous coordinates are useful for several reasons:
	- **Simplify Transformations:** They allow the combination of multiple transformations into one operation.
	- **Represent Points at Infinity:** Points at infinity can be represented using homogeneous coordinates, which is useful for rendering perspectives.
	- **Facilitate 3D Operations:** They simplify the mathematical operations involved in rendering 3D scenes on 2D screens, especially during the projection phase where 3D scenes are mapped to the 2D view of a camera.
	
	For instance, when you perform a perspective projection in a 3D rendering pipeline, objects that are farther away are made smaller by the perspective divide (dividing by w), simulating how things appear smaller in the distance in the real world. This is seamlessly handled by using homogeneous coordinates and the perspective transformation matrix.

<font size=3>Geometry</font>
- The study of shapes, sizes, patterns, positions with quantities that can be measured
- We can talk of a "unit circle", define it implicitly as $$x^2 + y^2 =1$$
	- Unit circle is a circle with radius 1 centred at the origin (0,0) on the cartesian coordinate plane
- Or explicitly as $$(cos\theta, sin\theta)$$
- The parametric or explicit form `(cos θ, sin θ)` represents the coordinates of points on the unit circle as a function of the angle θ with respect to the positive x-axis. This is an explicit way of representing the circle, as it provides a direct computation to get coordinates on the circle for a given angle.

- **Explicit Representations:**
    - These are direct ways of defining geometry where each element is individually specified.
    - **Point Cloud:** A collection of points in space. Each point is defined by its coordinates.
    - **Polygon Meshes:** A collection of vertices, edges, and faces that define the shape of a polyhedral object in 3D computer graphics.
    - **Subdivision:** A method of representing smooth surfaces by repeatedly refining polygon meshes.
    - **NURBS:** Non-Uniform Rational B-Splines are mathematical models used to generate and represent curves and surfaces.
- **Implicit Representations:**
    - These define shapes by a function or rule that can be evaluated to determine if a point is inside, outside, or on the surface.
    - **Algebraic Surfaces:** Surfaces defined by polynomial equations.
    - **L-Systems:** A method of generating fractals using recursive rules, often used to model plants.
    - **Fractals:** Complex patterns that are self-similar across different scales. Fractals are generated by recursive algorithms.
- **Choosing the Appropriate Representation:** It's crucial in computer graphics to choose the right representation for a given application or effect. Different representations have different advantages, such as ease of rendering, memory efficiency, or the ability to represent complex shapes or patterns.

<font size=4>Rendering Equation (kajiya)</font>
- Radiance is the measure of the amount of light energy along a ray defined by an origin point p and direction $\omega$. This is fundamental to physically based rendering as it helps simulate how light travels and interacts with surfaces
- A photorealistic renderer's goal is to accurately estimate the radiance that arrives at the virtual camera from a scene at any point p in direction $\omega$. the rendering equation provides a framework for calculating this radiance by taking into account light that is emitted and reflected from surfaces in a scene
- $L_0$ is the radiance at point $p$ direction $w_0$ at time $t$ from a position x