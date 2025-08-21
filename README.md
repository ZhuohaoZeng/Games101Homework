# Modern Computer Graphics
Class Link: https://sites.cs.ucsb.edu/~lingqi/teaching/games101.html  
Built core modules: transformation matrices, triangle rasterizer with Z-buffering, Blinn–Phong shading with texture/bump/displacement mapping, Bézier curve rendering, ray–triangle intersection, and BVH traversal.  
Gained extensive experience translating math (linear algebra, numerical methods) into performant C++ code, with debugging, modular design, and optimization for rendering tasks.

## HW1: Rotation and Projection
I implemented the fundamental transformations needed to render a triangle on the screen. Specifically, I constructed a rotation matrix and a perspective projection matrix, which transform 3D points into screen space for rasterization. Using the provided draw_triangle function, the transformed vertices are connected to form a wireframe triangle that can be displayed and rotated around the z-axis. 
### Features
- **get_model_matrix(float rotation_angle):**  
  Construct the model transformation matrix and return it. Only the rotation matrix around the 3D z-axis is implemented, without handling translation or scaling.
  
- **get_projection_matrix(float eye_fov, float aspect_ratio, float zNear, float zFar):**  
  Construct the perspective projection matrix using the given parameters and return it.

## HW2: Triangles and Z-buffering
I implemented the rasterization of filled triangles on the screen. The task focuses on determining whether a pixel lies inside a triangle, computing interpolated depth values, and applying z-buffering to ensure correct visibility. Through this, triangles can be correctly rasterized and displayed with proper depth handling.
### Features
- **rasterize_triangle(const Triangle& t)**  
Perform triangle rasterization. For each pixel inside the triangle’s bounding box, check if its center lies within the triangle. If inside, compute the interpolated depth value and compare it with the depth buffer. Update the pixel color and depth buffer if it is closer to the camera.

- **insideTriangle()**  
Test whether a given point lies inside the triangle. This function can be customized and updated based on your own implementation style.
- **z-buffer**  
Store interpolated depth values and perform depth testing to ensure correct rendering order. Pixels with smaller depth values overwrite those with larger ones.

## HW3: Pipeline and Shading
I extended the rasterization pipeline by integrating modern rendering techniques such as shading and texture mapping. Building on the previous assignment, where triangles were rasterized with basic interpolation, I implemented several fragment shaders to simulate more realistic visual effects. Specifically, I filled in the projection matrix, applied the Blinn–Phong lighting model, and extended it with texture shading, bump mapping, and displacement mapping. Together, these components form a foundation for understanding how vertex and fragment shaders contribute to realistic rendering in computer graphics.
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

## HW4: Bezier Curve
I implemented Bézier curve drawing using the De Casteljau algorithm. The task involves computing curve points through recursive subdivision of control points and rendering the resulting curve with OpenCV.
### Features
- **bezier**  
Implements Bézier curve drawing by iterating over parameter t in the range [0,1]. For each value of t, it calls recursive_bezier to compute the corresponding point on the curve, and then stores the result into an OpenCV Mat object.
- **recursive_bezier**  
Computes a point on the Bézier curve given a sequence of control points and parameter t. This is done using the De Casteljau algorithm: repeatedly subdividing line segments between adjacent control points until only one point remains, which represents the curve point at t.
## HW5: Ray–Triangle Intersection
I implemented basic ray tracing to render scenes with spheres and triangles. The task focuses on generating rays for each pixel, computing ray–triangle intersections, and applying shading at the intersection points.
### Features
- **Render()**  
For each pixel in the image, generate the corresponding ray and call castRay to compute the color. The resulting color is then stored in the framebuffer to produce the final image.
- **rayTriangleIntersect()**  
Compute the intersection between a ray and a triangle defined by vertices v0, v1, v2. The ray is specified by its origin orig and normalized direction dir. The intersection test is performed using the Möller–Trumbore algorithm, returning parameters tnear, u, v if an intersection occurs.
## HW6: Acceleration Architecture
I implemented bounding volume hierarchy (BVH) to accelerate ray–object intersection tests. The task involves checking whether a ray intersects with bounding boxes and using the BVH tree structure to reduce the number of intersection computations.
### Features
- **IntersectP(const Ray& ray, const Vector3f& invDir, const std::array<int, 3>& dirIsNeg)**  
Determine whether a ray intersects with a bounding box. This function implements the bounding-box intersection test used during BVH traversal.
- **getIntersection(BVHBuildNode node, const Ray& ray)**  
Traverse the BVH structure to accelerate ray–object intersection queries. At each node, bounding-box tests are applied using Bounds3::IntersectP, and only intersected branches are recursively explored.
