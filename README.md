# Modern Computer Graphics
Built core modules: transformation matrices, triangle rasterizer with Z-buffering, Blinn–Phong shading with texture/bump/displacement mapping, Bézier curve rendering, ray–triangle intersection, and BVH traversal.  
Gained extensive experience translating math (linear algebra, numerical methods) into performant C++ code, with debugging, modular design, and optimization for rendering tasks.

## HW1: Rotation and Projection
In this assignment, I implemented the fundamental transformations needed to render a triangle on the screen. Specifically, I constructed a rotation matrix and a perspective projection matrix, which transform 3D points into screen space for rasterization. Using the provided draw_triangle function, the transformed vertices are connected to form a wireframe triangle that can be displayed and rotated around the z-axis. 
### Features
- **get_model_matrix(float rotation_angle):**  
  Construct the model transformation matrix and return it. Only the rotation matrix around the 3D z-axis is implemented, without handling translation or scaling.
  
- **get_projection_matrix(float eye_fov, float aspect_ratio, float zNear, float zFar):**  
  Construct the perspective projection matrix using the given parameters and return it.

## HW2: Triangles and Z-buffering
In this assignment, I extended the previous wireframe rendering to rasterize filled triangles. The task involves implementing triangle rasterization, point-in-triangle testing, and z-buffering to correctly render solid triangles with proper depth handling.
### Features
- **rasterize_triangle(const Triangle& t)**
Perform triangle rasterization. For each pixel inside the triangle’s bounding box, check if its center lies within the triangle. If inside, compute the interpolated depth value and compare it with the depth buffer. Update the pixel color and depth buffer if it is closer to the camera.

- **insideTriangle()**
Test whether a given point lies inside the triangle. This function can be customized and updated based on your own implementation style.
- **z-buffer**
Store interpolated depth values and perform depth testing to ensure correct rendering order. Pixels with smaller depth values overwrite those with larger ones.

## HW3: Pipeline and Shading
In this assignment, I extended the rasterization pipeline by integrating modern rendering techniques such as shading and texture mapping. Building on the previous assignment, where triangles were rasterized with basic interpolation, I implemented several fragment shaders to simulate more realistic visual effects. Specifically, I filled in the projection matrix, applied the Blinn–Phong lighting model, and extended it with texture shading, bump mapping, and displacement mapping. Together, these components form a foundation for understanding how vertex and fragment shaders contribute to realistic rendering in computer graphics.
### Features
- **rasterize_triangle(const Triangle& t)**
Perform triangle rasterization with interpolation of normals, colors, and texture coordinates.
- **get_projection_matrix()**
Fill in the projection matrix implementation as in the previous assignment.
- **phong_fragment_shader()**
Implement Blinn–Phong shading model to compute fragment color.
- **texture_fragment_shader()**
Extend Blinn–Phong shading by incorporating texture color as kd, implementing texture shading.
- **bump_fragment_shader()**
Extend Blinn–Phong shading with bump mapping, modifying surface normals using height map information.
- **displacement_fragment_shader()**
Extend bump mapping with displacement mapping, adjusting both surface normals and vertex positions based on height map.

## HW4: 
- ****
## HW5:
- ****
## HW6:
- ****
