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

This category does not take affect if "Use Specular and Roughness Inputs" in [Conversion](#conversion) is enabled.

## Emissive Color
Using the switch at the top of the  category you can switch between using a static color or using a texture for the material's emissive oclor.

If you are using a static color you can input that color below.
If you are using a texture you can select that texture and set a tint to modify the texture's color and brightness.

When using emissive color, be aware, that when the emissive color is brighter than black (0,0,0) the emissive parts of where the material is applied will no longer be able to receive colored lights and the shadows on the emissive parts will become smaller.

## Opacity Mask
You can specify which parts of the mesh will be hidden by enabling the "Enable Opacity Mask" parameter and selecting a texture in the "Opacity Mask Texture" parameter.
- 0 (black) for hidden parts
- 1 (white) for visible parts

If you are using a gradient instead of a black and white mask, and want to determine the threshold below which the material will turn invisible, head to the general category in the instance's detail panel and under Material Property Overrides, change the Opacity Mask Clip Value to your required value.

## Conversion
---
