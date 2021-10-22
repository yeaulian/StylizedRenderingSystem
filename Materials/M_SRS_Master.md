---
layout: default
title: M_SRS_Master 
parent: Materials
nav_order: 10
---

# M_SRS_Master
{: .no_toc }
This is the default master material for most non-translucent materials in your project that should be compatible with SRS. All materials that do not have any additional requirements should be instances of this material.

This master material can either directly control the materials rimlight and highlight size or convert standard roughness and specular textures to be used as a simple size control for both rimlights and highlights, if "Use Specular and Roughness Inputs" is enabled. In this case the rimlight and the highlight size will be equal.

As SRS is using a mainly post-process based approach to cel-shading, materials using this master material will only appear cel-shaded if they are in a scene with an enabled [SRS actor](../Blueprints/BP_StylizedRenderingSystem.md).

Below, it will be explained what the parameters in each category of an instance of this material do.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

## Base Color
Using the switch at the top of the  category you can switch between using a static color or using a texture for the material's base color.

If you are using a static color you can input that color below.
If you are using a texture you can select that texture and set a tint to modify the texture's color and brightness.

## Metallic
In the metallic category you can switch if the material is metallic or not by adjusting the "Metallic" parameter. Alternatively you can set a texture if "Use Metallic Texture" is enabled.

- 0 for not metallic
- 1 for metallic

The "Metallic Color Modulation Strength" parameter will control how strong certain parts of the mesh get darkened to give a more metallic appearence. This only takes effect if the corresponding part of the material is metallic.

## Highlight / Rimlight
Here you can adjust the scale of the highlight and rimlight in proportion to the maximum highlight and rimlight sizes defined in the [SRS actor](../Blueprints/BP_StylizedRenderingSystem.md) in the scene. The scale is limited to 8 steps ranging from no rimlight/highlight at 0 to the specified maximum size at 1.

Instead of using the sliders you may also set texture for each of the size scales if the corresponding switch is enabled.

This category does will not appear if "Use Specular and Roughness Inputs" in [Conversion](#conversion) is enabled.

## Emissive Color
Using the switch at the top of the  category you can switch between using a static color or using a texture for the material's emissive oclor.

If you are using a static color you can input that color below.
If you are using a texture you can select that texture and set a tint to modify the texture's color and brightness.

When using emissive color, be aware, that when the emissive color is brighter than black (0,0,0) the emissive parts of where the material is applied will no longer be able to receive colored lights and the shadows on the emissive parts will become smaller.

## Normals
Select a texture to use as a normal map in the "Normal Texture"-Parameter and control its strength with the "Normal Strength"-Parameter.
Using either the default "FlatNormal"-Texture or setting the strength to 0 will disable normal maps from taking effect.

## Opacity Mask
You can specify which parts of the mesh will be hidden by enabling the "Enable Opacity Mask" parameter and selecting a texture in the "Opacity Mask Texture" parameter.
- 0 (black) for hidden parts
- 1 (white) for visible parts

If you are using a gradient instead of a black and white mask, and want to determine the threshold below which the material will turn invisible, head to the general category in the instance's detail panel and under Material Property Overrides, change the Opacity Mask Clip Value to your required value.

## Pattern
In this category you can select a texture that will define what pattern gets applied to the shadows, highlights and rimlights of the material. To use the default patterns shipped with SRS, use the textures with the prefix "T_SRS_P_". This texture will be mapped onto the object such that the texture always faces to the camera (see SRS_CameraAlignedTexture).

Additionally, you can specify a scale and a rotation for the pattern texture.

## Displacement
Here you can specify the displacement map and the strength of the displacement. Use strength 0 or a black texture to disable displacement.
You can adjust the resolution of the displacement by adjusting the "Tessellation Multiplier"-parameter.

## Texture Mapping
This category allows you to control the mapping of all textures except the pattern texture.

Under the Scale / Offset Vector, you can specify the Scale on the horizontal and vertical axis of the texture in the first two channels, and the offset along the same axis in the last two channels. Under Texture Rotation Angle you can specify how the texture gets rotated in degrees.

## Conversion
If you have a set of conventional textures for your material, you may convert those roughness and specular textures to replace the rimlight and highlight size textures.

To do this, enable the parameter "Use Specular and Roughness Inputs" and select your textures in the new parameters below. Enabling this will disable the [Highlight / Rimlight](#highlight--rimlight) category.
