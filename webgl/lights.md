---
title: Lights
description: 
published: true
date: 2020-11-06T01:24:34.528Z
tags: webgl, web-technologies
editor: markdown
---

# Lights


### Positional vs Directional
Light sources can be positional or directional. Directional lighting is simpler and less computationally expensive than positional lighting.
* **Positional** - It's position will determine how a scene is lit. A lamp inside a room is a positional light source. Objects far away will receive little light and may be obscured. This is modeled by a point in space.
* **Directional** - Will illuminate all objects in a scene, regardless of distance from the source. The sun is an example of a directional light source. A directional light is modeled with a normalized vector that indicates its direction. 

### Normals
**Normals** are [vectors](/mathematics/linear-algebra/vectors-and-spaces) that are perpendicular to the surface we want to illuminate.They represent the orientation of the surface and are therefore critical to modeling the interaction between a light source and the object. 

### Material
**Materials** control how an object appears on the screen. It can be modeled by several params, including its color and texture. 

### Parallelism and the Difference Between Attributes and Uniforms
When a draw call is invoked (*drawArrays* or *drawElements*), the GPU will launch several copies of the vertex shader in parallel. Each copy receives a different set of attributes  but the same uniforms. 

## Shading Methods and Light-Reflection Models
### Shading
**Shading** is the interpolation that is performed to obtain final color for fragments in a scene. Shading models  determine where the final color is calculated ( fragment vs vertex shader). 
The **Goraud** interpolation calculates the final color in the *vertex* shader, using vertex normals to perform the calculation. Leverages the built-in rendering pipeline's interpolation. Much faster since the performed calculations are computed per vertex.

The **Phong** interpolation calculates the final color in the *fragment* shader, using vertex normals to perform the calculation. Slower but much more accurate / realistic interpolation.  

![shading_interpolation_methods.png](/shading_interpolation_methods.png)


### Lighting
**Lighting** algorithms using physical principles of light reflection, lighting models are also referred to as reflection models. 
#### Lambertian Reflection Model
**Lambertian reflections** are commonly used as a model for *diffuse reflections* (kinds of reflections where an incident light ray is scattered at many angles) ![reflections.png](/reflections.png)

It is usually calculated as the dot product between the surface normal (vertex or fragment normal, depending on the interpolation method used) and the negative of the light-direction vector. Then, the number is multiplied by the material and light source colors.

> **Light-Direction Vector** 
> A vector that starts on the surface and ends on the light source position, mapping the light's position to the surface of the geometry.

![reflections_2.png](/reflections_2.png)

Where 
$$F=C_lC_m(-L\bullet N)$$
 * F - final diffuse color
 * C~l~ - light diffuse color
 * C~m~ - material diffuse color
 
The final diffuse color would be derived with..

$$-L\bullet N= | -L||N|\cos \varnothing$$ 

If L and N are normalized, then:

$$
-L\bullet N= \cos \varnothing
\\
F = C_lC_m\cos \varnothing 
$$

#### Phong Reflection Model
Describes the way a surface reflects light as the sum of three types of reflection.
1. Ambient - amount of light present everywhere in a scene, independent from any light source.
2. Diffuse ( modeled by Lambertian reflectance)
3. Specular - Mirrorlike reflection. Direction of the incoming light and direction of reflected light makes the same anglewith respect to the surface normal.

![specular_reflection.png](/specular_reflection.png)

Where
$$
F_s = C_lC_m(R\bullet E)^n
$$

$
\textbf{F}_{\textbf{s}}   
$ is final specular color. 
$
\textit{C}_{\textbf{l}}   
$ is the light specular color, 
$
\textit{C}_{\textbf{m}}   
$ is the material specular color
$
\textit{n}    
$ is the shininess factor.

The final specular color would be derived with..

$$R\bullet E= | R||E|\cos \varnothing$$ 

If R and E are normalized, then:

$$
R\bullet E= \cos \varnothing
\\
F = C_lC_m\cos^n \varnothing 
$$

