

#### What is a bitmap
a Bitmap is a ones and zeros representation of the rectangular array of points (pixels = picture elements) on the screen

A bitmap is also called "raster", it is created from rows of different colourd pixels that together form an image.
- In their simplest form, bitmaps have only two colours, with each colour being black or white
- with increasing complexty, an image can include more colours, e.g. of bitmaps are JPEG, PNG, BMP. As well as the image displayed on a computer screen is also a bitmap

Bitmaps are oftenn affected by resolution, enlarging a bitmap graphic will make it look jagged

#### Vector Graphics
are constructed using mathematical formulas describing shapes, colours and placement. Rather than a grid of pixels, a vector graphic consists of shapes, curves, lines and text which together form a picture

- While a bitmap image contains information about the color of each pixel, a vector graphic contains instructions about where to place each of the components. 
- It is even possible to embed a bitmap graphic within a vector graphic, which is how vector-bitmap hybrid graphics work. It is not possible, however, to embed vector information within a bitmap.
- Examples of vector graphic formats are PICT, EPS, and WMF as well as PostScript and TrueType fonts. These are created with GIS and CAD applications as well as drawing programs like FreeHand.

vector graphics are often not affected by resolution, reshaping it wont cause damage


### Rendering
Rendering is a technique of producing images from a 2D or 3D model . Also the results of such a model can be called a render


## Modelling Techniques: PhotoRealistic rendering


a number of techniques may be used to generate a scene including 
- Raytracing
- scan-line polygon rendering
- wire-frame (outlines only)
- hidden-line rendering (lines in the wireframe that are note visible are not drawn)
- gouraoud shading (texturing at vertices only)
- radiosity (simulating the way directly illuminated surfaces act as indirect light sources that illuminate other surfaces)

#### Raytracing

Raytracing is used to simulate the interaction between objects and light within a view
Light photons are simulated from one or more light sources. Those ending up in the background are ignored since they are not visible

>"The program Polyray is a rendering program for producing scenes
of 3D shapes and surfaces. The means of description range from
standard primitives like box, sphere, etc. to 3 variable polynomial
expression, and finally (and slowest of all) surfaces containing
transcendental functions like sin, cos, log. The files associated
with Polyray are distributed installed in four parts: the executable,
a collection of document files, a collection of sample data files, and
a few small utility programs.


anti-aliasing in polyray can be done using final.bat however it will take longer


### Daz Studio
A software program which has been used in actual movie production

DAZ STUDIO WORKFLOW
Load scene file
Load characters + props
Accessorize the characters
Arrange the scene
Pose characters
Set up lighting
Position the camera
Render the scene


Clothing problems
- Some problems with clothes not matching figures used to be solved by hiding body parts,
- however, there is a new solution for Genesis, wheere you can apply a smoothing modifier


## Conventions, Definitions and Lighting

![[Pasted image 20240518150242.png|400]]

Coordinate systems are used to specify the position and orientation of objects in a virtual space


Conventionally a right-handed coordinate system is used in computer graphics theory, however in practical usage one might prefer to use a left-
handed system (this is done by Polyray, for instance). The z-axis can be
thought of as receding out of the page.

- With a left-handed system, positive rotations are CLOCKWISE when
looking from a positive axis toward the origin, and larger z-values are conveniently further from the viewer.

- Realistic Image - An image, picture etc is said to be REALISTIC if it  captures many of the effects of light interacting with real physical objects.

We speak of images being "more" realistic than others.
- Photographic Realism
	- the most realistic an image can be.
(Photorealism is an art movement of the 60's where painters were
inspired from photographs)

Sometimes photorealism is not what we want, and instead reality is
altered for aesthetic, surrealistic or simply abstract effects. The
production of realistic pictures is essential in areas like simulation,
design, entertainment & advertising, research, education, command &
control.

Realistic images that change dynamically are called simulation systems.

### Explanation of Illumination Models in Computer Graphics

The text describes different illumination models used in computer graphics to determine the color and brightness of a surface at a given point.

### Key Concepts

