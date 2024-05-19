
## Raytracing

raytracing is used to simulate the interaction between objects and light within a field of view

- Light photons are simulated from one or more light sources

It is a rendering technique that can realistically simulate the lighting of a scene and its objects by rendering physically accurate reflections, shadows and indirect lighting
![[Pasted image 20240518122601.png|400]]

Ray casting: is the process in a ray tracing algorithm that shoots one or more rays from the camera (eye position) through each pixel in an image plane, and then tests to see if the rays intersect any primitives in the scene



Polyray usage
```
surface {
[surface definitions]
}
```

```
define shiny_red
	texture {
	surface {
		ambient red, 0.2 //shpere slightly red throughout
		diffuse red, 0.6 //where light hits the sphere, colour will be brighter
		specular white, 0.8 //shpere will have a white highlight
		mirofacet Reitz 10
		}
	}

```
![[Pasted image 20240518124511.png]]

### Povray Raytracer
**Pigment statment**
- The colour or pattern for an object is defined by a pigment statement, this statement specifies the basic colour pattern that will be applied to a surface of an object
**Texture statement**
- the texture statement is an object modifier that describes the appearance of an objects surface. This includes details about the material characteristics
- Textures in POV-Ray are combinations of three main components:
	- **Pigments**: These define the basic color or pattern as mentioned earlier.
	- **Normals**: These describe the small-scale surface irregularities that affect how light interacts with the surface, contributing to the appearance of bumps or roughness.
		- a method of simulating various patterns of bumps, dents, ripples or waves by modifying the surface normal vector
	- **Finishes**: These determine the surface properties such as shininess, reflectivity, and transparency.


#### Polyray object

```
sphere <x,y,z>, radius
```
where (x,y,z) is the center of the sphere in 3D coordinates

This statement creates a simple sphere with one light source and a black background

![[Pasted image 20240518125600.png|400]]

By default, polyray creates a out.tga file, in true-colour 24-bit image format (16.7 million colours). Using the -o parameter will force polyray to output the file in the TARGA subdirectory as img1.tga


## Anti-aliasing

If we want higher quality output, we can use anti-aliasing. this attempts to remedy the block effect of the pixels tin the image, by averaging out the values around every pixel, smoothing out sharp colour variations

It is a technique that removes the jagged edges in a rasterised image (an image rendered using pixels)
- The jagged edges problem occurs due to undersampling
	- undersampling results in a loss of information about a picture, which happens when sampling is don e at a frequency lower than the Nyquist sampling frequeency

Images can be rendered with multiple techniques:
- rasterisation and raytracing are two techniques
- rasterisation is the task of taking an image described in vector graphics format (shapes) and converting it to a raster image (a series of pixlels, dots or lines)

#### What causes jagged lines (undersampling)

To understand why jagged lines (or "jaggies") happen, it's helpful to know a bit about how digital images are created. Here are the key concepts explained in simpler terms:

#### Digital Sampling

1. **Pixels**: Digital images are made up of tiny squares called pixels. Each pixel has a single color, and when you look at many pixels together from a distance, they form a picture.
    
2. **Rendering a Scene**: When a computer creates (renders) an image, it decides the color of each pixel by looking at the scene and sampling it. Sampling means checking the scene at specific points and using that information to determine the pixel color.
#### Resolution Mismatch and Undersampling

1. **Resolution**: Resolution is the number of pixels in an image. Higher resolution means more pixels, which can show more detail. For example, an image with 1920x1080 pixels (Full HD) has a higher resolution than one with 640x480 pixels.
    
2. **Undersampling**: If the resolution (number of pixels) is too low to capture all the details of the scene, we get undersampling. This means there aren't enough pixels to show smooth lines and curves.
    
3. **Example**: Imagine drawing a diagonal line on a grid of squares. If the grid has many tiny squares (high resolution), the line looks smooth. But if the grid has only a few large squares (low resolution), the line looks like a staircase with visible steps. These steps are the "jaggies."
#### The Staircase Effect

1. **Staircase Effect**: When we have undersampling, diagonal lines and curves don't look smooth. Instead, they appear as a series of small steps or jagged segments. This happens because the pixels can't accurately represent the smooth transition of the line or curve.#
2. ![[Pasted image 20240518140709.png|300]]

with polyray, we use final.bat to tell the raytracer to perform adaptive anti-aliasing, taking a threshold value set by the -T parameter and the numebr of samples per pixel to be set by the -S parameter. 