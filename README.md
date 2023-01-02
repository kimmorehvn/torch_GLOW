# Moreh AI Framework
pytorch-flows
[reference](https://github.com/ikostrikov/pytorch-flows)
## Install (MAF with Pytorch 1.7.1-Conda env activated)
```bash
cd pytorch-flows
pip install requirements.txt
```
## Data preparation

1. Download the datasets from: https://zenodo.org/record/1161203#.Wmtf_XVl8eN (wget https://zenodo.org/record/1161203/files/data.tar.gz?download=1)
```bash
wget -O data.tar.gz https://zenodo.org/record/1161203/files/data.tar.gz?download=1
```

2. Unpack the downloaded file, and place it in the same folder as the code:
```bash
tar -xf data.tar.gz
```

3. Make sure the code reads from the location the datasets are saved at:
```
pytorch-flows
│   ├── data
│   ├── datasets
│   ├── data.tar.gz
│   ├── flows.py
│   ├── flow_test.py
│   ├── main.py
│   ├── requirements.txt
│   ├── ...
```
## Training
```bash
python main.py --dataset POWER 2>&1 | tee maf_pytorch-flows.log
```
------------------
# Original README:
## pytorch-flows

A PyTorch implementations of [Masked Autoregressive Flow](https://arxiv.org/abs/1705.07057) and 
some other invertible transformations from [Glow: Generative Flow with Invertible 1x1 Convolutions](https://arxiv.org/pdf/1807.03039.pdf) and [Density estimation using Real NVP](https://arxiv.org/abs/1605.08803).

For MAF, I'm getting results similar to ones reported in the paper. GLOW requires some work.

## Run

```bash
python main.py --dataset POWER
```

Available datasets are POWER, GAS, HEPMASS, MINIBONE and BSDS300. For the moment, I removed MNIST and CIFAR10 because I have plans to add pixel-based models later.

## Datasets

The datasets are taken from the [original MAF repository](https://github.com/gpapamak/maf#how-to-get-the-datasets). Follow the [instructions](https://github.com/gpapamak/maf#how-to-get-the-datasets) to get them.

## Tests

Tests check invertibility, you can run them as

```bash
pytest flow_test.py
```