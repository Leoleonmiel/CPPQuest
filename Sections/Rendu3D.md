# 5. Pipeline graphique et rendu 3D avancé  
*(Graphics Pipeline and Advanced 3D Rendering)*  

## 📘 Sommaire local / Local Table of Contents  
1. [5.1 Pipeline graphique classique / Traditional Graphics Pipeline](#51-pipeline-graphique-classique--traditional-graphics-pipeline)  
2. [5.2 Shaders et programmation GPU / Shaders and GPU Programming](#52-shaders-et-programmation-gpu--shaders-and-gpu-programming)  
3. [5.3 Éclairage et matériaux / Lighting and Materials](#53-éclairage-et-matériaux--lighting-and-materials)  
4. [5.4 Rendu physiquement plausible (PBR) / Physically Based Rendering](#54-rendu-physiquement-plausible-pbr--physically-based-rendering)  
5. [5.5 Techniques avancées de rendu / Advanced Rendering Techniques](#55-techniques-avancées-de-rendu--advanced-rendering-techniques)  
6. [5.6 Optimisation et gestion des ressources / Optimization and Resource Management](#56-optimisation-et-gestion-des-ressources--optimization-and-resource-management)  

---

## 5.1 Pipeline graphique classique / Traditional Graphics Pipeline  

5.1.1 – Quelles sont les étapes principales du pipeline graphique classique ?  
5.1.2 – Qu’est-ce que le rasterizer ?  
5.1.3 – Qu’est-ce qu’un vertex shader ?  
5.1.4 – Qu’est-ce qu’un fragment shader ?  
5.1.5 – Qu’est-ce que le depth test ?  
5.1.6 – Quelle est la fonction du z-buffer ?  
5.1.7 – Quelle est la différence entre early-Z et late-Z ?  
5.1.8 – Qu’est-ce que le clipping ?  
5.1.9 – Qu’est-ce que le back-face culling ?  
5.1.10 – Pourquoi les triangles sont-ils utilisés pour le rendu 3D ?  
5.1.11 – Quelle est la différence entre pipeline fixe et programmable ?  
5.1.12 – Qu’est-ce que la perspective division ?  
5.1.13 – Qu’est-ce que la viewport transformation ?  
5.1.14 – Comment le pipeline gère-t-il les coordonnées homogènes ?  
5.1.15 – Quelle est la différence entre rendu forward et deferred ?  
5.1.16 – Qu’est-ce que le multi-render target (MRT) ?  
5.1.17 – Qu’est-ce qu’une framebuffer object (FBO) ?  
5.1.18 – Qu’est-ce qu’un render pass ?  
5.1.19 – Qu’est-ce qu’un swap chain ?  
5.1.20 – Quelle est la différence entre VSync et triple buffering ?  

---

## 5.2 Shaders et programmation GPU / Shaders and GPU Programming  

5.2.1 – Qu’est-ce qu’un shader ?  
5.2.2 – Quelles sont les principales étapes programmables du pipeline ?  
5.2.3 – Quelle est la différence entre GLSL, HLSL et SPIR-V ?  
5.2.4 – Qu’est-ce qu’un geometry shader ?  
5.2.5 – Qu’est-ce qu’un tessellation shader ?  
5.2.6 – Qu’est-ce qu’un compute shader ?  
5.2.7 – Quelle est la différence entre vertex shader et compute shader ?  
5.2.8 – Qu’est-ce qu’une uniform ?  
5.2.9 – Qu’est-ce qu’un UBO (Uniform Buffer Object) ?  
5.2.10 – Qu’est-ce qu’un SSBO (Shader Storage Buffer Object) ?  
5.2.11 – Quelle est la différence entre sampler2D et image2D ?  
5.2.12 – Qu’est-ce qu’un pipeline de shader Vulkan ?  
5.2.13 – Qu’est-ce que la compilation offline de shader ?  
5.2.14 – Quelle est la différence entre SPIR-V et DXIL ?  
5.2.15 – Qu’est-ce qu’une liaison de ressources (resource binding) ?  
5.2.16 – Qu’est-ce que la spécialisation de constantes ?  
5.2.17 – Qu’est-ce qu’un push constant ?  
5.2.18 – Quelle est la différence entre pipeline monolithique et modulaire ?  
5.2.19 – Qu’est-ce qu’un shader library ?  
5.2.20 – Pourquoi compiler les shaders par stade plutôt que globalement ?  

---

## 5.3 Éclairage et matériaux / Lighting and Materials  

5.3.1 – Qu’est-ce qu’un modèle d’éclairage ?  
5.3.2 – Quelle est la différence entre éclairage local et global ?  
5.3.3 – Qu’est-ce que le modèle de Phong ?  
5.3.4 – Qu’est-ce que le modèle de Blinn-Phong ?  
5.3.5 – Quelle est la différence entre diffuse et specular ?  
5.3.6 – Qu’est-ce qu’un vecteur de réflexion ?  
5.3.7 – Qu’est-ce que le BRDF ?  
5.3.8 – Quelle est la différence entre BRDF et BSDF ?  
5.3.9 – Qu’est-ce qu’une normale interpolée ?  
5.3.10 – Qu’est-ce que le normal mapping ?  
5.3.11 – Qu’est-ce que le parallax mapping ?  
5.3.12 – Qu’est-ce qu’un cube map ?  
5.3.13 – Qu’est-ce que l’éclairage ambiant ?  
5.3.14 – Quelle est la différence entre point light, directional light et spot light ?  
5.3.15 – Qu’est-ce qu’un shadow map ?  
5.3.16 – Quelle est la différence entre PCF et VSM ?  
5.3.17 – Qu’est-ce que le screen space ambient occlusion (SSAO) ?  
5.3.18 – Qu’est-ce que le bloom ?  
5.3.19 – Qu’est-ce que le tone mapping ?  
5.3.20 – Quelle est la différence entre gamma space et linear space ?  

---

## 5.4 Rendu physiquement plausible (PBR) / Physically Based Rendering  

5.4.1 – Qu’est-ce que le PBR ?  
5.4.2 – Quelles sont les grandes composantes d’un matériau PBR ?  
5.4.3 – Qu’est-ce que le modèle Cook-Torrance ?  
5.4.4 – Qu’est-ce qu’une LUT BRDF ?  
5.4.5 – Quelle est la différence entre roughness et smoothness ?  
5.4.6 – Qu’est-ce qu’une map métallique ?  
5.4.7 – Quelle est la différence entre albedo et base color ?  
5.4.8 – Qu’est-ce que l’IBL (Image-Based Lighting) ?  
5.4.9 – Qu’est-ce qu’une radiance map ?  
5.4.10 – Qu’est-ce qu’une irradiance map ?  
5.4.11 – Qu’est-ce que le fresnel Schlick approximation ?  
5.4.12 – Qu’est-ce que le microfacet model ?  
5.4.13 – Quelle est la différence entre specular workflow et metallic workflow ?  
5.4.14 – Qu’est-ce que la rémission (émission light) ?  
5.4.15 – Qu’est-ce que la conservation de l’énergie dans le PBR ?  
5.4.16 – Quelle est la différence entre éclairage réel et approximé ?  
5.4.17 – Qu’est-ce qu’une spherical harmonic ?  
5.4.18 – Qu’est-ce que la pré-intégration d’IBL ?  
5.4.19 – Qu’est-ce qu’un mipmap et pourquoi important en PBR ?  
5.4.20 – Qu’est-ce qu’un HDR render target ?  

---

## 5.5 Techniques avancées de rendu / Advanced Rendering Techniques  

5.5.1 – Qu’est-ce que le ray tracing ?  
5.5.2 – Quelle est la différence entre path tracing et ray tracing classique ?  
5.5.3 – Qu’est-ce que la global illumination ?  
5.5.4 – Qu’est-ce que le rendu temps réel vs hors-ligne ?  
5.5.5 – Qu’est-ce qu’un acceleration structure (BVH, Kd-Tree) ?  
5.5.6 – Qu’est-ce que le denoising dans le ray tracing ?  
5.5.7 – Qu’est-ce que la refraction et comment la simuler ?  
5.5.8 – Qu’est-ce que le screen space reflections (SSR) ?  
5.5.9 – Quelle est la différence entre rendu volumétrique et surface ?  
5.5.10 – Qu’est-ce qu’une fog volumétrique ?  
5.5.11 – Qu’est-ce que le subsurface scattering ?  
5.5.12 – Qu’est-ce qu’une texture 3D (volumetric texture) ?  
5.5.13 – Qu’est-ce qu’un rendu multi-pass ?  
5.5.14 – Quelle est la différence entre post-process et rendu principal ?  
5.5.15 – Qu’est-ce que le temporal anti-aliasing (TAA) ?  
5.5.16 – Qu’est-ce que le motion blur ?  
5.5.17 – Qu’est-ce que le depth of field ?  
5.5.18 – Qu’est-ce que le bloom HDR ?  
5.5.19 – Qu’est-ce que le render-to-texture ?  
5.5.20 – Quelle est la différence entre deferred lighting et forward plus ?  

---

## 5.6 Optimisation et gestion des ressources / Optimization and Resource Management  

5.6.1 – Qu’est-ce qu’un LOD (Level of Detail) ?  
5.6.2 – Qu’est-ce qu’un culling hiérarchique ?  
5.6.3 – Qu’est-ce que le frustum culling ?  
5.6.4 – Qu’est-ce que l’occlusion culling ?  
5.6.5 – Qu’est-ce qu’un batch de rendu ?  
5.6.6 – Pourquoi regrouper les objets par matériau ?  
5.6.7 – Qu’est-ce que le instancing ?  
5.6.8 – Quelle est la différence entre instancing et merging ?  
5.6.9 – Qu’est-ce qu’un texture atlas ?  
5.6.10 – Qu’est-ce que le streaming de textures ?  
5.6.11 – Quelle est la différence entre meshlet et vertex cache ?  
5.6.12 – Qu’est-ce que le bindless rendering ?  
5.6.13 – Qu’est-ce qu’un GPU memory heap ?  
5.6.14 – Quelle est la différence entre VRAM et RAM ?  
5.6.15 – Pourquoi pré-calculer les shaders et pipelines ?  
5.6.16 – Qu’est-ce qu’un frame graph ?  
5.6.17 – Qu’est-ce qu’une render queue ?  
5.6.18 – Qu’est-ce qu’un GPU timeline ?  
5.6.19 – Qu’est-ce que l’asynchronisme entre CPU et GPU ?  
5.6.20 – Qu’est-ce qu’un profiler de rendu ?  
