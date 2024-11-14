---
layout: post
title: Molecule Generation with Fragment Retrieval Augmentation
permalink: /
---

<p style="text-align:center">
    <span style="font-weight:bold">
    Conference on Neural Information Processing Systems (NeurIPS), 2024<br>
    </span>
    Seul Lee<sup>1*</sup>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    Karsten Kreis<sup>2</sup>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    Srimukh Prasad Veccham<sup>2</sup>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    Meng Liu<sup>2</sup><br>
    Danny Reidenbach<sup>2</sup>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    Saee Paliwal<sup>2</sup>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    Arash Vahdat<sup>2†</sup>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    Weili Nie<sup>2†</sup><br>
    <span style="color:gray">
        1 <img height="25px" alt="KAIST" src="/assets/2024-09-17-f-rag/kaist.svg"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        2 <img height="20px" alt="NVIDIA" src="/assets/2024-09-17-f-rag/nvidia.svg"/><br>
        * Work done during an internship at NVIDIA&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        † Equal advising<br>
        seul.lee@kaist.ac.kr<br>
        {kkreis, sveccham, menliu, dreidenbach, saeep, avahdat, wnie}@nvidia.com<br>
    </span>
    <a href="https://arxiv.org" style="color:teal">[Paper]</a>
</p>

<br>

<p align="center"><img width="800px" alt="f-RAG" src="/assets/2024-09-17-f-rag/concept.png"/></p>

### *f*-RAG: Fragment Retrieval-Augmented Generation
***
Many fragment-based molecule generation methods show limited exploration beyond the existing fragments in the database as they only reassemble or slightly modify the given ones. To tackle this problem, we propose a new fragment-based molecule generation framework with retrieval augmentation, namely **Fragment Retrieval-Augmented Generation (*f*-RAG)**. *f*-RAG is based on a pre-trained molecular generative model ([<span style="color:teal">SAFE-GPT</span>](https://arxiv.org/abs/2310.10773)) that proposes additional fragments from input fragments to complete and generate a new molecule. Given a fragment vocabulary, *f*-RAG retrieves two types of fragments: (1) **hard fragments**, which serve as building blocks that will be explicitly included in the newly generated molecule, and (2) **soft fragments**, which serve as reference to guide the generation of new fragments through a trainable **fragment injection module**. To extrapolate beyond the existing fragments, *f*-RAG updates the fragment vocabulary with generated fragments via an iterative refinement process which is further enhanced with post-hoc genetic fragment modification. *f*-RAG can achieve an improved exploration-exploitation trade-off by maintaining a pool of fragments and expanding it with novel and high-quality fragments through a strong generative prior.

<br>

### Fragment-based Drug Discovery with *f*-RAG
***
On the [<span style="color:teal">PMO benchmark</span>](https://arxiv.org/abs/2206.12411), *f*-RAG outperforms the previous methods in terms of the sum of the AUC top-10 values and achieves the highest AUC top-10 values in 12 out of 23 tasks. Furthermore, even though the essential considerations in drug discovery (e.g., diversity, novelty, and synthesizability) often conflict with each other, *f*-RAG exhibits the best balance across them, demonstrating its applicability as a promising tool for drug discovery.

<p align="center"><img width="700px" src="/assets/2024-09-17-f-rag/table.png"/></p>
<p align="center"><img width="100%" src="/assets/2024-09-17-f-rag/tradeoff.png"/></p>

<br>

### Evolution of Generated Molecules over Iterations
***
*f*-RAG dynamically updates the fragment vocabulary with newly generated fragments. The fragment vocabulary and therefore the generated molecules are iteratively refined throughout generation.

<p align="center">
    <img width="300px" src="/assets/2024-09-17-f-rag/frag.gif"/>
    <img width="300px" src="/assets/2024-09-17-f-rag/frag.png"/>
    <br>
    <img width="300px" src="/assets/2024-09-17-f-rag/mol.gif"/>
    <img width="300px" src="/assets/2024-09-17-f-rag/mol.png"/>
</p>

<br>

### Exploration with Dynamic Vocabulary Update
***
*f*-RAG effectively improves the exploration-exploitation trade-off in drug discovery by utilizing existing fragments while dynamically updating the fragment vocabulary with newly proposed fragments. *f*-RAG can discover molecules that have better target properties than the top molecule in the training set with the dynamic update.

<p align="center"><img width="250px" src="/assets/2024-09-17-f-rag/kde.png"/></p>

### Citation
***
```
@article{lee2024frag,
    title   = {Molecule Generation with Fragment Retrieval Augmentation},
    author  = {Seul Lee and Karsten Kreis and Srimukh Prasad Veccham and Meng Liu and
               Danny Reidenbach and Saee Paliwal and Arash Vahdat and Weili Nie},
    journal = {arXiv},
    year    = {2024}
}
```
