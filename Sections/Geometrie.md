# 3. Géométrie et transformations 3D  
*(Geometry and 3D Transformations)*  

## 📘 Sommaire local / Local Table of Contents  
1. [3.1 Coordonnées et repères / Coordinates and Frames](#31-coordonnées-et-repères--coordinates-and-frames)  
2. [3.2 Transformations géométriques / Geometric Transformations](#32-transformations-géométriques--geometric-transformations)  
3. [3.3 Espaces et caméras / Spaces and Cameras](#33-espaces-et-caméras--spaces-and-cameras)  
4. [3.4 Intersections et géométrie analytique / Intersections and Analytic Geometry](#34-intersections-et-géométrie-analytique--intersections-and-analytic-geometry)  

---

## 3.1 Coordonnées et repères / Coordinates and Frames  

3.1.1 – Qu’est-ce qu’un repère cartésien ?  
3.1.2 – Quelle est la différence entre coordonnées locales et globales ?  
3.1.3 – Qu’est-ce qu’un repère objet ?  
3.1.4 – Qu’est-ce qu’un repère monde ?  
3.1.5 – Qu’est-ce qu’un repère caméra (view space) ?  
3.1.6 – Qu’est-ce qu’un espace d’écran (screen space) ?  
3.1.7 – Quelle est la différence entre coordonnées homogènes et cartésiennes ?  
3.1.8 – Pourquoi utiliser des coordonnées homogènes en 3D ?  
3.1.9 – Que représente le quatrième composant w ?  
3.1.10 – Quelle est la différence entre coordonnées normalisées (NDC) et écran (viewport) ?  
3.1.11 – Qu’est-ce qu’un repère orthonormé ?  
3.1.12 – Qu’est-ce qu’un changement de base ?  
3.1.13 – Quelle est la différence entre rotation active et passive ?  
3.1.14 – Comment convertir un vecteur d’un repère à un autre ?  
3.1.15 – Quelle est la différence entre orientation et direction ?  
3.1.16 – Qu’est-ce qu’un système de coordonnées main droite vs main gauche ?  
3.1.17 – Quelle convention utilise OpenGL ?  
3.1.18 – Quelle convention utilise DirectX ?  
3.1.19 – Qu’est-ce qu’un repère affine ?  
3.1.20 – Quelle est la différence entre translation et changement d’origine ?  

---

## 3.2 Transformations géométriques / Geometric Transformations  

3.2.1 – Qu’est-ce qu’une transformation géométrique ?  
3.2.2 – Quelle est la différence entre rotation et translation ?  
3.2.3 – Qu’est-ce qu’une mise à l’échelle non uniforme ?  
3.2.4 – Qu’est-ce qu’un cisaillement (shear) ?  
3.2.5 – Qu’est-ce qu’une réflexion ?  
3.2.6 – Quelle est la différence entre rotation dans le plan et en espace ?  
3.2.7 – Qu’est-ce qu’un axe de rotation ?  
3.2.8 – Quelle est la différence entre angle et orientation ?  
3.2.9 – Comment représenter une rotation avec une matrice 3×3 ?  
3.2.10 – Qu’est-ce qu’un quaternion ?  
3.2.11 – Quelle est la différence entre quaternion et matrice de rotation ?  
3.2.12 – Pourquoi les quaternions évitent-ils le gimbal lock ?  
3.2.13 – Comment convertir quaternion ↔ matrice ?  
3.2.14 – Qu’est-ce qu’une interpolation sphérique (slerp) ?  
3.2.15 – Qu’est-ce qu’une transformation affine composée ?  
3.2.16 – Pourquoi l’ordre des transformations est-il important ?  
3.2.17 – Qu’est-ce qu’une matrice de transformation inverse ?  
3.2.18 – Comment calculer la normale transformée d’un vertex ?  
3.2.19 – Pourquoi utiliser la matrice inverse transposée pour transformer une normale ?  
3.2.20 – Qu’est-ce qu’une transformation rigide ?  

---

## 3.3 Espaces et caméras / Spaces and Cameras  

3.3.1 – Qu’est-ce qu’une caméra en 3D ?  
3.3.2 – Quelle est la différence entre position et orientation d’une caméra ?  
3.3.3 – Qu’est-ce qu’un vecteur avant (forward), haut (up) et droite (right) ?  
3.3.4 – Qu’est-ce qu’une matrice de vue (view matrix) ?  
3.3.5 – Comment construire une matrice de vue à partir de la position et orientation ?  
3.3.6 – Qu’est-ce qu’une projection orthographique ?  
3.3.7 – Qu’est-ce qu’une projection perspective ?  
3.3.8 – Quelle est la différence entre FOV horizontal et vertical ?  
3.3.9 – Qu’est-ce que near plane et far plane ?  
3.3.10 – Pourquoi un z-buffer utilise une profondeur normalisée ?  
3.3.11 – Quelle est la formule de profondeur après projection perspective ?  
3.3.12 – Qu’est-ce qu’une matrice de projection inverse ?  
3.3.13 – Qu’est-ce que la déprojection ?  
3.3.14 – Comment passer de coordonnées écran à monde ?  
3.3.15 – Quelle est la différence entre clip space et NDC ?  
3.3.16 – Pourquoi inverser l’axe Y selon les API graphiques ?  
3.3.17 – Qu’est-ce qu’une vue miroir ?  
3.3.18 – Qu’est-ce qu’un frustum de caméra ?  
3.3.19 – Qu’est-ce que la culling frustum ?  
3.3.20 – Comment vérifier si un point est visible dans le frustum ?  

---

## 3.4 Intersections et géométrie analytique / Intersections and Analytic Geometry  

3.4.1 – Qu’est-ce qu’une équation paramétrique de droite ?  
3.4.2 – Comment définir un plan à partir de trois points ?  
3.4.3 – Qu’est-ce qu’un vecteur normal de plan ?  
3.4.4 – Qu’est-ce que l’équation cartésienne d’un plan ?  
3.4.5 – Comment trouver l’intersection entre une droite et un plan ?  
3.4.6 – Comment trouver l’intersection entre deux droites ?  
3.4.7 – Qu’est-ce qu’un segment ?  
3.4.8 – Quelle est la différence entre segment et droite infinie ?  
3.4.9 – Qu’est-ce qu’un rayon (ray) ?  
3.4.10 – Comment tester une intersection rayon-sphère ?  
3.4.11 – Comment tester une intersection rayon-triangle ?  
3.4.12 – Qu’est-ce qu’une boîte englobante (AABB) ?  
3.4.13 – Quelle est la différence entre AABB et OBB ?  
3.4.14 – Qu’est-ce qu’un test de collision séparée (SAT) ?  
3.4.15 – Qu’est-ce que la distance minimale entre deux segments ?  
3.4.16 – Comment calculer le barycentre d’un triangle ?  
3.4.17 – Comment interpoler une normale à partir des barycentriques ?  
3.4.18 – Qu’est-ce qu’une surface paramétrique ?  
3.4.19 – Quelle est la différence entre surface implicite et paramétrique ?  
3.4.20 – Qu’est-ce qu’une courbe de Bézier et à quoi sert-elle ?  
