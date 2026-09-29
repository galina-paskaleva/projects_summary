# Projects

This is an overview of past and current major projects. 

## 1. SIMULTAN *(2015 - present)*

This project was developed over the course of 11 years by an interdisciplinary team of software and civil engineers at the [TU Wien](https://www.tuwien.at/cee/mbb/bph) under the lead of [Prof. Thomas Bednar](https://tiss.tuwien.ac.at/person/37331.html).

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/assets/images/Simultan_dark.png">
  <source media="(prefers-color-scheme: light)" srcset="/assets/images/Simultan_light.png">
  <img alt="SIMULTAN" src="default-image.png">
</picture>

[Initial publication in 2020](https://nachhaltigwirtschaften.at/resources/sdz_pdf/schriftenreihe-2020-04-simultan.pdf)

[Other publications](https://gitlab.tuwien.ac.at/simultangroup/SIMULTAN-Documentation/-/wikis/Publikationen-%C3%BCber-Simultan)

[Data model repository on GitLab](https://gitlab.tuwien.ac.at/simultangroup/SIMULTAN)

[Data model repository on GitHub](https://github.com/bph-tuwien/SIMULTAN)

[Data model documentation](https://gitlab.tuwien.ac.at/simultangroup/SIMULTAN-Documentation/-/wikis/home)

It was initially funded by the [Austrian Research Promotion Agency (FFG)](https://www.ffg.at/en); later it was further developed in close cooperation with multiple partners from the Architecture, Engineering and Construction (AEC) industry.

SIMULTAN is a [meta-model](https://dl.acm.org/doi/abs/10.5555/3103551) (see [Figure 1.1](#figure_1_1)). It offers a few generic building blocks for the construction of domain-specific models, e.g., for the model of a building, for the simulation model of a physical phenomenon, or for an electrical grid. A SIMULTAN model element behaves similarly to a [clabject](https://link.springer.com/article/10.1007/s10270-006-0017-9), i.e., an amalgamation of a class and an object.

<a name="figure_1_1"></a>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/assets/images/Metamodel_dark.png">
  <source media="(prefers-color-scheme: light)" srcset="/assets/images/Metamodel_light.png">
  <img alt="METAMODEL" src="default-image.png">
</picture>


![]()
*Figure 1.1. The relationship between a model and its metamodel.*

The generic building blocks cover three different aspects of modelling: *structure*, *semantics* and *representation*. For the structure there are components, parameters and calculations; for semantics there are taxonomies with nested taxonomy entries; for the representation there are shapes: vertices, edges, faces and volumes.

[Video 1.1](#video_1_1) outlines the road from the modelling requirements of the Architecture, Engineering and Construction (AEC) industry to the concept behind SIMULTAN. [Video 1.2](#video_1_2) shows the implementation of the concept and demonstrates the interplay of structure, semantics and representation in a digital model from the AEC domain of building physics.

<a name="video_1_1"></a>

[![Simultan Concept Video](assets/images/Simultan_Concept_Video.png)](https://www.youtube.com/embed/UpgmfMcSJz4)
*Video 1.1. The idea behind SIMULTAN.*

<a name="video_1_2"></a>

[![Simultan Implementation Video: coming soon](assets/images/Simultan_Impl_Video.png)](https://www.youtube.com/embed/yo2M2NYsBuI)
*Video 1.2. The implementation of SIMULTAN.*


[Figure 1.2](#figure_1_2) demonstrates the power of SIMULTAN to model deep semantic hierarchies. In essence, the relationships between component and instance provide a syntax that can express multiple semantic levels. (*A video going into more detail will be coming soon.*)

<a name="figure_1_2"></a>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/assets/images/Clabject_dark.png">
  <source media="(prefers-color-scheme: light)" srcset="/assets/images/Claject_light.png">
  <img alt="CLABJECT" src="default-image.png">
</picture>

![]()
*Figure 1.2. The syntactic and semantic dimensions of a clabject.*

This project is open source and its development is ongoing.

## 2. Procedural Shape Contraction *(2021 - 2023)*

![Overview of PSC](assets/images/PSC_Overview.png)

This project demonstrates a method for integrating 2d construction documentation-level architectural details into a 3d conceptual model of a building, which transforms it into a detailed surface model.  The goal is to generate geometry that can be built in the designated material using the appropriate standardized techniques. The workflow consists of the following steps:

1. Each 2d detail is subjected to manual 1d feature extraction to determine those shapes that have an influence on the final 3d model.
2. The sharp features of the 3d model are extracted to obtain the building’s 3d skeleton, consisting of edge curves and corners.
3. We align the feature collection obtained from each detail with the 3d skeleton, in accordance with the architectural design. The goal is to build a 2-manifold with a boundary at each corner of the 3d skeleton.
4. Spanning ruled surfaces between neighbouring corner manifolds completes the final surface model.

This project focuses on the algorithm for constructing the corner manifolds: After the alignment of the feature collections with the 3d skeleton is performed, we calculate a rich descriptor, based on geometric relationship functions, for each feature. In addition, we construct its adjacency graph, containing all other features whose descriptor will change in case this feature is discarded. We then apply simultaneous procedural contraction to all feature collections affecting the same corner of the 3d model ([see Figure 2.1](#figure_2_1)). In each step a preservation score is calculated for all features, based on their descriptors. The feature with the lowest score is discarded and the descriptors and adjacency graphs for all others recalculated. This contraction produces ruled surface segments that are eventually stitched together into a 2-manifold with a boundary. The algorithm evaluation was performed by building a prototype in [MatLab](https://de.mathworks.com/products/matlab.html) and testing it on 170 detail combinations.

![Example PSC](assets/images/PSC_Example.png)
*Figure 2.1. Contracting a collection of 1d features step-by-step.*
<a name="figure_2_1"></a>


[![Procedural Shape Contraction](assets/images/OverviewWorkflowPlay.png)](https://www.youtube.com/embed/xn1lYXiqfSk)


[//]: # (<video width="600" src="https://github.com/user-attachments/assets/885bc938-5e18-46ca-8e63-fdc4c941c47c.mp4"></video>)
*Video 2.1. Prototype tests implemented in MatLab.*


The work was published as a [master thesis at TU Wien](https://repositum.tuwien.at/handle/20.500.12708/158223) and awarded the [Forschungspreis der Österreichischen Bundeskammer der Ziviltechniker:innen für 2023, BFG Informationstechnologie ](https://bund.zt.at/aktuell/veranstaltungen/veranstaltungsarchiv/forschungspreise-zivilingenieurwesen/preistraegerinnen-forschungspreise-2023).
