# Material Rendering implemented with OpenGL
This is a simple CG project for learning, including 6 sample materials.

### 1. White Chalk

The material should have a rough feeling, so "NormalMap" texture and bump mapping effect is used. The shape is adjusted to be finer and the color is set similar to real white chalk.

As the reflection of chalk should not include specular reflection, the fragment color is computed as:

R<sub>rgb</sub> = C<sub>rgb</sub>()
$$
R_{rgb} = C_{rgb}\left( I \cdot k_d \cdot \max\left( \frac{N \cdot -L}{|N||L|} , 0\right) + a \right)
$$
<a href="https://www.codecogs.com/eqnedit.php?latex=R_{rgb}&space;=&space;C_{rgb}\left(&space;I&space;\cdot&space;k_d&space;\cdot&space;\max\left(&space;\frac{N&space;\cdot&space;-L}{|N||L|}&space;,&space;0\right)&space;&plus;&space;a&space;\right)" target="_blank"><img src="https://latex.codecogs.com/svg.latex?R_{rgb}&space;=&space;C_{rgb}\left(&space;I&space;\cdot&space;k_d&space;\cdot&space;\max\left(&space;\frac{N&space;\cdot&space;-L}{|N||L|}&space;,&space;0\right)&space;&plus;&space;a&space;\right)" title="R_{rgb} = C_{rgb}\left( I \cdot k_d \cdot \max\left( \frac{N \cdot -L}{|N||L|} , 0\right) + a \right)" /></a>

Where C<sub>rgb</sub> is object color, <a href="https://www.codecogs.com/eqnedit.php?latex=I" target="_blank"><img src="https://latex.codecogs.com/svg.latex?I" title="I" /></a>is light color, 