#### Illumination Models

1. **Self-Luminous Objects**:
    
    - In the simplest model, there are no external light sources. This is an unrealistic scenario where objects are self-luminous and do not reflect light from any source.
    - The illumination equation for this model is $I=k_i$​, where:
        - $I$ is the resulting intensity.
        - $k_i$​ is the object's intrinsic intensity (a constant value).
2. **Ambient Light**:
    
    - A more realistic model involves ambient light, which is a diffuse, non-directional source of light created by multiple reflections from various surfaces in the environment.
    - The illumination equation for ambient light is $I=I_ak_a$​, where:
        - $I_a$​ is the intensity of the ambient light, which is constant for all objects.
        - $k_a$​ is the ambient-reflection coefficient, ranging from 0 to 1, representing the proportion of ambient light reflected by the surface.

### Detailed Explanation

#### Self-Luminous Model

- **Extreme Illumination Model**:
    - Assumes no external light sources, only self-luminous objects.
    - The illumination equation $I=k_i$​ means that the intensity (brightness) at a point is solely determined by the object's intrinsic property $k_i$​.



#### Ambient Light Model

- **Diffuse, Non-Directional Light**:
    - Ambient light is considered a product of multiple reflections from surfaces in the environment, creating a uniform light source.
    - The illumination equation I=IakaI=Ia​ka​ describes the effect of ambient light on the object's surface:
        - Ia​ (ambient light intensity) is constant for all objects.
        - ka​ (ambient-reflection coefficient) characterizes how much ambient light is reflected by the surface.
    - **Coefficient kaka​**:
        - A material property that determines the amount of ambient light reflected. Values range from 0 (no reflection) to 1 (full reflection).
        - It is an empirical value and doesn't directly correspond to any specific physical property of materials.

$I=I_ak_a$

### Importance of Ambient Light

- **Uniform Illumination**:
    
    - Ambient light ensures that objects are lit uniformly regardless of their position or orientation.
    - Objects reflect ambient light proportionally to their ambient intensity, ensuring consistent illumination across surfaces.
- **Point Light Source**:
    
    - When using a point light source, which emits light equally in all directions from a single point, the object's brightness varies depending on its distance and direction relative to the light source.

### Reflections

Lambertian reflection
- dull, matt surfaces, e.g. chalk, exhibit diffuse reflection (aka lambertian reflection)
- These surfaces appear equally bright from all viewing angles since they reflect light with equal intensity in all directions

Specular Reflection
- This type of reflection can be observed on shiny surfaces, e.g. an apple illuminated by a bright white light
- This reflection causes a highlight on the apple, while the light reflected from the rest of the apple is caused by diffuse reflection
- At the highlight the apple does not appear to be red, but white, the colour of the incident light.
- The area around the highlight where light is not directly reflected is called ranking light
![[Pasted image 20240518154129.png|400]]
Most objects have a light area and a shadow area. Most detail is in the
light area as it receives the majority of light. The shadow area is the part
that does not receive direct light from the light source. It has the least
amount of detail as a result. Where there is a single light source on an
object like a ball, roughly half the ball will be in the shadow area and half
in the light area. The core shadow is a band of shadow separating the
raking light from the shadow area of the ball. It is the shadow that defines
the form, so it is important for the artist. The core shadow is the darkest
one. The shadow area receives indirect light reflected from other light
sources onto the ball. This reflected light gives definition to the shadow
area of an image. The cast shadow is a shadow area where the object has
interrupted light travelling from the light source to the table or plane.


### Composition
Art can have a purpose such as a message or feeling to express, both in commercial or fine art


# Graphs and polygon-nets (mathematics of lines and edges)
## Definition

A Graph is a pair of two sets $G=(P,E)$, where $P$ is a non-empty set of $n$ distinct (different) points $p_0,p_1,\ldots,p_{n-1}$ and $E$ is a set of lines $(p_k,\ldots,p_l)$. Elements of $P$ are called knots and elements of $E$ are called edges. $G=(P,E)$ is called a geometric Graph when $P$ is a subset of $\mathbb{R}^d$ with $d\geq2$.

