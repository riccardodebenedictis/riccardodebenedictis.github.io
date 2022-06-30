---
layout: default
title: TEL and Cultural Heritage
---

Technology Enhanced Learning (TEL) is a set of training methodologies, based on particular digital technologies, which emphasize the interactivity of the learning process. The TEL theme has been initially developed within the [Città Educante](http://www.cittaeducante.it) project, aiming at proposing new educational approaches, enriching and innovating methods and tools,
overcoming classical systems and the traditional role of educators. Within this project, in particular, [ExPLoRAA](https://github.com/pstlab/ExPLoRAA) (ExPeriential LeaRning for Active Aging) was initially developed. Starting from a static representation containing an high-level lesson track, initially stored in the database, a lesson is planned and dynamically adapted and personalized for the involved users.

The idea of using the technology related to Artificial Intelligence (AI) comes from the need to create a sufficiently extensive didactic experiences to reproduce a large number of different situations which are, at the same time, characterized by a high variability of stimuli, aimed at increasing the involvement level of users. Automated planning, declined as a form of automated [abductive reasoning](/research/#abductive-reasoning), favors the generation of different lessons that would be too complicated to obtain with a simple pre-compilation of stories.

From a high-level point of view, it is possible to distinguish between two kinds of involved users: the **students**, i.e. a group of people, potentially, of any age, interested in using the learning services offered by the ExPLoRAA, and the **teachers**, i.e. users with special privileges who have the opportunity to observe students, monitoring the progress of the actions and the learning environment. The above users interact with the ExPLoRAA system which is composed of three functional blocks, intended as architectural subsystems, implementing the corresponding high-level functionalities:
 - the *user modeling*, whose goal is to create and maintain a user model and provide guidance for improving the learning process;
 - the *lesson modeling*, whose role is to combine the information from the previous subsystem and to create the customized lesson as well as to control its evolution;
 - the lesson *presentation*, whose purpose is to effectively represent the lesson.

Among the first works, in which I participated, about Technology Enhanced Learning you can find \[[4](#r4)\]. One of the main challenges of Technology Enhanced Learning tools, however, concerns the creation of content. This challenge, in particular, concerns the creation of causal rules that allow the reasoner to generate sequences of actions that are effective in teaching students the desired contents. It is therefore, in a certain sense, part of an [induction problem](/research/#inductive-reasoning). Initial solutions to this problem are described in the \[[1](#r1), [2](#r2), [3](#r3)\] papers.

## References

[<a name="r1"></a>1] De Benedictis, R.; De Medio, C.; Palombini, A.; Cortellessa, G.; Limongelli, C.; Cesta, A. Fostering the Creation of Personalized Content for Cultural Visits. Appl. Sci. 2021, 11, 7401. https://doi.org/10.3390/app11167401 [pdf](https://www.mdpi.com/2076-3417/11/16/7401/pdf?version=1628748639).

[<a name="r2"></a>2] Amedeo Cesta, Gabriella Cortellessa, Riccardo De Benedictis, Carlo De Medio, Carla Limongelli, Filippo Sciarrone, Giulia Tassarotti, and Augusto Palombini. 2020. Personalizing Technology-Enhanced Learning for Cultural Visits. In Adjunct Publication of the 28th ACM Conference on User Modeling, Adaptation and Personalization (UMAP '20 Adjunct). Association for Computing Machinery, New York, NY, USA, 333–339. https://doi.org/10.1145/3386392.3399278.

[<a name="r3"></a>3] Cesta, A., Cortellessa, G., De Benedictis, R., De Medio, C., Fracasso, F., Limongelli, C. (2019). Toward Automated Courseware Production for the ExPLoRAA Learning Environment. In: Alviano, M., Greco, G., Scarcello, F. (eds) AI*IA 2019 – Advances in Artificial Intelligence. AI*IA 2019. Lecture Notes in Computer Science(), vol 11946. Springer, Cham. https://doi.org/10.1007/978-3-030-35166-3_37.

[<a name="r4"></a>4] De Benedictis, R., Cortellessa, G., Fracasso, F., & Cesta, A. (2019). Technology-enhanced learning to support active ageing. Form@re - Open Journal Per La Formazione in Rete, 19(1), 301-311. https://doi.org/10.13128/formare-24995. ([pdf](https://doi.org/10.13128/formare-24995)).