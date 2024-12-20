<p align="center">

<img src="assets/banner.png">

</p>


WiseRL provides banchmarked PyTorch implementations for Offline Preference-Based RL algorithms, including:
- Oracle-IQL & Oracle AWAC
- Supervised Finetuning
- Bradley-Terry Model + IQL/AWAC
- Contrastive Prefereing Learning
- Inverse Preference Learning + IQL/AWAC
- Preference Transformer + IQL/AWAC
- [Hindsight Preference Learning](https://arxiv.org/abs/2407.04451) + IQL/AWAC

## Usage
```bash
# for reward-model free algorithms
python3 scripts/main.py --config /path/to/config.yaml

# for reward-model-based algorithms
python3 scripts/rmb_main.py --config /path/to/config.yaml
```


## Installation
+ clone this repo and install the dependencies
  ```bash
  git clone git@github.com:typoverflow/WiseRL
  cd WiseRL && pip install -e .
  ```
+ install environment or dataset dependencies
  + for D4RL experiments:
    ```bash
    git clone https://github.com/Farama-Foundation/d4rl.git
    cd d4rl
    pip install -e .
    ```
  + for metaworld experiments:
    ```bash
    git clone git@github.com:Farama-Foundation/Metaworld
    cd Metaworld && git checkout 04be337a
    pip install -e .
    ```
  + for robosuite experiments (we follow the instructions from [IPL](https://github.com/jhejna/inverse-preference-learning?tab=readme-ov-file)):
    + Git clone the robosuite repository, checkout to `offline_study` branch and install.
      ```bash
      git clone https://github.com/ARISE-Initiative/robosuite
      cd robosuite && git checkout offline_study
      pip install -e . --no-dependencies
      ```
      Nota that if you are using python 3.10 or higher, you need to change `from collections import Iterable` to `from collections.abc import Iterable` in file `robosuite/models/arenas/multi_table_arena.py`.
    + Run `import robosuite` repeatedly until it completes. Install the missing packages if any error shows up.
    + Git clone the robomimic repository.
      ```bash
      git clone git@github.com:ARISE-Initiative/robomimic.git
      cd robomimic && git checkout v0.2.0
      ```
    + Download the robomimic dataset
      ```bash
      mkdir -p ~/.robomimic/datasets/
      cd robomimic/scripts/
      python download_datasets.py --tasks sim --dataset_types ph --hdf5_types low_dim --download_dir ~/.robomimic/datasets/
      python download_datasets.py --tasks sim --dataset_types mh --hdf5_types low_dim --download_dir ~/.robomimic/datasets/
      ```
    + Checkout back to the master branch and install. **Note that you must first checkout to v0.2.0 branch to download the dataset, and come back to install the latest version of code.**
      ```bash
      git checkout master
      pip install -e . --no-dependencies
      ```
    + Run `import robomimic` repeatedly until it completes. Install the missing packages if any error shows up.
    + Note that the above installation scripts will download the datasets to `~/.robosuite/datasets`. If you would like to change to other locations, please make sure to change the macro in Robomimic Dataset accordingly.

## Acknowledgement
+ [Research Lightening](https://github.com/jhejna/research-lightning) and [Inverse Preference Learning](https://github.com/jhejna/inverse-preference-learning): for their module design and implementations of some baseline algorithms.
+ [Preference Transformer](https://github.com/csmile-1006/PreferenceTransformer): for the Gym-MuJoCo datasets.


## Citation
```bibtex
@software{wiserl
  title = {{WiseRL: Benchmarked Implementations of Offline Preference-based RL Algorithms}},
  author = {Gao, Chen-Xiao and Shengjun, Fang},
  month = feb,
  url = {https://github.com/typoverflow/WiseRL},
  year = {2024}
}

@article{gao2024hindsight,
  title={Hindsight Preference Learning for Offline Preference-based Reinforcement Learning},
  author={Chen-Xiao Gao and Shengjun Fang and Chenjun Xiao and Yang Yu and Zongzhang Zhang},
  journal={arXiv preprint arXiv:2407.04451},
  year={2024},
}
```