- Two edges are said to be neighbouring edges if they have one point in common.
- Edges in general have NO DIRECTION and are just written as $p_kp_l$.
- Half-edges are edges together with a given direction.

### Definition

A geometric Graph $Q=(P,E)$ with $P=\{p_0,p_1,\ldots,p_{n-1}\}\subseteq\mathbb{R}^d$, $d\geq2$ and $E=\{(p_0,p_1),\ldots,(p_{n-2},p_{n-1})\}$ is called a Polygon.

- A polygon is called 2D if all its edges lie in a common plane, closed if $p_0=p_{n-1}$ (divides outside and inside).

### Polygon-net
A set $M$ of finitely many closed polygons $Q_i$ is called a Polygon-net if:
- The intersection of the interior of any two polygons considered is empty.
- The intersection of 2 Polygons out of $M$ is either empty or a single point (vertex) $p\in P$ or an edge $e\in E$.
- Each edge from $E$ is associated with a Polygon.
- The set of all edges, which are associated with just a single polygon, is either empty or forms a single closed polygon net by itself.
- A polygon net is closed if the set of all edges associated with just a single polygon is empty.

The sets of all points $P$ and all edges $E$ again form a Graph.


continue Polyhedrons



## Chapter 5 Vertex Based Boundary Models

![[Pasted image 20240519111648.png]]
**Representation of 3D Objects**: The slide highlights the importance of representing 3D objects in graphics using a vertex-based boundary model. This method is essential in various applications like CAD, physical simulation, and rendering.

Given the coordinates of a 3D cube:

- Vertices: (-1,-1,-1), (-1,-1,1), (-1,1,-1), (-1,1,1), (1,-1,-1), (1,-1,1), (1,1,-1), (1,1,1)
#### Vertex List

We label the vertices as follows for clarity:

- V0=(−1,−1,−1)
- V1=(−1,−1,1)
- V2=(−1,1,−1)
- V3​=(−1,1,1)
- V4=(1,−1,−1)
- V5=(1,−1,1)
- V6=(1,1,−1)
- V7=(1,1,1)

#### Edge List

Edges are pairs of vertices. The cube has 12 edges:

- E0=(V0,V1)
- E1=(V0,V2)
- E2=(V0,V4)
- E3=(V1,V3)
- E4=(V1,V5)
- E5=(V2,V3)
- E6=(V2,V6)
- E7=(V3,V7)
- E8=(V4,V5)
- E9=(V4,V6)
- E10=(V5,V7)
- E11=(V6,V7)

#### Face List

Faces are sets of edges that form the boundaries of the cube's surfaces. The cube has 6 faces:

- Front face: F0=(E0,E3,E4,E10)
- Back face: F1=(E1,E5,E6,E11)
- Top face: F2=(E5,E7,E10,E11)
- Bottom face: F3=(E0,E2,E8,E9)
- Left face: F4=(E1,E2,E6,E9)
- Right face: F5=(E3,E4,E8,E7)

### Key Points

 **Implicit Storage of Edges**

- **Edges Are Not Directly Stored**:
    - In a vertex-based boundary model, edges (the lines connecting vertices) are not stored explicitly as separate entities. Instead, they are implied by the connectivity information in the polygon (face) definitions.
    - **Example**: If a face (polygon) is defined by the vertices (V0,V1,V2,V3) the edges (V0,V1),(V1,V2), (V2,V3), and (V3,V0) are implied by this definition.
    - **Counted Twice**: Each edge is shared by two adjacent faces. For example, the edge (V0,V1) might be part of both the front face and the bottom face of a cube. This means the edge is counted in the edge list of both faces.

	
### Separation of Topology and Geometry

- **Topology**:
    - This refers to the connectivity information, which describes how vertices are connected to form edges and faces. In other words, it tells us which vertices are linked together to make the structure of the object.
    - **Example**: The indices (0,1,2,3) might indicate that these vertices form one face of the cube.
