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

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Register Light Color

## Unregister Light Color

---
