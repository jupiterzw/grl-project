# grl-project

## Datasets
`OGBN-Arxiv` is a real-world citation network dataset consisting of nodes representing arXiv papers and edges corresponding to citation relationships between these papers. The task involves predicting the subject area of papers across 40 classes. To simulate distribution shifts, the dataset is split based on the publication time of the papers, with training and testing sets drawn from different time periods.

## Dependency
PYTHON 3.7, CUDA 10.2, Numpy 1.20.3, PyTorch 1.9.0, PyTorch Geometric 1.7.2

## Model Architectures
**GraphSAGE.** We use the `SAGEConv` available in Pytorch Geometric for implementation. The detailed architecture description is as below:
- A sequence of $L$-layer `SAGEConv`.
- Add self-loop and use batch normalization for graph convolution in each layer.
- Use ReLU as the activation.

**GPRGNN.** We use the [implementation](https://github.com/jianhao2016/GPRGNN). We adopt the `PPR` initialization and `GPRprop` as the propagation unit. The associated hyper-parameters in GPRGNN model are set as: $\alpha_{GPRGNN} = 0.1$.

## Results

EERM SAGE
```bash
All runs:
Highest Train: 48.61 ± 0.49
Highest Valid: 43.89 ± 0.12
   Final Test 0: 41.54 ± 0.63
   Final Test 1: 40.27 ± 1.29
   Final Test 2: 38.46 ± 1.33
```
SAGE + FLAG
```bash
All runs:
Highest Train: 49.75 ± 1.28
Highest Valid: 47.63 ± 0.47
   Final Test 0: 44.50 ± 1.17
   Final Test 1: 39.89 ± 1.50
   Final Test 2: 37.24 ± 1.41
```

EERM GPR
```bash
All runs:
Highest Train: 51.13 ± 0.94
Highest Valid: 50.89 ± 0.16
   Final Test 0: 49.92 ± 0.48
   Final Test 1: 49.03 ± 0.50
   Final Test 2: 44.70 ± 0.61
```
GPR + FLAG
```bash
All runs:
Highest Train: 49.77 ± 1.50
Highest Valid: 50.14 ± 0.74
   Final Test 0: 48.30 ± 0.53
   Final Test 1: 42.50 ± 0.66
   Final Test 2: 41.52 ± 0.65
```