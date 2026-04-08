# NorMuon

This is an unofficial optimized implementation for the [NorMuon paper](https://arxiv.org/abs/2510.05491) Many of these optimizations were adapted from the Modded NanoGPT repository. 

This is a standalone version of the NorMuon optimizer, which features several improvements over the urgent code base, including:

1) Cautious Weight Decay

## Installation

Install directly from GitHub:

```bash
python3 -m pip install git+https://github.com/ShizukaKuze/NorMuon.git
```


## Usage

Usage mirrors the original [Muon](https://github.com/KellerJordan/Muon/tree/master) optimizer; please refer to their examples and details.

## Suggested Usage

It may be advisable to break up the learning rates and weight decays in groups such as in the following example:

```python
    optim_groups = [
        {"params": hidden_params, "lr": 0.02, "weight_decay": 0.1, "use_muon": True},
        {"params": embed_params,  "lr": 0.0001, "weight_decay": 0.01, "use_muon": False},
        {"params": scalar_params, "lr": 0.0001, "weight_decay": 0.01, "use_muon": False},
        {"params": head_params, "lr": 0.0001, "weight_decay": 0.01, "use_muon": False}
    ]
    optim = SingleDeviceNorMuonWithAuxAdam(optim_groups)
```