- **Geometry**:
    - This refers to the actual coordinates of the vertices in space. Geometry provides the spatial information needed to position the vertices correctly.
    - **Example**: Vertex V0​ might have coordinates (0,0,0) and vertex V1​ might have coordinates (1,0,0).
- **Orientation of Faces**:
    
    - The order of vertices in the face list is important for rendering. Proper orientation helps in rendering correctly and aids in operations like backface culling (removing faces not visible to the camera in OpenGL).
- **Using Indexes**:
    - Instead of repeatedly storing the coordinates of vertices for each face, we store the coordinates once in a vertex list. Faces are then defined using indices that refer to these vertices.
    - **Efficiency**: This approach saves memory because it avoids redundant storage of vertex coordinates.


Euler--Poincare Formula
- It describes the relationhip of the number of vertices, the number of edges and the number of faces of a manifold
- to check if an object is a valid solid

![[Pasted image 20240519120332.png|400]]

some objects  may not satisfy the formula but not encompass any volume


### Chapter 6 Cameras, viewpoints and clothing in Daz


In Daz there are six present orthogonal cameras which cover all the six cardinal directions

Daz 4 has a special perspective View, "camera" but its not very adjustable


Using Default camera you can view diferent  views, e.g. left view, top view etc..


Applying clothing to a character
clothing fits automatically to a characcter if
1. the character is already selected
2. the clothing was created for the character#

with clothing you can always try to play with the scale (x,y,z) and rotate to improve the fit


Under pose we can find MAT's (material presets) for items like clothing. Buy not all items come with one. Instead we can go to the surfaces tab. 

We can also use magnetize pose which automatically adjusts the clothing;s morph settings to match any body morphs usdeed in the character
- we can change opacity or add an opacity map

Opacity map tells daz what parts of the surface are to be transparent and how much. White is 100% opaque and black is 100% transparent
![[Pasted image 20240519121802.png]]



### Chapter 10

#### Storyboarding
Storyboards are still scenes for motion pictures or animation sequences, pre-planned and laid-out in hand painted or drawn frames
- They are an animation in outline form

They often have sequential art, however they are not meant to be 'read' but there rather to bridge the gap between a script and the final animation o rfilrm

- it suggests shots and to envision staging and lighting

A scene from above referred to birds eye view
A scene from below is referred to worms eye view


### Animation techniques
To animate means to bring to life. animation encompasses motion dynamics, update dynamics (shpae, colour, stucture), changes in lighting, camera position, orientation and even changes in rendering technique

Scientific application of computer graphics and especially of animation. It  may involve other disciplines such ass computational geometry and datbases. A number of animations in scientific visualisation are generated from large datasets generated by simulations of scientific phenomena, e.g. fluid flow simulaions

### Temporal Aliasing in Animation

- **Temporal Aliasing**: This occurs when an animation's aspect (i.e., the visual changes in the scene) changes too quickly relative to the number of frames displayed per second. An example of temporal aliasing is the “wagon-wheel effect,” where wheels appear to move backward or rotate incorrectly due to insufficient frame rates.

### Frame Rates in Different Media

- **Videotape**:
    
    - **NTSC**: The National Television System Committee standard used in North America and parts of Asia, which shows videotape at 29.97 frames per second (fps).
    - **PAL**: The Phase Alternating Line standard used in Europe and other regions, which shows videotape at 25 fps.
- **Photographic Film**:
    
    - Typically has a frame rate of 23.976 fps, often referred to in the context of 3:2 pulldown. This method is used to convert film's frame rate to NTSC's frame rate for television broadcast.

### Frame Rates in European Movies

- Most European movies are filmed at 25 fps, adhering to the PAL standard. This can be either interlaced (where each frame is split into two fields shown sequentially) or progressive (where each frame is shown as a whole).

### Adequacy of Frame Rates

- The frame rates mentioned (29.97 fps, 25 fps, and 23.976 fps) generally provide adequate results for most applications, ensuring smooth motion and minimizing issues like temporal aliasing.

### Real-Time Animation

