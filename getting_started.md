---
layout: default
title: Getting Started
nav_order: 10
---

# Getting Started
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

##  Setting your project up to work with SRS

1. Open up the Epic Games Launcher, click on Unreal Engine and head to your Library.
2. Find 'Stylized Rendering System' in your Vault and click add to project.
3. Select the project you want to add SRS to.
4. Open up your project and open your project settings
5. Under the Engine category in the Rendering Tab, set "Custom Depth-Stencil Pass" to "Enabled with Stencil".

![Image](assets/setting_up_stencil.png)

---

## Adding SRS to your scene

1. Navigate to StylizedRenderingSystem/Blueprints your content browser.
2. Drag the actor "BP_StylizedRenderingSystem" into your scene. This actor will allow you to control where SRS will take affect and how SRS will render your scene. ![Image](assets/adding_srs.png)
3. Select the actors you want SRS to affect and enable "Render CustomDepth Pass" in the details panel
4. If you want SRS to affect your entire scene, disable "Only On Custom Depth" in the details panel of the SRS actor you just dragged into your scene. 

---

## Converting existing materials to work with SRS

1. Open the material editor for a material you want to make compatible with SRS
2. Add the SRS_MaterialAttributes node and connect the outputs to the inputs with the same name on the **Material Outputs** node.
3. Add the SRS_AttributeConverter node and connect the outputs to the inputs with the same name on the **SRS_MaterialAttributes** node.
4. If there were previous connections to the input pins of the **Material Outputs** node, connect those with the respective inputs on the two nodes that were just created.
5. If there is an Emissive Color Texture, connect that to the **SRS_MaterialAttributes** node as well.
6. The final result should look similar to this:

![Image](assets/converting_materials.png)

---
