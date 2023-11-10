# Midterm video script

## Intro

Our group is investigating the task of protein function prediction.

We hope to gain a deep understanding of the state of the art in the field, and to explore potential improvements to model architecture.
These could be improvements to prediction accuracy, training efficiency, or reducing model complexity without impacting performance.

## Project background

Our original project was to predict patient-level immune response to novel antigens.
Specifically, we were interested in the potential to predict whether a novel epitope would bind to a known set of paratopes representing a patient's immune system.

Since we were unable to find patient-level data of this kind, we decided to generalize our task to predicting "antigenic distance" from an epitope to an arbitrary set of paratopes.
However, even this reformulation of the task posed major difficulties.
Most importantly, antigenic distance is not a well-defined measure, and the availability of ground-truth data is sparse.

We finally settled on protein function prediction as it is a related task that is more well-defined, with extensive of prior work, curated datasets, and baseline models.

## Progress so far

After pivoting to the task of protein function prediction, we have made good progress in preparation for investigating potential model improvements.

So far, we have:
* Surveyed the field and aggregated our findings into a comprehensive set of resources, including existing models, papers, datasets, data processing utilities, and competitions
  - We've learned from our survey that:
    * Graph Neural Networks are quickly becoming the predominant choice of model architecture
    * The state of the art is largely being driven by incorporating transformers, LLMs for protein representation learning, and diffusion models (SPROF-GO)
    * However, there is still progress being made by incorporating known GNN methods such as graph pooling (Struct2GO), and exploring effective feature representations for gene ontologies, protein structure, sequence data, and protein knowledge graphs (OntoProtein, DeepProtGO)
* Chosen a baseline model and dataset
* Successfully ran pretrained models and trained models from scratch on multiple workspaces

## Next steps

Next, we plan to
* Port our chosen baseline model from tensorflow to pytorch, to make it easier to explore GNN architecture changes with pytorch-geometric.
  Our baseline is a 2019 model called DeepFRI, and it's implemented using a Graph Convolutional Network.
* After porting to pytorch, we plan to investigate alternative model architectures.
  In class, we've discussed GraphGPS as a strong default model architecture.
  Given the recent successes of incorporating transformers for protein function prediction (Gat-GO), we plan to explore this and perhaps other models in the pytorch-geometric ecosystem.
* Finally, we hope to synthesize our model investigations into concrete insights and improvements.

