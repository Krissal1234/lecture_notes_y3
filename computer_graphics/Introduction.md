Bitmap
- A bitmap is a 1's and 0's representation of pixels on a screen
- bitmapped graphics and GUI's aided the success of window based apps

improvements in hardware resulted in further development of computer graphics

Rendering 
- is the process of producing images from 3d models
Modelling 
- The creation/manipulation/storage of geometric objects

<font size=4>3D Models</font>
3D models are made from a mesh of simple geometric shapes (POLYGONS), combined to make a more complex shape
- A polygon is a simple flat plane with 3 or more sides. The point on a corner of a polygon is a vertex, lines between vertices are edges. The flat plane of a polygon is called a face
![[Pasted image 20240428123114.png|400]]

- Polygons can have textures applied to them
	- Textures or often 2d images that can be applied on top of other images
![[Pasted image 20240428123343.png|400]]
Daz Studio
- A powerful application for modelling scenes with characters
- With Daz you can customise and possilby alter existing 3d models

<font size =4>Coordinate Systems</font>
- Conventionally, a right-handed co-ordinate system is used in computer graphics theory
- Left handed systems: PolyRay, Pov-Ray, Bryce, DirectX, Unreal
- Right-handed system
![[Pasted image 20240428125113.png|400]]
  ![[Pasted image 20240428125423.png]]
- Left handed system
	- positive rotations are clockwise when looking from a positive axis towards the origin, the larger z-values are conveniently further from the viewer
	- In the left handed system, the z axis is reversed

An image is said to be realistic if it captures many of the effects of light interacting with real physical objects
**PhotoRealistic images**, the most realistic an image can be
- in the 80's images took days to render
- Sometimes photorealism is not what we want, we might want to display other effects

<font size=3>Orthonormal Bases and Frames</font>
- In computer graphics these orthonormal bases are commonly used to represent orientations in 3D space
	- Orthonormality ensures that these directions are mutually perpendicular, which is essential for transformations like rotations to behave predictably
- Two vectors are orthonormal if they are perpendicular to each other, i.e. thier dot product is 0
- geometric definition of the dot product:
- ![[Pasted image 20240428125742.png|300]]
- The orientation part of the coordinate system is stored as three orthnormal vectors, u,v and w, which are unit length, right handed (u x v = w) and mutually perpendicular
- These 3 vectors are the basis vectors of the coordinate system. As they are called an orthonormal basis (ONB)
	- The x, y and z vectors form a special ONB called the canonical basis, any vector can be represented in xyz cords:
		- ![[Pasted image 20240428140754.png|200]]

