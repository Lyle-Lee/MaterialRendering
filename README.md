# Material Rendering implemented with OpenGL
This is a simple CG project for practicing, including 6 sample materials rendered under D65 illumination.

### White Chalk

The material should have a rough feeling, so "NormalMap" texture and bump mapping effect is used. The shape is adjusted to be finer and the color is set similar to real white chalk.

As the reflection of chalk should not include specular reflection, the fragment color is computed as:

<a href="https://www.codecogs.com/eqnedit.php?latex={\color{Emerald}&space;R_{rgb}&space;=&space;C_{rgb}\left(&space;I&space;\cdot&space;k_d&space;\cdot&space;\max\left(&space;\frac{N&space;\cdot&space;-L}{|N||L|}&space;,&space;0\right)&space;&plus;&space;a&space;\right)&space;\quad\quad\quad&space;(1)}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?{\color{Emerald}&space;R_{rgb}&space;=&space;C_{rgb}\left(&space;I&space;\cdot&space;k_d&space;\cdot&space;\max\left(&space;\frac{N&space;\cdot&space;-L}{|N||L|}&space;,&space;0\right)&space;&plus;&space;a&space;\right)&space;\quad\quad\quad&space;(1)}" title="{\color{Emerald} R_{rgb} = C_{rgb}\left( I \cdot k_d \cdot \max\left( \frac{N \cdot -L}{|N||L|} , 0\right) + a \right) \quad\quad\quad (1)}" /></a>

where <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;C_{rgb}}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;C_{rgb}}" title="{\color{Emerald} C_{rgb}}" /></a> is object color, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;I}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;I}" title="{\color{Emerald} I}" /></a> is light color, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;k_d}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;k_d}" title="{\color{Emerald} k_d}" /></a> is diffuse reflectivity, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;N}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;N}" title="{\color{Emerald} N}" /></a> is the normal vector at a point, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;L}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;L}" title="{\color{Emerald} L}" /></a> is vector of light direction and <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;a}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;a}" title="{\color{Emerald} a}" /></a> is ambient light.

<p align="middle"><img src="imgs/whiteChalk1.png" alt="whiteChalk" width=100>&nbsp<img src="imgs/whiteChalk2.png" alt="whiteChalk" width=100>&nbsp<img src="imgs/whiteChalk3.png" alt="whiteChalk" width=100></p>

### Brick

This example used color with RGB of `(50, 209, 146)`. To make the object similar to brick, set the specular reflection color close to turquoise, and apply "BrickNormalMap" texture. The bump mapping effect is strengthened. Let <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;V}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;V}" title="{\color{Emerald} V}" /></a> be the vector of view direction, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;H&space;=&space;\frac{V&space;-&space;L}{2}}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;H&space;=&space;\frac{V&space;-&space;L}{2}}" title="{\color{Emerald} H = \frac{V - L}{2}}" /></a>, according to Phong reflection model, the fragment color is computed as:

<a href="https://www.codecogs.com/eqnedit.php?latex={\color{Emerald}&space;R_{rgb}&space;=&space;C_{rgb}\left(&space;I&space;\cdot&space;k_d&space;\cdot&space;\max\left(&space;\frac{N&space;\cdot&space;-L}{|N||L|}&space;,&space;0\right)&space;&plus;&space;I&space;\cdot&space;k_s&space;\cdot&space;\left(&space;\max\left(&space;\frac{N&space;\cdot&space;H}{|N||H|},&space;0&space;\right)&space;\right)^n&space;&plus;&space;a&space;\right)&space;\quad\quad\quad&space;(2)}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?{\color{Emerald}&space;R_{rgb}&space;=&space;C_{rgb}\left(&space;I&space;\cdot&space;k_d&space;\cdot&space;\max\left(&space;\frac{N&space;\cdot&space;-L}{|N||L|}&space;,&space;0\right)&space;&plus;&space;I&space;\cdot&space;k_s&space;\cdot&space;\left(&space;\max\left(&space;\frac{N&space;\cdot&space;H}{|N||H|},&space;0&space;\right)&space;\right)^n&space;&plus;&space;a&space;\right)&space;\quad\quad\quad&space;(2)}" title="{\color{Emerald} R_{rgb} = C_{rgb}\left( I \cdot k_d \cdot \max\left( \frac{N \cdot -L}{|N||L|} , 0\right) + I \cdot k_s \cdot \left( \max\left( \frac{N \cdot H}{|N||H|}, 0 \right) \right)^n + a \right) \quad\quad\quad (2)}" /></a>

where <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;k_s}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;k_s}" title="{\color{Emerald} k_s}" /></a> is specular reflectivity and <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;n}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;n}" title="{\color{Emerald} n}" /></a> is related to shininess value of the highlight.

<p align="middle"><img src="imgs/brick1.png" alt="brick" width=100>&nbsp<img src="imgs/brick2.png" alt="brick" width=100>&nbsp<img src="imgs/brick3.png" alt="brick" width=100></p>

### Copper Metallic Coin

For copper metalic material, the RGB of copper color is used and the specular reflection color is set proportional to the incident light color. Compute fragment color in the same way as <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;(2)}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;(2)}" title="{\color{Emerald} (2)}" /></a>.

<p align="middle"><img src="imgs/coin1.png" alt="coin" width=100>&nbsp<img src="imgs/coin2.png" alt="coin" width=100>&nbsp<img src="imgs/coin3.png" alt="coin" width=100></p>

### Obsidian

To make the surface close to the unevenness of the rock, "circles" texture is used and the bump mapping effect is strengthened. The object color, specular reflection color and ambient light color is used from [OpenGL/VRML Materials](http://devernay.free.fr/cours/opengl/materials.html). Compute fragment color in the same way as <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;{\color{Emerald}&space;(2)}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;{\color{Emerald}&space;(2)}" title="{\color{Emerald} (2)}" /></a>.

<p align="middle"><img src="imgs/obsidian1.png" alt="obsidian" width=100>&nbsp<img src="imgs/obsidian2.png" alt="obsidian" width=100>&nbsp<img src="imgs/obsidian3.png" alt="obsidian" width=100></p>

### Red Plastic

The specular reflection color is set equal to the incident light color, and ambient light is set to 0.

<p align="middle"><img src="imgs/redPlastic1.png" alt="plastic" width=100>&nbsp<img src="imgs/redPlastic2.png" alt="plastic" width=100>&nbsp<img src="imgs/redPlastic3.png" alt="plastic" width=100></p>

### Pearl

<p align="middle"><img src="imgs/pearl1.png" alt="pearl" width=100>&nbsp<img src="imgs/pearl2.png" alt="pearl" width=100>&nbsp<img src="imgs/pearl3.png" alt="pearl" width=100></p>