- For every frame to take advantage of these rates, a new image must be generated for each frame.
- **Importance in Real-Time Systems**:
    - Real-time animation is crucial in applications like flight simulators and other control systems where timely and accurate visual feedback is necessary.
    - Such systems require architectures capable of supporting basic animation in real time to ensure that visual representations match the real-time dynamics accurately.


### ### Conventional Animation Process

1. **Story and Storyboard**:
    - The process begins with writing a story. Once the story is written, a storyboard is created. The storyboard serves as a visual representation of the narrative, showing the sequence of events and key scenes.
2. **Recording a Soundtrack**:
    - If necessary, a soundtrack is recorded at this stage. The soundtrack provides the audio foundation for the animation, including dialogue, music, and sound effects.
3. **Drawing Key Frames**:
    - Key frames are the next step in the process. These are specific frames where the entities being animated are at significant or extreme positions. Key frames define the starting and ending points of any smooth transition and are crucial for understanding the motion and timing of the animation.
4. **Inbetweening**:
    - After the key frames are drawn, the intermediate frames, known as inbetweens, are filled in. This process is called inbetweening. It involves creating the frames that transition smoothly between key frames to ensure fluid motion.
5. **Pencil Test**:
    - A trial film, known as a pencil test, is created using these key frames and inbetweens. The pencil test allows animators to review the motion and timing of the animation before finalizing it.
6. **Transferring to Cels**:
    - The pencil-test frames are then transferred to sheets of acetate film called cels. This can be done either by hand-copying in ink or by photocopying directly onto the cels.
7. **Multiplane Animation Technique**:
    - In this technique, multiple layers of cels are used. These layers include a background that remains static and additional layers for elements that move (translation). This allows for more complex and dynamic scenes.
8. **Coloring and Assembly**:
    - The cels are colored or painted. Once all the cels are prepared, they are assembled in the correct sequence.
9. **Filming**:
    - The assembled cels are then filmed to create the final animation. Different parts of this process are often handled by different specialists.
### Cels in Animation

**Cels** (short for **celluloids**) are transparent sheets of acetate or plastic on which characters, objects, and other elements of an animation are drawn or painted. The use of cels is a traditional animation technique that has been fundamental to the process of creating animated films and shows. Here’s a more detailed explanation:

#### Characteristics of Cels

1. **Transparency**:
    
    - Cels are transparent, allowing animators to layer multiple cels on top of one another. This layering is crucial for creating complex scenes where multiple elements move independently.
2. **Durability**:
    
    - Made from durable materials like cellulose acetate, cels can withstand repeated handling during the animation process.
### Key-Frame Animation in Computer Graphics

- The principles of key-frame animation used in conventional animation are also applied in computer-based systems. In computer graphics, key-frame animation involves setting key positions for objects and having the computer generate the inbetweens, mimicking the traditional process.


The **organisational process** of an animation is described by its storyboard, by a **route sheet** describing each scene and the people responsible for producing the scenes various aspects and by the **exposure sheet** which is a detailed description of the animation, describing the dialogue, the order of all figures in the frame, the choice of background and the camera position of each frame 
- the entire process is usually sequential but often iterative

Computers can assist in this process in various ways., Principally the drawings must be digitalised, either by optical scanning, traicing the drawings with a tablet, using a drawing application


![[Pasted image 20240519130034.png]]


## chapter 11 

depth files, csg and particle systmes


## Chapter 12 Grammer Based Models
https://medium.com/@hhtun21/l-systems-draw-your-first-fractals-139ed0bfcac2
L-Grammers which were originally developed by Lindenmayer are a way for describing the structure of certain plants

![[Pasted image 20240519130319.png]]![[Pasted image 20240519130333.png]]![[Pasted image 20240519130349.png]]![[Pasted image 20240519142429.png]]
![[Pasted image 20240519142449.png]]
https://medium.com/@hhtun21/l-systems-draw-your-first-fractals-139ed0bfcac2



![[Pasted image 20240519142547.png]]



i think vertex and edges should be the other way round