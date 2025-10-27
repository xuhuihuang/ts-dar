# TS-DAR: Transition State identification via Dispersion and vAriational principle Regularized neural networks

### Abstract

Identifying transitional states is crucial for understanding protein conformational changes that underlie numerous biological processes. Markov state models (MSMs), built from Molecular Dynamics (MD) simulations, capture these dynamics through transitions among metastable conformational states, and have demonstrated success in studying protein conformational changes. However, MSMs face challenges in identifying transition states, as they partition MD conformations into discrete metastable states (or free energy minima), lacking description of transition states located at the free energy barriers. Here, we introduce Transition State identification via Dispersion and vAriational principle Regularized neural networks (TS-DAR), a deep learning framework inspired by out-of-distribution (OOD) detection in trustworthy artificial intelligence (AI). TS-DAR offers an end-to-end pipeline that can simultaneously detect all transition states between multiple free minima from MD simulations using the regularized hyperspherical embeddings in latent space. The key insight of TS-DAR lies in treating transition state structures as OOD data, recognizing that they are sparsely populated and exhibit a distributional shift from metastable states. We demonstrate the power of TS-DAR by applying it to a 2D potential, alanine dipeptide, and the translocation of a DNA motor protein on DNA, where it outperforms previous methods in identifying transition states.

### Illustration

![figure](./docs/figs/fig2.png)

## System requires

The software package can be installed and runned on Linux, Windows, and MacOS (x86_64)

Dependency of Python and Python packages: 

(versions that has been previously tested on are also listed below, other versions should work the same)

```bash
python == 3.9
numpy == 1.26.1
scipy == 1.11.4
torch == 1.13.1
tqdm == 4.66.1
```
The required python packages with the latest versions will be automatically installed if these python packages are not already present in your local Python environment.

## Installation from sources

The source code can be installed with a local clone:

The most time-consuming step is the installation of PyTorch (especially cuda version) and the whole installation procedure takes around 5 mins to complete at a local desktop.

```bash
git clone https://github.com/xuhuihuang/ts-dar.git
```

```bash
python -m pip install ./ts-dar
```

## Quick start

### Note

Our python package name is currently tsdar.

### Start with jupyter notebook

Check these two files for the demo:

```
./ts-dar/example/muller-example.ipynb
```

```
./ts-dar/example/quadruple-well-example.ipynb
```

### Start with python script (Linux)

The whole training procedure of the following demo on i9-10900k cpu takes around 30mins to complete at a local desktop.

```sh
python ./ts-dar/scripts/train_tsdar.py \
    --seed 1 \
    --device 'cpu' \
    --lag_time 10 \
    --encoder_sizes 2 20 20 20 10 2 \
    --feat_dim 2 \
    --n_states 2 \
    --beta 0.01 \
    --gamma 1 \
    --proto_update_factor 0.5 \
    --scaling_temperature 0.1 \
    --learning_rate 0.001 \
    --pretrain 10 \
    --n_epochs 20 \
    --train_split 0.9 \
    --train_batch_size 1000 \
    --data_directory ./ts-dar/data/quadruple-well \
    --saving_directory . 
```

Or
```
sh ./ts-dar/scripts/train_tsdar.sh
```

## Compiling Document Environment
Once you have already installed ts-dar in your conda environment. 
```bash
python -m pip install -U sphinx
pip install sphinx-rtd-theme
pip install nbconvert nbformat
pip install sphinx-design
cd docs
make html
```
(Warnings can be ignored!)
You can also visit our [documentation online](https://bojunliu0818.github.io/ts-dart-doc/html/index.html)

## More instructions 

TS-DAR refers to the preprint [10.26434/chemrxiv-2024-r8gjv](https://chemrxiv.org/engage/chemrxiv/article-details/65adf0b966c1381729fb4c11).

We already added the example of Muller potential reported in this preprint to the repo. 

To reproduce the results of the other datasets reported in this preprint, please refer to [Zenodo](https://zenodo.org/records/13835580), where we have uploaded all of our training results and raw simulation data. Or you can directly contact bliu293@wisc.edu.

## Reference

Our codebase builds heavily on
- [https://github.com/deeplearning-wisc/cider](https://github.com/deeplearning-wisc/cider)
- [https://github.com/deeptime-ml/deeptime](https://github.com/deeptime-ml/deeptime)

Thanks for open-sourcing!

[Go to Top](#Abstract)
