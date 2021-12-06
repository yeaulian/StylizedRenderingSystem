---
layout: default
title: SRS_CameraAlignedTexture
parent: Material Functions
nav_order: 10
---

# SRS_CameraAlignedTexture

This node generates UVs for your object such that any texture mapped using these UVs will always face the camera, however keep its size in relation to the object your material is used on.

In order to use this node, simply connect this node's Output to the UV Input on a Texture Sample Node. You can modify the texture's scale or position by connecting a Vector2 to the corresponding input of this node.

---
