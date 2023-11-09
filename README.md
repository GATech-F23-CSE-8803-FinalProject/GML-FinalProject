# GLM-FinalProject

* [**Resources spreadsheet**](https://docs.google.com/spreadsheets/d/15Bmkx0n4Z9lcgvBW5DICMc_5DQGoknjJyintSgLNBVY/edit?usp=sharing)
* Discord: https://discord.gg/yknjdBGS


## Rough plan

* Start with running DeepFRI pretrained local model as baseline.
  - Earliest, most popular protein function prediction using GNN methods.
  - Uses GCN model (graph convolutional network)
  - [Util: "Pipeline for searching and aligning contact maps for proteins, then running DeepFri's GCN"](https://github.com/bioinf-mcb/Metagenomic-DeepFRI)
* Lots of directions we can branch out to after this for model improvements.
  Most use LLMs, which is a possibility, but probably best to take simpler approaches, at least at first.
  - [Struct2GO](https://github.com/lyjps/Struct2GO) is a very recent (Oct 2023) model: "Protein function prediction based on **graph pooling algorithm** and **AlphaFold2 structure information**"
