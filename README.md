# GLM-FinalProject

- [**Resources spreadsheet**](https://docs.google.com/spreadsheets/d/15Bmkx0n4Z9lcgvBW5DICMc_5DQGoknjJyintSgLNBVY/edit?usp=sharing)
- Discord: https://discord.gg/yknjdBGS

## Rough plan

- Start with running DeepFRI pretrained local model as baseline.
  - Earliest, most popular protein function prediction using GNN methods.
  - Uses GCN model (graph convolutional network)
  - [Util: "Pipeline for searching and aligning contact maps for proteins, then running DeepFri's GCN"](https://github.com/bioinf-mcb/Metagenomic-DeepFRI)
  - Maybe a "simple" contribution could be a PyTorch implementation of this model?
- Lots of directions we can branch out to after this for model improvements.
  Most use LLMs, which is a possibility, but probably best to take simpler approaches, at least at first.
  - [Struct2GO](https://github.com/lyjps/Struct2GO) is a very recent (Oct 2023) model: "Protein function prediction based on **graph pooling algorithm** and **AlphaFold2 structure information**"

### Karl notes for running DeepFRI

I'm on a Mac M1 machine.
Fork with changes: https://github.com/khiner/DeepFRI

- Unpin all dependency versions in `setup.py` to use lastest + python 3.10.
- Download pretrained models for CPU run (for now - will get tensorflow-metal working later):
```shell
$ cd DeepFRI
$ wget https://users.flatironinstitute.org/~renfrew/DeepFRI_datanewest_trained_models.tar.gz
$ tar xvzf newest_trained_models.tar.gz -C .
```
- Predict
```shell
$ python predict.py --cmap ./examples/pdb_cmaps/1S3P-A.npz -ont mf --verbose
### Computing predictions on a single protein...
Protein GO-term/EC-number Score GO-term/EC-number name
query_prot GO:0005509 0.99999 calcium ion binding
### Saving predictions to *.json file...
```
- I've added a [prediction data explorer notebook](https://github.com/khiner/DeepFRI/blob/master/predict_explore.ipynb) to my fork.
- Train
  * _Notes:_ Tried to run train script, but it failed due to zero train/validation set size. This turned out to be because the TFRecords files were missing. I modified the `data_collection.sh` script in my fork.
  However, this led to other issues that I'm still resolving, since I'm using a newer `Biopython` version:
    ```ImportError: Bio.Alphabet has been removed from Biopython. In many cases, the alphabet can simply be ignored and removed from scripts. In a few cases, you may need to specify the ``molecule_type`` as an annotation on a SeqRecord for your script to work correctly. Please see https://biopython.org/wiki/Alphabet for more information.```
  * Run:
```shell
$ cd preprocessing && ./create_tfrecords.sh
$ python train_DeepFRI.py -h
```
